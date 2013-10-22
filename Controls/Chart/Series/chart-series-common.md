---
title: Common Configuration
meta_title: Common Configuration
meta_description: description.
slug: 
tags:common,configuration
publish:True
---


This article will introduce you to the common options of RadChart series. They are all members of the __Telerik.Chart.Series__ class.
			

# Common Options for Chart Series

* 

__border__: The border settings for the series, represented by the internal ___BorderConfiguration__ class.
							You can see a list of its members if you go to T:Telerik.UI.Common._BorderConfiguration. They allow you to
							modify the color, width and dash type of the series border.
						


 __html__
    


				<div id="borderSettingChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
							border: {
								dashType: 'longDashDotDot',
								width: 1,
								color: '#33ccff'
							},
							opacity:0.8,
							name: 'Example Series',
							type: 'column',
							data:[{
								value: 40,
								category: 'Apples'
							}, 
							{
								value: 60,
								category: 'Oranges'
							}]
					}]
				}">
				</div>



With the above declaration, you will get a chart like this one:![Customizing border](../Media/Controls\Chart\chart-common-border.png)

* 

__color__: You can use it to assign the base color of the series.
						

* 

__colorField__: Applicable for all series having a separate representation of each data point (column, bar, bubble, etc.).
							Points to a field in the data source containing a valid CSS color. This color will be applied to the current data point. Note that in such a case
							a single series will have many colors, so they will not be in sync with the single color per series, displayed in the chart legend.
						

* 

__data__: Through this property you can assign an array of data points for the series.
						


 __html__
    


				<div id="colorSettingChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						name: 'Example Series',
						type: 'pie',
						data:[{
							value: 40,
							category: 'Apples'
						},
						{
							value: 60,
							category: 'Oranges',
							color: '#ff6103'
						}]
					}]
				}">
				</div>



* 

__field__: Represents the data field containing the series value. It is meaningful when you are binding the chart to a datasource
							and you want to assign a certain field as a source of data points for the series.
						

* 

__groupNameTemplate__: This is a name template for auto-generated series when binding to grouped data. The template variables are:
						

* 

__series__: The series options.
								

* 

__group__: The data group.
								

* 

__group.field__: The name of the field used for grouping.
								

* 

__group.value__: The field value for this group.
								

The following example shows how to use a groupNameTemplate.


 __js__
    


					var groupedChart = new Telerik.UI.RadChart(document.getElementById("groupSeriesChart"), {
						series: [{
							type: 'area',
							name: 'close',
							field: 'close',
							groupNameTemplate: '#= group.value # (#= series.name #)'
	
						}],
						dataSource: {
							data: [
								{ date: new Date(30, 11, 2011), close: 405, volume: 6414369, open: 403.51, high: 406.28, low: 403.49, symbol: '2. AAPL' },
								{ date: new Date(30, 10, 2011), close: 382.2, volume: 14464710, open: 381.29, high: 382.276, low: 378.3, symbol: '2. AAPL' },
								{ date: new Date(31, 4, 2011), close: 196.69, volume: 3405698, open: 195.94, high: 198.44, low: 195.03, symbol: '3. AMZN' },
								{ date: new Date(28, 1, 2011), close: 173.29, volume: 6781774, open: 173.91, high: 175.89, low: 172.15, symbol: '3. AMZN' }
							],
							group: {
								field: 'symbol'
							},
	
							sort: {
								field: 'date',
								dir: 'asc'
							}
						},
						legend: {
							position: 'bottom'
						},
						valueAxis: {
							labels: {
								format: '${0}',
								skip: 2,
								step: 2
							}
						},
						categoryAxis: {
							field: 'date',
							labels: {
								format: 'MMM'
							}
						}
					});

![Group name template](../Media/Controls\Chart\chart-common-group-name-template.png)

* 

__labels__: The settings for the series labels. They are represented by the internal ___LabelConfiguration__ class.
							You can see a list of its members if you go to T:Telerik.UI.Chart._LabelConfiguration. They allow you to
							modify the styling or the entire look (through a template) of the labels.
						


 __html__
    


				<div id="labelsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
							name: 'Example Series',
							type: 'column',
							data:[{
								value: 40,
								category: 'Apples'
							}, 
							{
								value: 60,
								category: 'Oranges'
							}],
							labels: {
								visible: true,
								color: 'blue',
								template: 'Count: #=value#'
						}
					}]
				}">
				</div>



The image below shows the resulting chart.![Showing labels](../Media/Controls\Chart\chart-common-labels.png)

* 

__name__:  Represents the series name that will be displayed in the legend.
						

* 

__opacity__: You can assign a value between 0 (transparent) and 1 to control the opacity of the series. The default value is 1.
						

* 

__stack__: A value indicating if the series should be stacked. To stack two series, set their __stack__
							property to the same string value. You can combine series in more than one stack.
						

* 

__tooltip__: If you allow it, a tooltip will show when you hover over the series. By default, a tooltip contains the series value, but you could
							modify its content through a template. This is achieved using the __tooltip__ settings for the series. They are represented by the
							internal ___TooltipConfiguration__ class.
							You can see a list of its members if you go to T:Telerik.UI.Chart._TooltipConfiguration. They allow you to
							modify the styling or the entire look (through a template) of the tooltips.
						


 __html__
    


				<div id="tooltipChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series:[{
						name: 'Example Series',
						type: 'column',
						data:[{
							value: 40,
							category: 'Apples'
						}, 
						{
							value: 60,
							category: 'Oranges'
						}],
						tooltip: {
							visible: true,
							template: 'Name: #=dataItem.category# &lt;br/&gt; Count: #=value#'
						},
					}]
				}">
				</div>



The image below shows the resulting tooltip.![Customizing tooltips](../Media/Controls\Chart\chart-common-tooltips.png)

* 

__type__: Use this property to get or set the type of the series you are currently working with. The default value is 'column'.
						

* 

__visibleInLegend__: A Boolean property that indicates whether or not the series will be shown in the legend.
						

# Combining Series

There are series types that you can combine together to visualize related information. There are however some limitations related to the
					nature of the series, that you should have in mind:
				

* 

You cannot combine one type of XY-series with another. You can only have multiple series from the same type in one chart.

* 

You cannot combine radial series together or with another type of series.

* 

You cannot combine bar and column series in one chart. To visualize multiple categorical fields, you can use bar or column series together
							with line or area series.
						

# Related Topics
