---
title: Donut Series
meta_title: Donut Series
meta_description: description.
slug: 
tags:donut,series
publish:True
---


Donut series visualize data as arc segments on a radial coordinate system. The sum of all data points in a Donut
				series is considered a full Donut (a 360-degree arc). Each single data point is represented as a portion of the
				full Donut. Thus, the Donut series visualizes data points as a ratio of the total sum of all points.
			![chart-donut-series](../Media/Controls\Chart\chart-donut-series.png)

# 
				Defining a Donut Series Declaratively
			

To define a Donut series in HTML, add an object with __type__ property set to "donut"
					to the __series__ array.
				


 __html__
    


				<div id="declarativeDonutSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						field: 'value',
						type: 'donut', 
						labels: { 
							visible: true 
						}
					}],
					dataSource: {
						data: [
							{ value: 16.7, category: 'Europe', explode: true },
							{ value: 20, category: 'North America' },
							{ value: 15.7, category: 'South America' },
							{ value: 26.6, category: 'Asia' },
							{ value: 23.5, category: 'Australia' }
						]
					}        
				}">
				</div>



# 
				Defining a Donut series programmatically
			

To programmatically add a Donut series to the chart, create a new __Telerik.UI.Chart.DonutSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var donutSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("donutSeriesChart"));
					var donutSeries = new Telerik.UI.Chart.DonutSeries();
					donutSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					donutSeriesChartCtrl.series.push(donutSeries); //chart is the RadChart control instance
					donutSeriesChartCtrl.refresh();



# Configuring Donut Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Donut series. They follow below.
				

# Setting the Donut Series Fields

There are three available field settings for the Donut series. Here is a brief description of their usage.

* 

__colorField__: The data field containing the Donut color. The field should contain valid CSS colors.
								

* 

__explodeField__: The data field containing the Boolean value that indicates if the sector is exploded.
								

* 

__categoryField__: The data field containing the bubble category name. This field will be used to populate the bubble series
									tooltips.
								

A simple example of the usage of these fields follows below. Of course, it is not required to have them always set; this would mostly depend on the
							type of data you pass to the chart series.
						


 __html__
    


				<div id="donutSeriesFieldsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'donut', 
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



The resulting chart looks like this:![Setting fields](../Media/Controls\Chart\chart-donut-series-fields.png)

# Changing the Hole Size

The size of the donut hole is controlled by the __holeSize__ property. It accepts numeric values representing the diameter of the hole in
							pixels.
						


 __html__
    


				<div id="holeSizeChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'donut', 
						field: 'Value',
						categoryField: 'Continent',
						explodeField: 'Highlighted',
						colorField: 'Color',
						labels: { 
							visible: true 
						},
					holeSize: 70,
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



This will produce a chart like the one shown below:![Changing the hole size](../Media/Controls\Chart\chart-donut-series-hole-size.png)

# Setting the Start Angle for Drawing the Series

By default, the first series segment is drawn at 90 degrees. You can change this if you set the __startAngle__ property. Note that the
							segments are ordered clockwise, where a start angle of 0 degrees is equal to 180 degrees in the polar coordinate system. For a better understanding, see the example
							below.
						


 __html__
    


				<div id="startAngleChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					  series: [{ 
						  type: 'donut', 
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



Now the segment corresponding to Asia will be rendered at a start angle of 45 degrees (which would be 135 degrees in the polar coordinate system):![45 degrees start angle](../Media/Controls\Chart\chart-donut-series-start-angle.png)

# Modifying the Donut Size

The __size__ property represents the width of the donut ring. If the value is not set, it will be automatically calculated based on the
							chart size.
						


 __html__
    


				<div id="donutSizeChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'donut',  
					  field: 'Value',
					  categoryField: 'Continent',
					  explodeField: 'Highlighted',
					  colorField: 'Color',
					  labels: { 
						  visible: true 
					  },
					size: 30
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

![Modifying the donut size](../Media/Controls\Chart\chart-donut-series-size.png)

# Gradient Options

You can easily show a gradient in the Donut series by changing the default value of the __overlayGradient__ property. By default, it
							is __"none"__ and a solid color fills the series, but you could also set it to __"glass"__ or
							__"roundedBevel"__.
						

Example:


 __html__
    


				<div id="gradientChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'donut',  
						field: 'Value',
						categoryField: 'Continent',
						explodeField: 'Highlighted',
						colorField: 'Color',
						labels: { 
							visible: true 
						},
					overlayGradient: 'roundedBevel'
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

![Showing gradient](../Media/Controls\Chart\chart-donut-series-gradient.png)

# Styling the connectors

Connectors are the lines connecting the Donut sectors with their corresponding values. Through the __connectors__ options you can set
							__color__, __padding__ and __width__ for these lines.
						


 __html__
    


				<div id="connectorsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'donut', 
						field: 'Value',
						categoryField: 'Continent',
						explodeField: 'Highlighted',
						colorField: 'Color',
						labels: { 
							visible: true 
						},
						connectors: {
							padding: 5,
							color: 'green',
							width: 2
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

![Styling the connectors](../Media/Controls\Chart\chart-donut-series-connectors.png)

# Related Topics

 * [Pie Series]({{slug:pie-series}})
