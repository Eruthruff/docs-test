---
title: Bullet
meta_title: Bullet
meta_description: description.
slug: 
tags:bullet
publish:True
---


The Bullet chart can be used to visualize one or more data points, consisting of two values - a current value, represented by a bar, and a target
				value, represented by a line at the same Y position as the bar. They can be used to represent comparison between an expected and actual value in different
				scenarios - company profit, people's performance, weather measures, etc.
			![chart-bullet-series](../Media/Controls\Chart\chart-bullet-series.png)

# 
				Defining a Bullet Series Declaratively
			

To define a bullet series in HTML, add an object with __type__ property set to "bullet"
				to the __series__ array:
				


 __html__
    


				<div id="declarativeBulletSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'bullet',
						data: [[17, 35],
							   [20, 37],
							   [36, 24],
							   [30, 38]]
					}],
					theme: 'light'
				}">
				</div>



# 
				Defining a Bullet Series Programmatically
			

To programmatically add a Bullet series to the chart, create a new __Telerik.UI.Chart.BulletSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect:
				


 __js__
    


					var bulletSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("bulletSeriesChart"));
					var bulletSeries = new Telerik.UI.Chart.BulletSeries();
					bulletSeries.data = [[17, 35], [20, 37], [36, 45], [30, 38]];
					bulletSeriesChartCtrl.series.push(bulletSeries);
					bulletSeriesChartCtrl.refresh();



# Configuring a Bullet Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Bullet series.
				

# Setting Fields

When binding RadChart to a DataSource, you should set the properties that point to the fields that will be used to populate the chart. The property
							names are:
						

* 

__currentField__: The field that will be used to populate the the current value bar.
								

* 

__targetField__: The field that will be used to locate the target value line.
								

For example:


 __html__
    


				<div data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bullet',
					  currentField: 'current',
					  targetField: 'target'
					}],
					dataSource: {
						data: [ 
							{current: 20, target: 100},
							{current: 38, target: 70},
							{current: 42, target: 57},
							{current: 40, target: 93},
							{current: 22, target: 40},
							{current: 56, target: 72},
							{current: 72, target: 80},
							{current: 35, target: 93} 
						],
					},
					tooltip: {
					  visible: true
					},
					theme: 'light'
					}">
				</div>

![chart-bullet-series-fields](../Media/Controls\Chart\chart-bullet-series-fields.png)

# Customizing the Target Line

The line that represents the target value exposes three main configuration options - __border__, __color__
							and __line__. Below you can see how they can be used to provide a customized look for the target line.
						

* 

__border__: The border settings for the line. They include __color__, 
									__width__ and __dashType__ options. __color__ accepts any valid CSS color.
									__width__ accepts a numeric value that sets the border width. __dashType__ accepts one of the
									following values:  "solid", "dot", "dash", "longDash", "dashDot", "longDashDot", "longDashDotDot".
								

* 

__color__: The line color.
								

* 

__line__: The line settings. To see a detailed description of the available options go to: 
									[](d2a774fd-284c-4a57-abb7-5b9eac22cc5f)

You can see a sample of a RadChart with customized bullet series below:


 __html__
    


				<div data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bullet',
					  currentField: 'current',
					  targetField: 'target',
					  target: {
						color: 'green',
						line: {
							width: 3
						},
						border: {
							width: 1,
							color: 'turquoise'
						}
					  }
					}],
					dataSource: {
						data: [ 
							{current: 20, target: 100},
							{current: 38, target: 70},
							{current: 42, target: 57},
							{current: 40, target: 93},
							{current: 22, target: 40},
							{current: 56, target: 72},
							{current: 72, target: 80},
							{current: 35, target: 93} 
						],
					},
					tooltip: {
					  visible: true
					},
					theme: 'light'
					}">
				</div>

![chart-bullet-series-target](../Media/Controls\Chart\chart-bullet-series-target.png)

# Controlling the Distance Between Categories

Based on your requirement, you can increase or decrease the space between category clusters. This is done by setting the __gap__
          property to an appropriate numeric value. This value represents the proportion between the space between category clusters and the bar width
          (i.e. "gap: 10" means that the bar width will be one tenth of the space between category clusters).
        


 __html__
    


				<div id="categoriesDistanceChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ 
							gap: 10,
							type: 'bullet', 
							data: [[16.7,19], [20,22], [15.7,25], [12,15], [40,28], [23,18]] 
						}
					],
					categoryAxis: {
							categories: ['2000', '2002', '2005', '2008', '2010', '2012']
					},
	                theme: 'light'
				}">
				</div>



You can see how the space increases between categories (Y-axis):![chart-bullet-series-gap](../Media/Controls\Chart\chart-bullet-series-gap.png)

# Related Topics

 * [Vertical Bullet]({{slug:vertical-bullet}})

 * [Common Configuration]({{slug:common-configuration}})
