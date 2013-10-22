---
title: Scatter Line Series
meta_title: Scatter Line Series
meta_description: description.
slug: 
tags:scatter,line,series
publish:True
---


Scatter Line series are suitable for visualizing two-dimensional data on a Cartesian coordinate system. The two axes, X and Y,
				both represent data values. Each data point in the series is represented by a pair of values - the X value and the Y value.
				Data points are connected in a line.
			![chart-scatter-line-series](../Media/Controls\Chart\chart-scatter-line-series.png)

# 
				Defining a Scatter Line Series Declaratively
			

To define a Scatter Line series in HTML, add an object with __type__ property set to "scatterLine"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeScatterLineChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
							type: 'scatterLine', 
							data: [[10, 10], [15, 20], [20, 25], [32, 40], [43, 50], [55, 60], [60, 70], [70, 80]],
							name: 'Example' 
						}
				]}">
				</div>



# 
				Defining a Scatter Line Series Programmatically
			

To programmatically add a Scatter Line series to the chart, create a new __Telerik.UI.Chart.ScatterLineSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var scatterLineSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("scatterLineSeriesChart"));
					var scatterLineSeries = new Telerik.UI.Chart.ScatterLineSeries();
					scatterLineSeries.data = [[10, 10], [15, 20], [20, 25], [32, 40], [43, 50], [55, 60], [60, 70], [70, 80]];
					scatterLineSeries.name = "Example";
					scatterLineSeriesChartCtrl.series.push(scatterLineSeries);
					scatterLineSeriesChartCtrl.refresh();



# Configuring a Scatter Line Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Scatter Line series.
				

The properties of the Scatter series fully apply to the Scatter Line series as well, so you can check them
					[here](8b72db8e-3e99-48ac-ac47-49433e5e3fc2). Additional settings are listed below.
				

# Handling Missing Values

There are three different options to handle missing values in your chart when using a Line series. They are presented by the
							__missingValues__ property, which accepts the following values:
						

* 

__gap__: The line stops before missing point and continues after it (default value).
								

* 

__interpolate__: The value is interpolated from neighboring points.
								

* 

__zero__: The value is assumed to be zero.
								

In the example below the missing value is interpolated:


 __html__
    


				<div id="missingValuesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'scatterLine',
						xField: 'Year',
						yField: 'Value',
						missingValues: 'interpolate'
					}],
					dataSource: {
						data: [
								{Year:2001, Value:5000},
								{Year:2002, Value:7500},
								{Year:null, Value:9000},
								{Year:2004, Value:null},
								{Year:2005, Value:12000},
								{Year:2006, Value:18000},
								{Year:2007, Value:null},
								{Year:2008, Value:19000},
								{Year:null, Value:16000},
								{Year:2010, Value:null},
								{Year:2011, Value:18000}
						] 
					}
				}">
				</div>



And this is the resulting chart:![Handling missing values](../Media/Controls\Chart\chart-scatter-line-series-missing-values.png)

# Related Topics

 * [Scatter Series]({{slug:scatter-series}})

 * [Bubble Series]({{slug:bubble-series}})
