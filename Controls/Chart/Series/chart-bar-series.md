---
title: Bar Series
meta_title: Bar Series
meta_description: description.
slug: 
tags:bar,series
publish:True
---


Bar series visualize data in horizontal bars on a Cartesian coordinate system. Categories are laid out
				on the Y-axis, while values go on the X-axis.
			![chart-bar-series](../Media/Controls\Chart\chart-bar-series.png)

# 
				Defining Bar Series Declaratively
			

To define a Bar series in the HTML, add an object with __type__ property set to "bar"
					to the __series__ array:
				


 __html__
    


				<div id="declarativeBarSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ type: 'bar', name: 'World', data: [16.7, 20, 15.7, 26.6, 23.5] }
					]
				}">
				</div>



# 
				Defining Bar Series Programmatically
			

To programmatically add a Bar series to your chart, create a new __Telerik.UI.Chart.BarSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var barSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("barSeriesChart"));
					var barSeries = new Telerik.UI.Chart.BarSeries();
					barSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					barSeries.name = "World";
					barSeriesChartCtrl.series.push(barSeries);
					barSeriesChartCtrl.refresh();



# Configuring Bar Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Bar series.
				

# Assigning a Value Axis

When you have multiple value axes, you can assign the bar series to one of them using the __axis__ property. The property
							defaults to the primary axis.
						

Example:


 __html__
    


				<div id="valueAxisChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					title: {
						text: 'Average temperature and humidity'
					},
					legend: {
						position: 'bottom'
					},
					series: [{
						type: 'bar',
						name: 'Temperature',
						data: [20, 25, 32],
						axis: 'temperature',
						color: '#1E98E4'
					}, {
						type: 'bar',
						name: 'Humidity',
						data: [45, 50, 80],
						axis: 'humidity',
						color: '#f99'
					}
					],
					categoryAxis: {
						categories: ['Aug', 'Sep', 'Oct']
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



The resulting chart will look like this.![Assigning value axis](../Media/Controls\Chart\chart-bar-series-axis.png)

# Displaying Negative Values

When negative values are displayed in RadChart, you may want to highlight the bars that represent negative values. An easy way to do so is to
							use the __negativeColor__ property. You can set it to any valid CSS color and it will be used to color bars that show negative
							values. The example below shows a chart which uses the negative of the default series color to display negative values:
						


 __html__
    


				<div id="negativeValuesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					title: {
						text: 'Average Temperature in Celsius'
					},
					dataSource: {
						data: [
						{Month: 'January', Temperature: -10},
						{Month: 'February', Temperature: -5},
						{Month: 'March', Temperature: -1},
						{Month: 'April', Temperature: 7},
						{Month: 'May', Temperature: 12},
						{Month: 'June', Temperature: 17}
						]
					},
					series: [
						{ 
							type: 'bar',
							field: 'Temperature',
							negativeColor: '#e1671b'
						}
					],
					categoryAxis: {
						field: 'Month',
						labels: {
							margin: {
								bottom: 40
							}
						}
					}
				}">
				</div>

![chart-bar-series-negative-color](../Media/Controls\Chart\chart-bar-series-negative-color.png)

# Controlling the Distance Between Categories

Based on your requirement, you can increase or decrease the space between category clusters. This is done by setting the __gap__
							property to an appropriate numeric value. This value represents the proportion between the space between category clusters and the bar width
							(i.e. "gap: 10" means that the bar width will be one tenth of the space between category clusters).
						


 __html__
    


				<div id="categoriesDistanceChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ 
							gap: 10,
							type: 'bar', 
							data: [16.7, 20, 15.7, 12, 40, 23] 
						}
					],
					categoryAxis: {
							categories: ['2000', '2002', '2005', '2008', '2010', '2012']
					}
				}">
				</div>



You can see how the space increases between categories (Y-axis):![Controlling distance between bars](../Media/Controls\Chart\chart-bar-series-gap.png)

# Controlling the Distance Between Bars

You can also increase or decrease the space between bars belonging to one and the same category. This is done by setting the __spacing__
							property to an appropriate numeric value. This value represents the proportion between the space between bars in a single category and the bar width
							(i.e. "spacing: 0.2" means that the bar width will be five times the space between bars in the same category).
						


 __html__
    


				<div id="barsDistanceChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'bar',
						name: 'Temperature',
						data: [20, 25, 32],
						axis: 'temperature',
						color: '#1E98E4',
						spacing: 0.2
					}, {
						type: 'bar',
						name: 'Humidity',
						data: [45, 50, 80],
						axis: 'humidity',
						color: '#f99'
					}
					],
					categoryAxis: {
						categories: ['Aug', 'Sep', 'Oct']
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



This will result in:![Spacing between bars](../Media/Controls\Chart\chart-bar-series-spacing.png)

# Gradient Options

You can easily show a gradient in the Bar series by changing the default value of the __overlayGradient__ property. Its default
							value is __"none"__ and a solid color fills the series, but you could also set it to __"glass"__ or
							__"roundedBevel"__.
						


 __html__
    


				<div id="gradientChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ 
							overlayGradient: 'glass',
							type: 'bar', 
							data: [16.7, 20, 15.7, 12, 40, 23] 
						}
					],
					categoryAxis: {
							categories: ['2000', '2002', '2005', '2008', '2010', '2012']
					}
				}">
				</div>

![Showing gradient](../Media/Controls\Chart\chart-bar-series-gradient.png)

# Related Topics

 * [Column Series]({{slug:column-series}})
