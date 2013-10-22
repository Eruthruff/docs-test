---
title: Line Series
meta_title: Line Series
meta_description: description.
slug: 
tags:line,series
publish:True
---


Line series visualize data as a continuous line on a Cartesian coordinate system. Categories are laid out
				on the X-axis, while values go on the Y-axis.
			![chart-line-series](../Media/Controls\Chart\chart-line-series.png)

# 
				Defining a Line Series Declaratively
			

To define a Line series in HTML, add an object with __type__ property set to "line"
					to the __series__ array.
				


 __html__
    


				<div id="declarativeLineSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ type: 'line', name: 'World', data: [16.7, 20, 15.7, 26.6, 23.5] }
					]
				}">
				</div>



# 
				Defining Line Series Programmatically
			

To programmatically add a Line series to the chart, create a new __Telerik.UI.Chart.LineSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var lineSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("lineSeriesChart"));
					var lineSeries = new Telerik.UI.Chart.LineSeries();
					lineSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					lineSeriesChartCtrl.series.push(lineSeries);
					lineSeriesChartCtrl.refresh();



# Configuring Line Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Line series.
				

# Assigning a Value Axis

When you have multiple value axes, you can assign the Line series to one of them, using the __axis__ option. The property
							defaults to the primary axis.
						


 __html__
    


				<div id="valueAxisChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					 title: {
						  text: 'Average temperature and humidity'
					 },
					 legend: {
						  position: 'bottom'
					 },
					 series: [{
						  type: 'line',
						  name: 'Temperature',
						  data: [32, 25, 20, 15, 5],
						  axis: 'temperature',
						  color: '#1E98E4'
					 }, {
						  type: 'line',
						  name: 'Humidity',
						  data: [45, 50, 80, 78, 76],
						  axis: 'humidity',
						  color: '#f99'
					 }
					 ],
					 categoryAxis: {
						  categories: ['Aug', 'Sep', 'Oct', 'Nov', 'Dec']
					 },
					 valueAxis: [{
						  name: 'temperature',
						  labels: {
						  format: '{0}C'
					 }
					 }, {
						  name: 'humidity',
						  labels: {
						  format: '{0}%'
					 }
					 }]
				}">
				</div>



The resulting chart will look like this:![Multiple axes](../Media/Controls\Chart\chart-line-series-axes.png)

# Customizing Markers

You can set a few options that change what a data point looks like in a Line series by setting the __markers__ property. They include:
							__background__, __border__ settings, __size__, __type__
							(circle, square or triangle) and __visible__.
						

Example:


 __html__
    


				<div id="customizedMarkersChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'line',
						name: 'Profit',
						data: [2200, 2500, 1800, 2400, 2300, 3000, 2900, 3100],
						markers: {
							type: 'square',
							background: 'yellow'
						}
					}]
				}">
				</div>

![Customizing markers](../Media/Controls\Chart\chart-line-series-markers.png)

# Handling Missing Values

There are three different options to handle missing values in your chart when using a Line series. They are presented by the
							__missingValues__ property, which accepts the following values:
						

* 

__gap__: The line stops before missing point and continues after it (default value).
								

* 

__interpolate__: The value is interpolated from neighboring points
								

* 

__zero__: The value is assumed to be zero.
								

In the example below, where the missing value is assumed to be zero:


 __html__
    


				<div id="missingValuesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'line',
						name: 'Profit',
						data: [2200, 2500, 1800, 2400, 2300, null, 2900, 3100],
						missingValues: 'zero'
					}]
				}">
				</div>



And this is the resulting chart:![Handling missing values](../Media/Controls\Chart\chart-line-series-missing-values.png)

# Related Topics

 * [Vertical Line Series]({{slug:vertical-line-series}})
