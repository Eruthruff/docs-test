---
title: Title Configuration
meta_title: Title Configuration
meta_description: description.
slug: 
tags:title,configuration
publish:True
---


This article describes the properties belonging to the T:Telerik.UI.Chart._AxisTitleConfiguration
				class, that are available when setting the axes' title.
			

# Section1Axis Title Configuration

Name

Description

background

To change the background of the axis title set this property to a valid CSS color.

border

Lets you customize the border settings of the title. Settings include __color__,
								__width__ and __dashType__. __dashType__ accepts
								the following values: "solid", "dot", "dash", "longDash", "dashDot", "longDashDot", "longDashDotDot".
							

color

Gets or sets the text color of the axis title.

font

Gets or sets the title font.

margin

Has __top__, __right__, __bottom__ and
								__left__ options. Used to set the margin around the axis title.
							

padding

Has __top__, __right__, __bottom__ and
								__left__ options. Used to set the padding around the axis title.
							

position

You can define the position of the axis title using this property. It accepts the following values:

* 

top

* 

bottom

* 

center

* 

left

* 

right

Depending on the vertical orientation of the axis, you can use these properties to position the text at the
							desired place. For more precise positioning, you can use the margin and padding settings.

rotation

Use this property when your axis title need to be rotated at a certain angle. You can provide a numeric value 
								representing this angle.
							

text

The text to display in the axis title.

visible

A Boolean value controlling the visibility of the axis title.

# Example


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009],
								title: {
									text: 'Year',
									color: 'orange',
									font: '14pt Segoe UI',
									position: 'left',
									padding: {
										top: -10
									}
								}
							},
							valueAxis: {
								title: {
									text: 'Sales',
									color: 'green',
									font: '14pt Segoe UI',
									position: 'bottom',
									padding: {
										right: -10
									}
								}
							},
							height: 300,
							width: 600
							}">
				</div>

![chart-axes-title](../Media/Controls\Chart\chart-axes-title.png)

# Related Topics
