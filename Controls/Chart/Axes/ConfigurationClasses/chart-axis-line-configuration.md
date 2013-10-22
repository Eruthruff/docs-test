---
title: Line Configuration
meta_title: Line Configuration
meta_description: description.
slug: 
tags:line,configuration
publish:True
---


This help article describes the properties belonging to the T:Telerik.UI.Chart._AxisLineConfiguration
				class, which are available when setting the axes' lines.
			

# Section1Axis Line Configuration

Name

Description

__color__

Controls the color of the axis line. Accepts any valid CSS color as value.
							

__dashType__

You can modify the "texture" of the axis line. By setting one of the following values to the __
							dashType__ property, you can choose the pattern of the line that will be drawn:
						

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

__visible__

A Boolean property that controls the visibility of the axis line.

__width__

Use this property to set the line width in pixels. It accepts numeric values.

# Example


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							valueAxis: {
								line: {
									color: 'cyan',
									width: 2
								},
								majorTicks: {
									size: 10
								}
							},
							height: 300,
							width: 600
				}">
				</div>

![chart-axes-line](../Media/Controls\Chart\chart-axes-line.png)

# Related Topics
