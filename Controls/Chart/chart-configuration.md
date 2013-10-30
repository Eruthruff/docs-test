---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This help article will introduce you to the properties exposed by the RadChart control and describe their usage. In the related help articles you will find 
more information about setting the different objects in the chart control.
			

# Binding RadChart to Data

To bind RadChart to data, you can use its __dataSource__ property for data that is accessible to all chart components. 
To see detailed information about the binding options of RadChart, check this article: [Data Binding](253f6f05-3f32-4ee9-82fb-2e360d156f5f).
				

# Section1Axis Settings

To configure the axes in RadChart, you can access and modify the following properties of the control:

* 

__axisDefaults__: This property lets you set common properties for all axes in the chart, instead of setting them
for each axis individually. For a list of these properties, see the 
T:Telerik.UI.Chart.Axis API reference article.
						

* 

The following list represents all axis types and their settings in RadChart. For detailed information and samples on chart axes, go to
[Chart Axes](5469340a-fd03-4793-9b78-aafcda0bf923).
						

* 

__categoryAxis__: the category axis settings object.
								

* 

__valueAxes__: the array of all value axis defined for the chart.
								

* 

__valueAxis__: the value axis settings object.
								

* 

__xAxes__: the array of all X axes defined for the chart.
								

* 

__xAxis__: tthe X-axis settings when a XY-chart type is used.
								

* 

__yAxes__: the array of all Y axes defined for the chart.
								

* 

__yAxis__: the Y-axis settings when a XY-chart type is used.
								

# Series Settings

The settings for RadChart related to chart series are listed below. For more detailed information, see the __Series__ section of the RadChart
					documentation.
				

* 

__series__: Used to get or set the chart data series.
						

For detailed information on the common series properties, check this article:
							[Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4).
						

To get acquainted with the different types of series and their configuration options, check each type's dedicated topic, under the
							__Series__ section of the documentation.
						

* 

__seriesColors__: Use this property to provide an array of valid CSS color definitions which will be used to
							color the chart series. Note that a single color will be applied to all visual representations of data points (bar, columns, etc.) in a
							single series. If you have only one series defined, without grouping, only one of the listed colors will be applied.
							To provide a different color for each data point, use a data source specifying a valid color in each of its data records and use the
							__colorField__ property of the series.
						

* 

__seriesDefaults__: This property lets you set common properties for all series in the chart, instead of setting them
							for each one individually. For a list of these properties, see
							[Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4).
						

# Chart Tooltip

The chart tooltip can be displayed when the user hovers a series in the RadChart control. Use a chart tooltip to display more information about the current
					data point. Configure it through the __tooltip__ property. For configuration guidelines regarding the tooltip feature,
					go to: [Tooltip](2d4f6986-e8b9-46c6-bcc9-8d9e97f65530).
				

# Chart Legend

The legend is used to display what information the series represent in the chart. To configure the legend's appearance, you can access and modify the
					__legend__ set of options in the chart instance. The legend and its configuration options are described here:
					[Chart Legend](03a5bd22-3ae3-4b2c-afe9-18ccbb4809cf).
				

# Appearance Settings

The following properties control the way the chart appears to the user. Most of them are styling options exposed through properties of the control
					for ease of use.
				

* 

__title__: Represents the title settings of the chart. There are numerous properties exposed here that allow you to
							customize the title. They are listed in the API reference under
							T:Telerik.UI.Chart._TitleConfiguration.
						

* 

__background__: Use it to change the background of the chart area. Any valid CSS color is accepted.
						

* 

__border__: The border settings for the chart. They are represented by the internal
							___BorderConfiguration__ class.
							You can see a list of its members in the API reference under T:Telerik.UI.Common._BorderConfiguration. 
							They allow you to modify the color, width and dash type of the series border.
						

* 

__height__: Used to set the height of the chart area in pixels.
						

* 

__margin__: Gives you access to the margin settings of the chart area. They include __top__,
							__right__, __bottom__ and __left__ properties.
						

* 

__plotArea__: The plot area settings. These include __background__, __border__ and
							__margin__. The border and margin settings are of the same type as those of the chart itself.
						

* 

__theme__: Use it to explicitly specify whether the chart should use a 'light' or 'dark' theme.
						

* 

__width__: Used to set the width of the chart area in pixels.
						

* 

__transitions__: Enables or disables transitions. The default value of this property is true.
						

# Related Topics
