---
title: Chart Legend
meta_title: Chart Legend
meta_description: description.
slug: 
tags:chart,legend
publish:True
---


The legend is used to display what information is presented by the series in the chart. For each series, the legend displays a token having the same color as
				the series and a label containing name of the series. When the user clicks/taps a legend item, the corresponding series' visibility is toggled (if the series is
				visible, it is hidden and vice versa). To configure the appearance of the legend, you can access and modify the __legend__ set of
				options in the chart instance. Below you can read more detailed information about the properties of the __legend__ object.
			![Chart legend](../Media/Controls\Chart\chart-legend.png)

# Section1Customizing the Chart Legend

The legend object exposes the following properties for customization:

* 

__background__: Use it to change the background of the legend. You can set it to any valid CSS color.
						

* 

__border__: This is a group of settings for the border around the legend. By default there is no border, but
							by setting the __color__, __dashType__ and __width__ properties,
							you can display a customized one.
						


 __html__
    


				<div id="borderSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{ 
								type: 'pie', 
								data: [
									{ value: 16.7, category: 'Europe', explode: true },
									{ value: 20, category: 'North America' },
									{ value: 15.7, category: 'South America' },
									{ value: 26.6, category: 'Asia' },
									{ value: 23.5, category: 'Australia' }
								], 
								labels: { 
									visible: true 
								}
							}],
							legend: {
								border: {
									color:'#336699',
									width: 1,
									dashType: 'dot'
								}
							}
						}">
				</div>



* 

__inactiveItems__: This property allows you to customize the appearance of inactive legend items. This property has two
							sub-properties that allow you to customize inactive legend items—__labels__ and __markers__. 
							Both properties have a __color__ option whose value can be any valid CSS color.
						

* 

__labels__: These are settings for the labels displaying the series names. You can customize them through the
							__color__ and __font__ properties.
						


 __html__
    


				<div id="labelsSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{ 
								type: 'pie', 
								data: [
									{ value: 16.7, category: 'Europe', explode: true },
									{ value: 20, category: 'North America' },
									{ value: 15.7, category: 'South America' },
									{ value: 26.6, category: 'Asia' },
									{ value: 23.5, category: 'Australia' }
								], 
								labels: { 
									visible: true 
								}
							}],
							legend: {
								labels: {
									color: '#fff',
									font: 'Segoe UI'
								}
							}
						}">
				</div>



* 

__margin__: Through this property you can change the margin around the legend. It has
							__bottom__, __left__, __right__ and __top__
							options that all accept numeric values.
						

* 

__offsetX__: This property represents the X offset of the legend from its preset position. Assign it a numeric
							value representing the offset of the legend in pixels (negative values will move the legend to the left).
						

* 

__offsetY__: This property represents the Y offset of the legend from its preset position. Assign it a numeric
							value representing the offset of the legend in pixels (negative values will move the legend up the screen).
						

* 

__padding__: Through this property you can change the padding of the legend. It has
							__bottom__, __left__, __right__ and __top__
							options that all accept numeric values.
						

* 

__position__: To position the legend at the different sides of the chart, set this property to one of the
							accepted values: *"top"* , *"bottom"*, *"left"*,
							*"right"*, *"custom"*. When a value of *"custom"* is used,
							the legend is positioned using its __offsetX__ and __offsetY__ properties. Default value is
							*"right"*.
						

* 

__visible__: Controls the visibility of the legend. By default its value is *true*
							and the legend is visible.
						

# Related Topics
