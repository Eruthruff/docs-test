---
title: Create a Drill-down Chart
meta_title: Create a Drill-down Chart
meta_description: description.
slug: 
tags:create,a,drill-down,chart
publish:True
---


Presenting large sets of categorical data can be done in more compact form if you do it in a drill-down manner. Using RadChart's features you can achieve such 
				results with a single chart instance. This article will introduce you to a simple drill-down scenario where in the main view, a chart displays sales info per year, 
				and on click of a column in the series, the 12-month breakdown of the data is displayed in the same chart.
			

# Section1

The following steps show how to create a column chart that has summarized sales data. When a user clicks a column in the series,  the chart displays detailed 
					data corresponding to the clicked column. The data is presented by objects of the following type:
				

	
					{ Date: new Date(2012, 11, 25), Sales: 850 }
				



Here is how you can implement such scenario:

* 

*Define a RadChart with the data initially aggregated.* To achieve this, set the category axis date and its base unit to
							years. To aggregate the data for each year, in the series definition define a __sum__ aggregate.
						


 __html__
    


				<div id="chart1"></div>
				<button id="restoreBtn" style="display: none">Restore years view</button>




 __js__
    


					var chart = new Telerik.UI.RadChart(document.getElementById("chart1"), {
						title: { text: "Yearly and monthly review of sales" },
						dataSource: ds,
						series: [
							{
								type: "column",
								field: "Sales",
								aggregate: "sum",
								name: "Units Sold",
								labels: {
									visible: true
								}
							}
						],
						categoryAxis: {
							field: "Date",
							baseUnit: "years",
							type: "date",
							labels: {
								dateFormats: {
									years: "yyyy",
									months: "MMMM 'yy"
								},
								rotation: 45
							}
						},
						tooltip: {
							visible: true
						},
						onseriesclick: drillDown,
						width: 800
					});



* 

*
								Handle the __onseriesclick__ event and modify the chart to display the detailed data*. In the event handler you 
								should:
						

* 

*Check at which level of data you are*. The event arguments of the __seriesclick__ event provide 
									information about the specific series click, as well as a reference to the chart control. In this scenario, we check the base unit of the category 
									axis, since we know at the top level we display years. Now, depending on the current base unit, the customization of the chart and its data source
									 can be done.
								

* 

*Filter the chart data based on the year value*. From the category of the clicked series, we extract the year, and
									then use it to filter the data source to contain only entries for the current year. This is easily done by adding a "greater than or equal to"
									filter (gte) with value of 1st Jan [Current Year] and a "less than" (lt) filter with a value of 1st Jan [Next Year].
								

* 

*Change the category axis base unit*. Since data will be displayed on per month basis, the base unit of the
									category axis should be changed to "months". If you have data that presents values on per day basis, you can follow similar logic
									and assign "days" as value of categoryAxis.baseUnit.
								

* 

*Call refresh() for the chart to rebind it and apply the provided changes.*


 __js__
    


		function drillDown(e) {
			if (e.target.categoryAxis.baseUnit.toLowerCase() == "years") {
				var date = e.category;
				var year = date.getFullYear();
				var ds = e.target.dataSource;
				var filters = [
				{ field: "Date", operator: "gte", value: new Date(year, 0) },
				{ field: "Date", operator: "lt", value: new Date(year + 1, 0) }];
				ds.filter = filters;
	
				var chart = e.target;
				chart.categoryAxis.baseUnit = "months";
				chart.refresh();
				document.getElementById("restoreBtn").style.display = "";
			}
		}



* 

*Provide a way to switch back to main (original) view*. In this example, we provide a button that upon click restores the 
							original view of the chart. This is achieved by clearing the dataSource filter and switching the category axis base unit back to 
							*"years"*.
						


 __js__
    


					document.getElementById("restoreBtn").addEventListener("click", function (e) {
						var chart = document.getElementById("chart1").winControl;
						chart.dataSource.filter = null;
						chart.categoryAxis.baseUnit = "years";
						chart.refresh();
						e.target.style.display = "none";
					});



The resulting chart looks like this:![chart-drill-down](../Media/Controls\Chart\chart-drill-down.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/DrilldownChart*.
        

# Related Topics

 * [Column Series]({{slug:column-series}})

 * [Category Axis]({{slug:category-axis}})

 * [Tooltip]({{slug:tooltip}})

 * [Events]({{slug:events}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})

 * [Filtering]({{slug:filtering}})
