---
title: Tick Configuration
meta_title: Tick Configuration
meta_description: description.
slug: 
tags:tick,configuration
publish:True
---


This article describes the properties belonging to the T:Telerik.UI.Chart._AxisTickConfiguration
				class, which are available when setting the axes' ticks.
			

# Section1Axis Tick Configuration

Name

Description

__size__

Use this property to change the length of the tick lines. It accepts a numeric value which is then applied as
								length in pixels.
							

__visible__

A Boolean property controlling the visibility of ticks on the axis.

# Example


 __html__
    


				<div id="Div1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							valueAxis: {
								majorTicks: {
									size: 15
								}
							},
							height: 300,
							width: 600
				}">
				</div>

![chart-axes-tick](../Media/Controls\Chart\chart-axes-tick.png)

# Related Topics
