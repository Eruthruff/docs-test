---
title: Show Chart in Grid Column
meta_title: Show Chart in Grid Column
meta_description: description.
slug: 
tags:show,chart,in,grid,column
publish:True
---


In this article you can see how you can embed a RadChart in each cell of a column in RadGrid. This is achieved using a template for the grid column. 

# Implementation

The sample below uses a single source of data for the grid and the chart series. However, by filtering the chart data source, based on the current grid row values,
					you can easily achieve more complex scenarios, working with multiple sources of data, including remote ones.
				

The steps to initialize and populate a RadControl inside RadGrid are as follows:

* 

Define your grid:

* 

Set the grid as you need it—data source, other columns, data operations, etc.

* 

In one of the columns, define a template which makes a call to an external function.

* 

Attach the databound event to point to an external function.

At that point, the code looks like this:


 __js__
    


					var gridWithChart = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							data: ChartSampleData.employees
						},
						columns: [
							{ field: 'Name', title: 'Name' },
							{
								title: 'Sales',
								template: getChartTemplate
							}
						],
						ondatabound: initializeControls
					});



* 

Implement the function that initializes the chart. Since it is expected to return a string, it is best to first create the chart options as a JavaScript
							object and then use the JSON.stringify() method to pass them inside the string defining the chart.
						


 __js__
    


		function getChartTemplate(data) {
			var options = {
				series: [{
				    data: data.Sales,
	                width: 3,
					name: 'Sales'
				},
				{
				    data: data.Customers,
	                width: 3,
					name: 'Customers'
				}
				],
				seriesDefaults: {
					type: 'line',
					markers: {
						visible: false
					}
				},
				valueAxis: {
					labels: { visible: false },
					line: { visible: false },
					majorGridLines: { visible: false }
				},
				categoryAxis: {
					labels: { visible: false },
					line: { visible: false },
					majorGridLines: { visible: false }
				},
				tooltip: {
	                visible: true
				},
				width: 250,
				height: 50
			};
			return "<div class='chart' data-win-control='Telerik.UI.RadChart' data-win-options='" + JSON.stringify(options) + "'></div>";
		}



If you will have two separate sources for the grid and chart, define the dataSource option of the chart and define a filter to assign only the
							relevant data to each chart. The __data__ object passed by RadGrid contains all values of the current grid row, so you can pass them
							as filter values, e.g.
						

	
							filter: [
							{ field: 'OrderID', operator: 'eq', value: data.ID }
							]
						



For more info, see the [Filtering](69ac0343-692f-402f-a04d-0d00498f34da) article of the DataSource control.
						

For simplicity, this example uses a single data source where the series data is nested inside the objects used to bind the grid.


 __js__
    


		var employees = [
			{ Name: "Nancy Davolio", Sales: [5, 12, 9, 21, 23], Customers: [5, 7, 7, 16, 17] },
			{ Name: "Andrew Fuller", Sales: [10, 12, 15, 19, 21], Customers: [7, 9, 8, 12, 13] },
			{ Name: "Janet Levering", Sales: [14, 15, 14, 21, 18], Customers: [9, 12, 12, 16, 15] },
			{ Name: "Margaret Peacock", Sales: [18, 24, 21, 25, 26], Customers: [12, 16, 16, 18, 20] },
			{ Name: "Michael Suyama", Sales: [16, 13, 17, 19, 23], Customers: [10, 10, 13, 15, 19] }
		];
	
		WinJS.Namespace.define("ChartSampleData", {
			employees: employees
		});



* 

In the databound event handler, call [WinJS.UI.processAll()](http://msdn.microsoft.com/en-us/library/windows/apps/hh440975.aspx) and pass the grid element as root  so that the controls inside RadGrid can be
							initialized.
						


 __js__
    


		function initializeControls(e) {
		    if (e.target.element.offsetHeight) {
		        WinJS.UI.processAll(e.target.element);
		    }
		    else {
		        setTimeout(initializeControls, 300);
		    }
		}



When you run this code, you shall see a chart placed in each cell of the second grid column.![grid-columns-howto-chart](../Media/Controls\Grid\grid-columns-howto-chart.png)

# 
        Tip: Initialize the Controls One at a Time
      

In case you have a large amount of data and many rows, initializing all the controls can take some time, which does not produce a good user experience. 
          To avoid this, you can initialize each control individually and display it, so the user can see some data records even before all of them are visualized. 
          First you need to get all desired elements in an array.
        


 __js__
    


		var _chartsToShow = [];
	
	    function initializeControlIndividually(e) {
	        var charts = $(e.target.element).find(".chart");
	        if (charts.length) {
	            for (var i = charts.length; i >= 0; i--) {
	                _chartsToShow.push(charts[i]);
	            }
	
	            setImmediate(function myfunction() {
	                renderControls();
	            });
	        }
		}



Then you can initialize each control individually by passing it as a parameter of the
          __processAll()__ method. For a better animation of the whole process use the __requestAnimationFrame()__
          method and pass the __processAll()__ method as a callback.
        


 __js__
    


	    function renderControls() {
	        var charts = _chartsToShow;
	        if (!charts || !charts.length) return;
	        var chartEl = charts.pop();
	
	        requestAnimationFrame(function () {
	            WinJS.UI.processAll(chartEl);
	            renderControls();
	        });
	    }



This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/ShowChartInGridColumn*.
        

# Related Topics[WinJS.UI.processAll() function](http://msdn.microsoft.com/en-us/library/windows/apps/hh440975.aspx)

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Events]({{slug:events}})

 * [Getting Started]({{slug:getting-started}})

 * [Filtering]({{slug:filtering}})
