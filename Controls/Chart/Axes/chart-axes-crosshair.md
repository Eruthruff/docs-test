---
title: Crosshair
meta_title: Crosshair
meta_description: description.
slug: 
tags:crosshair
publish:True
---


From Q2 2013 on, the crosshair is featured in RadChart. It is a functionality that displays a horizontal or vertical (or both) line across the chart plot area, 
				used to precisely locate a certain point on the chart.
			![chart-axes-crosshair](../Media/Controls\Chart\chart-axes-crosshair.png)

# Configuring the Crosshair

By default, neither crosshair line is visible in the chart. To show them, set the __crosshair.visible__
					property of the corresponding axis. For example, in a categorical chart, the crosshair visibility is controlled by the
					__categoryAxis.crosshair.visible__ and __valueAxis.crosshair.visible__ properties; in a XY-chart, the properties to
					set to *true* are __xAxis.crosshair.visible__ and __yAxis.crosshair.visible__.
				

Once you enable the crosshair, here are the available configuration options that you could use for it:

* 

__color__:  The color of the crosshair. Any valid CSS color is accepted.
						

* 

__dashType__:
							You can modify the "texture" of the crosshair line. By setting one of the following values to the __dashType__ property, you
							can choose the pattern of the line that will be drawn:
						

* 

*solid*

* 

*dot*

* 

*dash*

* 

*longDash*

* 

*dashDot*

* 

*longDashDot*

* 

*longDashDotDot*

* 

__opacity__: Controls the crosshair opacity, a value between 0 (transparent) and 1 (opaque) is accepted.
						

* 

__tooltip__: The tooltip settings for the crosshair. They are represented by the internal
							___CrossHairTooltipConfiguration__ class. You can see a list of its members if you go to
							T:Telerik.UI.Chart._CrossHairTooltipConfiguration .
							They allow you to modify the color, background, border, font, format, content template and visibility of the crosshair tooltip.
						

* 

__width__: A numeric value representing the crosshair line width.
						

* 

__zIndex__: A numeric value that determines the zIndex of the crosshair.
						

The example below uses some of these properties to customize the crosshair look and enable its tooltips.


 __html__
    


				<div id="crosshairChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
					  type: 'scatter',
					  xField: 'Quantity',
					  yField: 'Value'
					}],
					xAxis: {
						crosshair: {
							visible: true,
							tooltip: {
								visible: true,
								format: '{0:N2}'
							},
							opacity: 0.5,
							color: 'purple'
						},
					},
					yAxis: {
						crosshair: {
							visible: true,
							tooltip: {
								visible: true,
								format: '{0:N2}'
							},
							opacity: 0.5,
							color: 'green'
						}
					},
					dataSource: {
						data: [
							{Quantity: 10, Value: 10},
							{Quantity: 12, Value: 5},
							{Quantity: 9, Value: 19},
							{Quantity: 15, Value: 13},
							{Quantity: 25, Value: 10},
							{Quantity: 32, Value: 18}
						] 				
					}
				}">
				</div>



The result looks like this:![chart-axes-crosshair-customized](../Media/Controls\Chart\chart-axes-crosshair-customized.png)

# Related Topics
