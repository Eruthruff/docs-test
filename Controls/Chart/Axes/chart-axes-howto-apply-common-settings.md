---
title: Apply Common Settings to All Axes
meta_title: Apply Common Settings to All Axes
meta_description: description.
slug: 
tags:apply,common,settings,to,all,axes
publish:True
---


# default-settingsSpecifying Default Settings for All Axes

RadChart allows developers to specify common options for all chart axes in one place. The __axisDefaults__
				  property can be used to specify axis settings that will be copied over to every axis used in the current RadChart instance. Note that properties
				  explicitly defined on different axis instances will override any defaults set through the __axisDefaults__ property.
			  


 __html__
    


				<div id="defaultSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{ data: [15.7, 16.7, 20, 23.5, 26.6] }
							],
							axisDefaults: {
								labels: {
									color: 'blue',
									font: '16px Verdana'
								},
								minorTicks: {
									visible: true
								}
							},
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009],
								minorTicks: {
									visible: false
								}
							},
							valueAxis: {
								labels: {
									color: 'green'
								}
						}}">
				</div>



In the above code sample, the label and minorTick settings defined by the __axisDefaults__ property
				  will be applied to both axes. However, the category axis overwrites the default minorTicks settings, while the value axis
				  overwrites the label settings. Common settings defined on the specific axis object take precedence.
			  

# Related Topics

 * [Category Axis]({{slug:category-axis}})

 * [Value Axis]({{slug:value-axis}})
