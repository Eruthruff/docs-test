---
title: Using Detail Template
meta_title: Using Detail Template
meta_description: description.
slug: 
tags:using,detail,template
publish:True
---


When you want to display a more customized view of the detail records, you could use a detail template. It allows you to specify content of your choice for the
				detail row of the grid and in combination with the API provided by RadGrid, you can populate it dynamically based on the values in the expanded parent row. 
				Following, you can see a step-by-step description of implementing a detail template in RadGrid.
			

# Using a Detail Template in RadGrid

Follow the steps below to implement this scenario:

* 

To specify a template for the detail rows of RadGrid, you can use the __detailTemplate__ property of the control. It should be a
							string containing HTML or a function that returns a DOM element or HTML string.
						


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: Sample.categories,
						ondetailinit: detailInit,
						detailTemplate: detailTemplateInit,
						columns: [
							{ field: "ID", width: 40 },
							{ field: "Name" }
						]
					});



Here follows a very simple function returning a single line of HTML. It is used to demonstrate how you can access data from the parent row, for
							example, to use it to generate a unique name for a control inside the detail item.
						


 __js__
    


		function detailTemplateInit(args) {
			return "<div id='chart_" + args.Name + "'/>";
		}



For such a simple scenario, you could assign a string to the detailTemplate property directly. You will get the same result if you use the following
							string:
						

	
							detailTemplate: "<div id='chart_#=Name#'/>",
						



* 

Handle the __detailInit__ event and use it to initialize any WinJS controls, to populate the template with data, related to the
							parent item, etc.
						

The values passed in the event arguments, which you can find useful in a detail template scenario, are listed in the table below:

Argument

Description

__e.data__

The data item of the parent row. It contains all values for all fields from the corresponding entry of the data source. You can use these
										values to filter the detail template's data.
									

__e.detailCell__

The TD element containing the template that you have declared.

__e.detailRow__

The TR element of the current detail item (the row holding the above described cell).

__e.masterRow__

The TR element corresponding to the parent row, that has been expanded to load the current detail item. You can use this reference
										to style the expanded row.
									

__e.target__

The parent RadGrid object, that raised the event.

Our implementation continues by instantiating a RadChart using the DIV element declared in the template and filtering its data source to display
							only records relevant to the current parent row:
						


 __js__
    


		function detailInit(e) {
			var chart = new Telerik.UI.RadChart(document.getElementById("chart_" + e.data.Name), {
				dataSource: {
					data: Sample.data,
					filter: { field: "CategoryID", operator: "eq", value: e.data.ID }
				},
				series: [
					{
						field: "Price",
						type: "column",
						labels: {
							visible: true,
							template: "$#=value#"
						},
						name: "Price"
					}
				],
				categoryAxis: {
					field: "Name"
				},
				width: 700,
				height: 200
			});
		}



For clarity, the data used in this examples is defined as follows:


 __js__
    


		var data = [
	        { "ID": 0, "Name": "Bread", "Price": "2.5", "CategoryID": 0 },
	        { "ID": 1, "Name": "Milk", "Price": "3.5", "CategoryID": 1 },
	        { "ID": 2, "Name": "Vint soda", "Price": "20.9", "CategoryID": 1 },
	        { "ID": 3, "Name": "Havina Cola", "Price": "19.9", "CategoryID": 1 },
	        { "ID": 4, "Name": "Fruit Punch", "Price": "22.99", "CategoryID": 1 },
	        { "ID": 5, "Name": "Cranberry Juice", "Price": "22.8", "CategoryID": 1 },
	        { "ID": 6, "Name": "Pink Lemonade", "Price": "18.8", "CategoryID": 1 },
	        { "ID": 7, "Name": "DVD Player", "Price": "35.88", "CategoryID": 2 },
	        { "ID": 8, "Name": "LCD HDTV", "Price": "1088.8", "CategoryID": 2 },
			{ "ID": 9, "Name": "Soup", "Price": "10.5", "CategoryID": 0 },
			{ "ID": 10, "Name": "Cake", "Price": "7.5", "CategoryID": 0 },
			{ "ID": 11, "Name": "Surface Tablet", "Price": "499 ", "CategoryID": 2 }
		];
	
		var categories = [
	        { ID: 0, Name: "Food" },
	        { ID: 1, Name: "Beverages" },
	        { ID: 2, Name: "Electronics" }
		];
	
		WinJS.Namespace.define("Sample", {
			data: data,
			categories: categories
		});



This is how the grid will look when a parent item is expanded:![grid-detail-template](../Media/Controls\Grid\grid-detail-template.png)

# Related Topics
