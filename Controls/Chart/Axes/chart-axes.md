---
title: Common Configuration
meta_title: Common Configuration
meta_description: description.
slug: 
tags:common,configuration
publish:True
---


RadChart provides a flexible axis model that allows developers to define different types of axes on their Cartesian charts.
				Categorical series such as Bar, Column and Line use one category axis and one or more value axes. The axis orientation (horizontal or vertical)
				is inferred from the series type. XY charts such as Scatter and Scatter Line use one or more X and Y axes.
			

This help article will introduce you to the common properties between the different axis types.
			

# common-settingsCommon Axis Settings

All types of axes share a common set of properties that can be used for customization. The following list describes
					the set of all common sub-properties of the __categoryAxis__, __valueAxis__,
					__xAxis__ and __yAxis__ properties of RadChart.
				

* 

__axisCrossingValue__: You can control the arrangement of the value axes by specifying the values (category indices) at which they
							cross the category axis. The default value is 0. For example, if you have a categorical chart with two value axes and a category
							axis with three categories, to display the value axes at the two ends of the category one, you should set their crossing values at
							0 and 4 (before the first and after the third category).
						


 __js__
    


					var axisCrossingValueChartCtrl = new Telerik.UI.RadChart(document.getElementById("axisCrossingValueChart"), {
						legend: {
							position: "bottom"
						},
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
							axisCrossingValue: [0, 3]
	
						},
						valueAxis: [{
							name: "temperature",
							labels: {
								format: "{0}C"
							}
						}, {
							name: "humidity",
							labels: {
								format: "{0}%"
							}
						}],
						width: 400,
						height: 300
					});



The first value axis will cross the category axis at the first category (leftmost). The second value axis will cross it at the last category.![chart-multiple-axes-crossing-value](../Media/Controls\Chart\chart-multiple-axes-crossing-value.png)

* 

__baseUnit__: This is the base time interval for the axis when axis values are of Date type. Accepted 
							values are "seconds", "minutes", "hours", "days", "weeks", "months" and "years". The default value is determined automatically from the 
							minimum difference between subsequent categories.
						

* 

__color__: Sets the color to apply to all axis elements. You can use any valid CSS color. If
							you have color settings for lines or labels, they will take precedence over the axis color settings. The default value
							of this property is none (""). Using this property is convenient when you have multiple axes in a chart and you want to make it easy
							to see which series uses which axis. In such a scenario, you can apply the same color to the series and axis.
						

* 

__min__ and __max__: When you want to explicitly define the values at which the axis will
							start and end, use the min and max properties. Their default values are 0 and 1 respectively. Once the chart is aware of its data,
							the max value is dynamically changed to be larger than all values belonging to the current axis.
						

* 

__majorUnit__ and __minorUnit__: These properties set the interval between major and
							minor divisions on the axis. Both properties have a default value of zero.
						   __majorUnit__ determines the step size going up the vertical axis. You
							can additionally have minor steps and ticks in between the major ones by adjusting the __minorUnit__ and 
							__minorTicks.visible__ properties.
						

* 

__majorTicks__ and __minorTicks__: These properties control the visibility and
							appearance of the visual elements, representing major and minor units on the axis. Note that minor ticks are hidden by default, so
							you need to set minorTicks.__visible__ to true in order to see them in the chart. 
							You might also want to modify the __size__ property, which determines the length of the tick lines in pixels.
						

* 

__majorGridLines__ and __minorGridLines__: These properties contain settings for the grid
							lines crossing the chart plot area. There are four available settings: __color__, __dashType__,
							__visible__ and __width__. Minor grid lines are invisible by default.
						

* 

__name__: Gets or sets the unique axis name. Set this property, when you have a scenario of multiple axes
							and you need to assign series to their corresponding axes. The default value is empty string ("").
						

* 

__plotBands__: Gets or sets the plot bands of the axis. Elements of this array must be
							objects of the form { from:0, to: 100, color: '....' }. For more information, go to [](195ceab9-d4cd-42ae-a97d-b489a4096f91).
						

* 

__reverse__: Use this property to reverse the axis direction. Its default value is *false*. 
						

* 

__visible__: controls the visibility of the axis. The default value of the property is true.
						

* 

__title__: a title can be added to clearly indicate the role of the axis. For example:
						


 __html__
    


				<div id="axisTitleChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							legend: {
								position: 'bottom'
							},
							series: [{
								name: 'Temperature',
								data: [20, 25, 32],
								axis: 'temperature',
								color: '#1E98E4'
							}, {
								name: 'Humidity',
								data: [45, 50, 80],
								axis: 'humidity',
								color: '#f99'
							}
							],
							categoryAxis: {
								categories: ['Aug', 'Sep', 'Oct'],
								axisCrossingValue: [0, 3]
							},
							valueAxis: [{
									title: {
										text: 'Temperature, Celsius'
									},
									name: 'temperature'
								}, {
									title: {
										text: 'Relative Humidity'
									},
									name:'humidity'
							}],
								width: 400,
								height: 250
						}">
				</div>

![chart-axis-title](../Media/Controls\Chart\chart-axis-title.png)

* 

__labels__: Numerous settings that you can use to customize the axis labels.
						

* 

__line__: A set of settings used to customize the axis line.
						

# Related Topics
