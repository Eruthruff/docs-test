---
title: Label Configuration
meta_title: Label Configuration
meta_description: description.
slug: 
tags:label,configuration
publish:True
---


This article describes the properties belonging to the T:Telerik.UI.Chart._AxisLabelConfiguration
				class, which are available when setting the axes' labels.
			

# Section1Axis Label Configuration

Name

Description

__culture__

Changes the culture for the date values. The property takes any valid [BCP-47](http://tools.ietf.org/html/bcp47) language tag as a value.

__background__

To change the background of the axis labels set this property to a valid CSS color.

__border__

Lets you customize the border settings of the labels. Settings include __color__,
								__width__ and __dashType__. __dashType__ accepts
								the following values: "solid", "dot", "dash", "longDash", "dashDot", "longDashDot", "longDashDotDot".
							

__color__

Gets or sets the text color of the axis labels.

__dateFormats__

A set of properties for formatting date values. For more information, see [](50c01a79-c749-4f17-af92-82be1cb2bcaf)

__font__

Gets or sets the labels font.

__format__

Used to provide formatting for values.

__margin__

Used to set the margin around the axis labels. Has __top__, __right__, __bottom__ and
								__left__ options. 
							

__mirror__

When set to true, this property mirrors the axis labels. This means that the labels will be displayed on the
								other side of the axis line (not that their text will be mirrored).
							

__padding__

Used to set the padding around the axis labels. Has __top__, __right__, __bottom__ and
								__left__ options.
							

__rotation__

Use this property when your axis labels need to be rotated at a certain level. This is usually needed when their
								text is too long. You can provide a numeric value representing the angle at which you want the labels rotated.
							

__skip__

This property specifies  the number of labels from the beginning of the axis to skip rendering. For example, you can use it
								in scenarios, where there are no data points in a given range and labels are not needed there.
							

__step__

When you want to skip rendering some of the labels at a known step, use this property. For example, if you want
								to show labels at even ticks only (0-based count), set the __step__ property to 2.
							

__template__

You can provide a template for labels by setting this property. It has a binding context, where the current
								value is available, so you can output it with some content appended or prepended, or hide it on some condition. For
								example, "#= value % 5 == 0 ? value: '' #" will display a label only if its value can be divided by 5 without a 
								remainder.
							

__visible__

Boolean property, controlling the visibility of the axis.

# Configuration Example


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009],
								labels: {
									rotation: 45,
									color: 'white',
									font: '12pt Segoe UI',
									padding: {
										top: 10
									},
									mirror: true
								}
							},
							height: 300,
							width: 600
							}">
				</div>

![chart-axes-labels](../Media/Controls\Chart\chart-axes-labels.png)

# Related Topics
