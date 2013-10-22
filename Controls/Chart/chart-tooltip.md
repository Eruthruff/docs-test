---
title: Tooltip
meta_title: Tooltip
meta_description: description.
slug: 
tags:tooltip
publish:True
---


RadChart can display details about the part of the series that the mouse is currently hovering over. The tooltip appearance and content can be greatly customized, using
				the properties listed in this help article.
			![chart-tooltip](../Media/Controls\Chart\chart-tooltip.png)

# Configuration

The tooltip is not visible by default. You can enable it by setting the __visible__ property of the tooltip object to
					*true*.
				


 __html__
    


				<div id="tooltipConfigurationChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								type: 'bar',
								name: 'United States',
								data: [67.96, 68.93, 75, 74, 78]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							tooltip: {
								visible: true
							}
						}">
				</div>



The tooltip can also be configured per-series.


 __html__
    


				<div id="tooltipSeriesConfigurationChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								type: 'bar',
								name: 'United States',
								data: [67.96, 68.93, 75, 74, 78],
								tooltip: {
								  visible: true
								}
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							}
						}">
				</div>



# Formatting Values

You can format the point value using the __format__ property.
				

The number of format variables depends on the series type:
				

* 

Area, Bar, Column, Line, and Pie charts have one variable: 0—value;
						

* 

Bubble, Scatter and Scatter Line charts have two variables: 0—X value and 1—Y value.
						

* 

Candlestick and OHLC charts have five variables: 0—open value, 1—high value, 2—low value, 3—close value, and 4—category name.
						

To see what are the available formats that you can apply to the tooltip values, go to: [](0c3b0ea5-3850-4c90-86b3-5d20f2a18c1e).
			

In the following example, "N0" indicates that the value should be rounded to a whole number and should have a thousands separator.
				


 __html__
    


				<div id="formattedTooltipChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								type: 'bar',
								name: 'United States',
								data: [67.96, 68.93, 75, 74, 78]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							tooltip: {
								visible: true,
								format: 'Value: {0:N0}'
							}
						}">
				</div>

>
						If a tooltip template is set, the value of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">format</legacyBold> property will be ignored and the template will be
						used instead.
					

# Templates

Tooltip content can be defined with a string template with binding expressions when more flexibility is desired.
					The template provides access to all information associated with the point:
				

* 

__value__: The point value. Value dimensions are available as properties, for example, value.x and value.y
						

* 

__category__: The category name.
						

* 

__series__: The data series.
						

* 

__dataItem__: The original data item (when binding to DataSource).
						


 __html__
    


				<div id="templatedTooltipChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								name: 'Example Series',
								data: [200, 450, 300, 125]
							}],
							categoryAxis: {
								categories: [2000, 2001, 2002, 2003]
							},
							tooltip: {
								visible: true,
								template: '#=category# : #=value#'
							}}">
				</div>



# Using Shared Tooltip

When you implement a categorical chart with multiple series, you can use a shared tooltip for them. This means that a single tooltip will be
					displayed per category, containing information about all series. To enable this feature, set __tooltip.shared__ to
					*true*. For example:
				


 __html__
    


				<div id="sharedTooltipChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'bar',
						name: 'Temperature',
						data: [20, 25, 32],
						color: '#1E98E4'
					}, {
						type: 'bar',
						name: 'Humidity',
						data: [45, 50, 80],
						color: '#f99'
					}],
					categoryAxis: {
						categories: ['May', 'June', 'July']
					},
					tooltip: {
						visible: true,
						shared: true
					},
					width: 600
				}">
				</div>



With such declaration, the tooltip will look like this:![chart-tooltip-shared](../Media/Controls\Chart\chart-tooltip-shared.png)

# Templating the Shared Tooltip

To customize the content of the shared tooltip, use its __tooltip.sharedTemplate__ property. The fields which can be used
					in the template are:
				

* 

__points__: An array of all series data points that belong to the current category.
						

* 

__category__: The current category name.
						


 __html__
    


				<div id="sharedTooltipTemplateChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'bar',
						name: 'Temperature',
						data: [20, 25, 32],
						color: '#1E98E4'
					}, {
						type: 'bar',
						name: 'Humidity',
						data: [45, 50, 80],
						color: '#f99'
					}],
					categoryAxis: {
						categories: ['May', 'June', 'July']
					},
					tooltip: {
						visible: true,
						shared: true,
						sharedTemplate: '#=points[0].series.name#/#=points[1].series.name#: #=points[0].value#/#=points[1].value#'
					},
					width: 600
				}">
				</div>



And the resulting template:![chart-tooltip-shared-template](../Media/Controls\Chart\chart-tooltip-shared-template.png)

# Related Topics
