---
title: Tooltips
meta_title: Tooltips
meta_description: description.
slug: 
tags:tooltips
publish:True
---


RadSparkline displays a tooltip when you hover over one of its data points (a column, pie segment, point on the line, etc.). By default, it displays the value of
				the current data point. This article describes the tooltip's available customization options.
			

# Using a Shared Tooltip

By default, in sparklines that are identified by a category and a value (line, column, bar, area), the tooltip displays them both. However, you can change
					this behavior and display only the value. This is done by setting the __tooltip.shared__ property to *false*.
				![sparkline-tooltip-shared](../Media/Controls\Sparkline\sparkline-tooltip-shared.png)

# Formatting Values

The point value can be formatted using the __format__ property.
				


 __html__
    


				<span id="formatSparkline" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					series: [
						{
							type: 'column',
							field: 'UnitPrice',
							name: 'Unit Price'
						}
					],
					dataSource: {
						data: SampleData.salesPerYear
					},
					categoryAxis: {
						field: 'Year',
						crosshair: {
							visible: false
						}
					},
					tooltip: {
					shared: false,
						format: 'Value: {0:C0}'
					},
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>



The format string supports a subset of the syntax available in Java and C#.
					Here "C0" indicates that the value should be rounded to a whole number and should have a thousands separator and a currency sign.
				![sparkline-tooltip-format](../Media/Controls\Sparkline\sparkline-tooltip-format.png)>
						If a tooltip template is set, the value of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">format</legacyBold> property will be ignored and the template will be
						used instead.
					

# Providing a Template

Tooltip content can be defined with a string template with binding expressions when more flexibility is desired.
					The template provides access to all information associated with the point:
				

* 

__value__: The point value.
						

* 

__category__: The category name.
						

* 

__series__: The data series.
						

* 

__dataItem__: The original data item (when binding to DataSource).
						

For example:


 __html__
    


				<span id="tooltip" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					series: [
						{
							type: 'column',
							field: 'UnitsInStock',
							name: 'Number of Units'
						}
					],
					dataSource: {
						data: SampleData.salesPerYear
					},
					categoryAxis: {
						field: 'Year',
						crosshair: {
							visible: false
						}
					},
					tooltip: {
						shared: false,
						template: '#=series.name#: #=value# &lt;br/&gt; Price: $#=dataItem.UnitPrice#'
					},
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>



will produce the following result:![sparkline-tooltip-template](../Media/Controls\Sparkline\sparkline-tooltip-template.png)>
						To be able to display only your customized tooltip, set the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">tooltip.shared</legacyBold> property to <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">false</legacyItalic>.
						Otherwise, the template will also contain the bolded category name.
					

# Related Topics
