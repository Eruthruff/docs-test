---
title: Pie Series
meta_title: Pie Series
meta_description: description.
slug: 
tags:pie,series
publish:True
---


Pie series visualize data as arc segments on a radial coordinate system. The sum of all data points in a pie
				series is considered a full pie (a 360-degree arc). Each single data point is represented as a portion of the
				full pie. Thus, the Pie series visualizes data points as a ratio of the total sum of all points.
			![chart-pie-series](../Media/Controls\Chart\chart-pie-series.png)

# 
				Defining a Pie Series Declaratively
			

To define a Pie series in HTML, add an object with __type__ property set to "pie"
				to the __series__ array.
				


 __html__
    


				<div id="declarativePieSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'pie', 
						data: [
							{ value: 16.7, category: 'Europe', explode: true },
							{ value: 20, category: 'North America' },
							{ value: 15.7, category: 'South America' },
							{ value: 26.6, category: 'Asia' },
							{ value: 23.5, category: 'Australia' }
						], 
						labels: { 
							visible: true 
						}
					}]        
				}">
				</div>



# 
				Defining a Pie Series Programmatically
			

To programmatically add a Pie series to the chart, create a new __Telerik.UI.Chart.PieSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var pieSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("pieSeriesChart"));
					var pieSeries = new Telerik.UI.Chart.PieSeries();
					pieSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					pieSeriesChartCtrl.series.push(pieSeries);
					pieSeriesChartCtrl.refresh();



# Configuring a Pie Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Pie series.
				

# Setting the Pie Series Fields

There are three available field settings for the Pie series. Here is a brief description of their usage:

* 

__colorField__: The data field containing the slice color. The field should contain valid CSS colors.
								

* 

__explodeField__: The data field containing the boolean value that indicates if the segment is exploded 
									(separated out from the pie).
								

* 

__categoryField__: The data field containing the pie category name. This field will be used to populate the Pie series
									tooltips, unless they are templated.
								

A simple example of the usage of these fields follows below. Of course, it is not required to have them always set; this would mostly depend on the
							type of data you pass to the chart series.
						


 __html__
    


				<div id="pieSeriesFieldsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'pie',
						field: 'Value',
						categoryField: 'Continent',
						explodeField: 'Highlighted',
						colorField: 'Color',
						labels: {
						  visible: true
						}
					}],
					dataSource: {
						data: [
							{ Value: 26.6, Continent: 'Asia', Highlighted: true, Color: '#014E82' },
							{ Value: 23.5, Continent: 'Australia', Highlighted: false, Color: '#0065A7' },
							{ Value: 16.7, Continent: 'Europe', Highlighted: false, Color: '#00A99E' },
							{ Value: 20, Continent: 'North America', Highlighted: false, Color: '#926CA9' },
							{ Value: 15.7, Continent: 'South America', Highlighted: false, Color: '#B089CC' }
						]				
					}
				}">
				</div>



The resulting chart looks like this:![Setting fields](../Media/Controls\Chart\chart-pie-series-fields.png)

# Setting the Start Angle for Drawing the Series

By default, the first series segment is drawn at 90 degrees. You can change this if you set the __startAngle__ property. Note that the
							segments are ordered clockwise, where a start angle of 0 degrees is equal to 180 degrees in the polar coordinate system. For a better understanding, see the example
							below:
						


 __html__
    


				<div id="startAngleChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'pie', 
					  field: 'Value',
					  categoryField: 'Continent',
					  explodeField: 'Highlighted',
					  colorField: 'Color',
					  labels: { 
						  visible: true 
					  },
					  startAngle: 45
					}],
					dataSource: {
						data: [
							{ Value: 26.6, Continent: 'Asia', Highlighted: true, Color: '#014E82' },
							{ Value: 23.5, Continent: 'Australia', Highlighted: false, Color: '#0065A7' },
							{ Value: 16.7, Continent: 'Europe', Highlighted: false, Color: '#00A99E' },
							{ Value: 20, Continent: 'North America', Highlighted: false, Color: '#926CA9' },
							{ Value: 15.7, Continent: 'South America', Highlighted: false, Color: '#B089CC' }
						]				
					}
				}">
				</div>



Now, the segment, corresponding to Asia will be rendered at a start angle of 45 degrees (which would be 135 degrees in the polar coordinate system):![Changing the start angle](../Media/Controls\Chart\chart-pie-series-start-angle.png)

# Gradient Options

You can easily show a gradient in the Pie series by changing the default value of the __overlayGradient__ property. By default it
							is __"roundedBevel"__, but you could also set it to __"roundedBevel"__ or __"sharpBevel"__ (a solid color
							will fill the series).
						

Example:


 __html__
    


				<div id="noGradientChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'pie', 
						field: 'Value',
						categoryField: 'Continent',
						explodeField: 'Highlighted',
						colorField: 'Color',
						labels: { 
							visible: true 
						},
					overlayGradient: 'sharpBevel'
					}],
					dataSource: {
						data: [
							{ Value: 26.6, Continent: 'Asia', Highlighted: true, Color: '#014E82' },
							{ Value: 23.5, Continent: 'Australia', Highlighted: false, Color: '#0065A7' },
							{ Value: 16.7, Continent: 'Europe', Highlighted: false, Color: '#00A99E' },
							{ Value: 20, Continent: 'North America', Highlighted: false, Color: '#926CA9' },
							{ Value: 15.7, Continent: 'South America', Highlighted: false, Color: '#B089CC' }
						]				
					},
					theme: 'light'
				}">
				</div>

![Modifying the gradient](../Media/Controls\Chart\chart-pie-series-gradient.png)

# Related Topics

 * [Donut Series]({{slug:donut-series}})[How to work with Pie Charts in JavaScript based Application for Windows 8 (Telerik Helper blog)](http://telerikhelper.net/2013/01/02/how-to-work-with-pie-charts-in-javascript-based-application-for-windows-8/)
