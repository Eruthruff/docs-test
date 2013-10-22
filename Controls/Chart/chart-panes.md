---
title: Chart Panes
meta_title: Chart Panes
meta_description: description.
slug: 
tags:chart,panes
publish:True
---


From Q2 2013 on, RadChart adds panes to its structure. You can optionally use them to split the chart in two or more parts. The panes are ordered from top to
				bottom. Each axis can be associated with a pane.  When you associate a series to an axis, it is shown in the pane that is referenced by the axis. This help article
				describes how you can set up panes and what configuration options they expose.
			

# Using Panes

To display chart series in multiple panes, follow the steps below:

* 

Define your chart with multiple series and multiple value axes.

* 

Define the needed panes, by assigning an array of objects to RadChart’s __panes__ property. Each pane must have a name.
						

* 

At this point all axes and their belonging series will be shown in the first pane. To assign axes to different panes, set each axis’
							__pane__ property to the name of the pane in which you want it to appear.
						

* 

You can also decide the position of the category axis (in Categorical Charts). It also exposes a __pane__ property, so you
							can set it to one of the pane names and the category axis will appear in it. If the axis' __pane__ property is not set, it will
							appear in the top (first) pane.
						

This is an example of a basic scenario with panes:


 __js__
    


					var panesChart = new Telerik.UI.RadChart(document.getElementById("chart1"), {
						series: [{
							name: "Temperature",
							data: [20, 25, 32],
							axis: "temperature",
							color: "#1E98E4"
						}, {
							name: "Humidity",
							data: [45, 50, 80],
							axis: "humidity",
							color: "#f99"
						}
						],
						categoryAxis: {
							categories: ["Aug", "Sep", "Oct"],
							pane: "humidityPane"
						},
						valueAxis: [{
							name: "temperature",
							pane: "temperaturePane",
							labels: {
								format: "{0}C"
							}
						}, {
							name: "humidity",
							pane: "humidityPane",
							labels: {
								format: "{0}%"
							}
						}],
						panes: [
							{
								name: "temperaturePane"
							},
							{
								name: "humidityPane"
							}
						],
						theme: "light",
						width: 500
					});

![chart-panes-simple](../Media/Controls\Chart\chart-panes-simple.png)

# Customizing the Panes

Apart from the required name property of the panes, there are some others that you can use to customize their appearance:

* 

__background__: The background color of the chart pane. Accepts a valid CSS color string, including HEX and RGB.
						

* 

__border__: Lets you customize the border settings of the pane. Settings include __color__,
							__width__ and __dashType__. __dashType__ accepts the following values:
							*"solid"*, *"dot"*, *"dash"*, *"longDash"*,
							*"dashDot"*, *"longDashDot"*, *"longDashDotDot"*.
						

* 

__height__: The RadChart pane height in pixels.
						

* 

__margin__: Used to set the margin around the plot area in the pane. Has *"top"*, *"right"*,
							*"bottom"* and *"left"* options that accept
							numeric values.
						

* 

__padding__: Used to set the padding around the plot area in the pane. Has *"top"*, *"right"*,
							*"bottom"* and *"left"* options that accept
							numeric values.
						

* 

__title__: The settings for the title displayed in the pane. These settings include:
						

* 

__text__: The title text.
								

* 

__background__: The title background. Accepts any valid CSS color.
								

* 

__border__: Lets you customize the border settings of the title. Settings include __color__,
									__width__ and __dashType__. __dashType__ accepts the following values:
									*"solid"*, *"dot"*, *"dash"*,
									*"longDash"*, *"dashDot"*, *"longDashDot"*,
									*"longDashDotDot"*.
								

* 

__color__: Gets or sets the text color of the axis title.
								

* 

__font__: Gets or sets the title font style.
								

* 

__margin__: Used to set the margin around the pane title. It has *"top"*,
									*"right"*, *"bottom"* and *"left"* options that accept
									numeric values.
								

* 

__padding__: Used to set the padding around the pane title. It has *"top"*,
									*"right"*, *"bottom"* and *"left"* options that accept
									numeric values.
								

* 

__position__: You can define the position of the axis title using this property. It accepts the following values:
									*"top"*, *"bottom"*, *"center"*, *"left"*
									and *"right"*.
								

* 

__visible__: A Boolean value controlling the visibility of the pane title.
								

Below you can see an example, demonstrating some of these configuration options:


 __js__
    


					var customizedPanesChart = new Telerik.UI.RadChart(document.getElementById("chart2"), {
						series: [{
							name: "Temperature",
							data: [20, 25, 32],
							axis: "temperature",
							color: "#1E98E4"
						}, {
							name: "Humidity",
							data: [45, 50, 80],
							axis: "humidity",
							color: "#f99"
						}
						],
						categoryAxis: {
							categories: ["Aug", "Sep", "Oct"],
							pane: "humidityPane"
						},
						valueAxis: [{
							name: "temperature",
							pane: "temperaturePane",
							labels: {
								format: "{0}C"
							}
						}, {
							name: "humidity",
							pane: "humidityPane",
							labels: {
								format: "{0}%"
							}
						}],
						panes: [
						{
							name: "temperaturePane",
							title: {
								text: "Temperature",
								font: "20px Segoe UI Light",
							},
							margin: {
								left: 100
							},
							height: 200
						},
						{
							name: "humidityPane",
							title: {
								text: "Humidity",
								font: "20px Segoe UI Light"
							},
							margin: {
								left: 100
							},
							height: 200
						}
						],
						theme: "light",
						width: 500
					});

![chart-panes-customized](../Media/Controls\Chart\chart-panes-customized.png)

# Related Topics
