---
title: Data Binding
meta_title: Data Binding
meta_description: description.
slug: 
tags:data,binding
publish:True
---


RadChart supports a set of flexible data-binding mechanisms that will suite the data visualization needs of developers.
			

# Binding To Inline Data

When inline data binding is used, the chart data points are specified as part of the series definitions. The type of the data
					points depends on the type of the series.
				


 __html__
    


				<div id="columnSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
						series: [{
							name: 'Example Series',
							type: 'column',
							data: [200, 450, 300, 125]
						}]
		
						}">
				</div>




 __html__
    


				<div id="pieSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								name: 'Example Series',
								type: 'pie',
								data:[{
									value: 40,
									category: 'Apples'
								}, {
									value: 60,
									category: 'Oranges',
									color: '#ff6103'
								}]
							}]
						}">
				</div>




 __html__
    


				<div id="scatterSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series:[{
								name: 'Example Series',
								type: 'scatterLine',
								data:[[0, 1], [1, 2], [2,1]]
							}]
						}">
				</div>



# Binding to a Data Source

RadChart can be bound to local and remote data through integration with the __Telerik.Data.DataSource__
					component. The DataSource can be used to make requests both to local data files as well as remote web
					services that return data as JSON or XML.
				

To specify a data source for RadChart, use the __dataSource__ property of the control either declaratively
					in the HTML, or programmatically once the RadChart instance is created.
				


 __html__
    


				<div id="localBoundChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: Sample.Data.seriesData
							},
							series: [
								{ type: 'line', field: 'sales' }
							],
							categoryAxis: {
								field: 'year'
							}
							}">
				</div>




 __js__
    


					var chart = new Telerik.UI.RadChart(document.getElementById("dataSourceBoundChart"));
					var dataSource = new Telerik.Data.DataSource(Sample.Data.seriesData);
					chart.dataSource = dataSource;
	
					var series = new Telerik.UI.Chart.LineSeries();
					series.field = "sales";
					chart.series.push(series);
	
					chart.categoryAxis.field = "year";
					chart.refresh();



A sample of the data contained in Sample.Data.seriesData is shown below:


 __js__
    


	WinJS.Namespace.define("Sample.Data", {
		seriesData: [
		{ year: "2000", sales: 200 },
		{ year: "2001", sales: 450 },
		{ year: "2002", sales: 300 },
		{ year: "2003", sales: 125 }]
	});



# Binding to Remote Data

The chart can be bound to remote data by configuring the DataSource transport. The transport defines how the DataSource will interact with remote data.
				

In the below example, RadChart is bound to the sample OData Northwind service: "http://services.odata.org/Northwind/Northwind.svc/".
				

To bind RadChart to a remote source, set the __transport__ property of the data source:
				


 __html__
    


				<div id="remoteBoundChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
							pageSize: 4,
								transport: {
									read: {
										url: 'http://services.odata.org/Northwind/Northwind.svc/Products',
										dataType: 'json'
									}
								},
								schema: {
									data: 'value'
								}
							},
							series: [{
								type: 'column',
								field: 'UnitPrice'
							}],
							categoryAxis: {
								field: 'ProductName'
							}
						}">
				</div>



# Data-Bound Chart Series

All RadChart series can be data-bound to data source items. Each series type requires its own configuration
					for properly extracting field values from data items.
				

When binding categorical series (such as Bar, Column, Line and Area), use the __field__
					property of the series to specify the property that will be used for getting the data for each data item.
				


 __js__
    


					var categoricalSeriesBindingChartCtrl = new Telerik.UI.RadChart(document.getElementById("categoricalSeriesBindingChart"), {
						dataSource: [{ year: "2000", sales: 200 }, { year: "2002", sales: 250 }, { year: "2003", sales: 255 }]
					});
					var series = new Telerik.UI.Chart.LineSeries();
					series.field = "sales";
					categoricalSeriesBindingChartCtrl.series.push(series);
					categoricalSeriesBindingChartCtrl.refresh();



When binding to radial series (such as Pie and Donut), use the __field__ property
					as above shown and additionally specify the __categoryField__, __colorField__,
					and __explodeField__ to bind the category, color and exploded state of the series to your data item values:
				


 __js__
    


					var radialSeriesBindingChartCtrl = new Telerik.UI.RadChart(document.getElementById("radialSeriesBindingChart"), {
						dataSource: [
							{ year: "2010", sales: 200, color: "#33ccff" },
							{ year: "2011", sales: 212, color: "#336699" },
							{ year: "2012", sales: 235, color: "#3366cc", exploded: true }
						]
					});
					var series = new Telerik.UI.Chart.PieSeries();
					series.field = "sales";
					series.categoryField = "year";
					series.colorField = "color";
					series.explodeField = "exploded";
					radialSeriesBindingChartCtrl.series.push(series);
					radialSeriesBindingChartCtrl.refresh();



When binding XY-type series (like Scatter and Scatter Line), use the __xField__ and __yField__
					properties to specify data fields to bind the X and Y axis values of every data point in the series:
				


 __js__
    


					var xySeriesBindingChartCtrl = new Telerik.UI.RadChart(document.getElementById("xySeriesBindingChart"), {
						dataSource: [
							{ x: 3, y: 20 },
							{ x: 8, y: 22 },
							{ x: 11, y: 24 },
							{ x: 14, y: 21 }
						],
						series: [{
							type: "scatter",
							xField: "x",
							yField: "y"
						}]
					});



# Related Topics

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})
