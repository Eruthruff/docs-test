---
title: Using Data Storage with RadControls
meta_title: Using Data Storage with RadControls
meta_description: description.
slug: 
tags:using,data,storage,with,radcontrols
publish:True
---


This help article explains how to use the __Data Storage__ component in a project with RadControls for Windows 8/HTML. Make sure that before you follow the
				instructions from this article you have prepared your project to use the __Data Storage__ component. See instructions here:
				[](82cab44f-a2db-4a0c-9df0-89e89cd106bc).
			

# Section1How to Bind RadControls to Data Fetched From Telerik Data Storage

All databound RadControls use the __Telerik.Data.DataSource__ component as a data layer. That is why it is very easy to bind these
					controls to data fetched from the __Data Storage__ component. When you fetch data from the __Data Storage__ database, it is returned as a
					JavaScript array and the __DataSource__ can be bound directly to this result, thus populating the RadControl
					it belongs to. This procedure is described in the following steps.
				

* 

*Create and populate the database*. Before populating a table in the database, you should check its state. This is
							needed for you to know whether the database table(s) needs to be populated or it can be used directly. If the table(s) exists, based on your
							requirements, either delete the old records and add new or do nothing (this is the default scenario when the data
							isn't dynamic). If the table(s) does not exist, populate it with data using the __insert()__ method described in the
							[](82cab44f-a2db-4a0c-9df0-89e89cd106bc) article.
						

In the following code snippet you can see a method called __ensureDataBase()__. It checks if the database table of interest
							exists and creates new records only in case the table is not yet created.
						


 __js__
    


		function ensureDataBase() {
			//Make a connection to the DB. If it does not exist, it will be created.
			var db = Telerik.Data.Database.open("SalesDB");
			//Make a query to the table of interest to see if it exists. If it doesn't, the error function will be entered.
			db.query("select * from Sales as x").done(function (result) {
				//DB is OK
				db.close();
			}, function (error) {
				if (error && error.message && error.message.indexOf("no such table:") != -1) {
					//DB is new
					db.close();
					createDb();
				}
			});
		}



The error function calls the __createDb()__ method that is shown below. The method creates a table and populates it.
						


 __js__
    


		function createDb() {
			var db = Telerik.Data.Database.open("SalesDB");
			for (var i = 0; i < salesData.length; i++) {
				var item = salesData[i];
				//the first call to insert() creates the DB table
				db.insert("Sales", { name: item.name, salesYTD: item.salesYTD, salesQuota: item.salesQuota, bonus: item.bonus });
			}
			db.sync().then(function () {
				db.close();
			});
		}



__salesData__ is a simple JavaScript array. Its records are structured as shown in the snippet below.
						


 __js__
    


		{
			id: 275,
			name: "Michael Blythe",
			salesLastYear: 1750406.4785,
			salesYTD: 3763178.1787,
			salesQuota: 300000,
			bonus: 4100



* 

*Query the database*. In this step you need to build your SQL query. It can be a static one or it can be built
							depending on user actions. The syntax of the query should conform to the SQLite synax. See reference here: [SQL As Understood By SQLite](http://www.sqlite.org/lang_select.html). For queries with more complex filtering and sorting scenarios, you can use the Data Storage API described here:
							[Read Operations](e8255ea7-4da1-41fc-91a1-9401cef081a2).
						

This example uses a static query with a WHERE and ORDER BY clauses.


 __js__
    


					var sql = "SELECT * FROM Sales WHERE bonus > 0 ORDER BY bonus DESC";



The result of a successful query will be a JavaScript array. You can see how it is consumed in the next step.
						

* 

*Populate a DataSource and bind RadControls.* If you are going to bind multiple RadControls to the result, you can define
							one common __DataSource__ and assign it to the controls. This is shown in the example below where a __RadGrid__
							and a __RadChart__ controls are defined unbound in markup and are then bound when the query to the __Data Storage__
							succeeds.
						


 __html__
    


			<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
				columns: [
					{field: 'name'},
					{field: 'salesYTD', title: 'Sales This Year', format: '{0:c2}'},
					{field: 'salesQuota', title: 'Sales Quota', format: '{0:c0}'},
					{field: 'bonus', format: '{0:c0}'}
				],
				height: 300
			}">
			</div>
			<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
				series: [
					{
						type: 'column',
						field: 'salesYTD'
					},
					{
						type: 'line',
						field: 'salesQuota',
						missingValues: 'zero'
					}
				],
				categoryAxis: {
					field: 'name',
					labels: {
						rotation: 30
					}
				},
				valueAxis: {
					max: 4500000
				},
				width: 800,
				theme: 'light'
			}">
			</div>




 __js__
    


					queryDb(sql).done(function (result) {
						var ds = new Telerik.Data.DataSource({
							data: result,
							schema: {
								model: {
									id: "id",
									fields: {
										id: { type: "number" },
										name: { type: "string" },
										salesYTD: { type: "number" },
										salesQuota: { type: "number" },
										bonus: { type: "number" }
									}
								}
							}
						});
						var grid = Telerik.UI.to.Grid(document.getElementById("grid1").winControl);
						var chart = Telerik.UI.to.Chart(document.getElementById("chart1").winControl);
						grid.dataSource = ds;
						grid.refresh();
						chart.dataSource = ds;
						chart.refresh();
					}, function (err) {
						//handle error
						//information about the error is available in err.message
					});



If you want to populate a single control, you can directly create this control in JavaScript and assign the resulting array to its
							__dataSource.data__ property.
						

The __RadGrid__ and __RadChart__ controls from the above definition are shown in the following image:![datastorage-radcontrols](../Media/DataStorage\datastorage-radcontrols.png)

# Related Topics

 * [Getting Started]({{slug:getting-started}})

 * [Overview]({{slug:overview}})
