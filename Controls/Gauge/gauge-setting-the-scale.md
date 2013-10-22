---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article will introduce you to the common properties of RadLinearGauge and RadRadialGauge used to set/customize the controls' scale.
			

# Section1Setting the Scale

The properties that control the look of the scale are:

* 

__labels__: Retrieves the label settings for the current gauge. These settings control the
							look of the labels appearing next to each major tick. They are of type
							__Telerik.UI.Gauge._LabelConfiguration__. To see the available settings click to go to the API documentation:
							T:Telerik.UI.Gauge._LabelConfiguration.
						

* 

__majorTicks__: Retrieves the major tick settings. These settings control the look of the ticks
							marking the major units of the scale. They are of type
							__Telerik.UI.Gauge._TickConfiguration__. To find all available settings click to go to the API documentation:
							T:Telerik.UI.Gauge._TickConfiguration.
						

* 

__majorUnit__: A numeric value representing the interval between major divisions of the scale.
							For example, if the scale starts at __0__, ends at __6__ and the
							__majorUnit__ property is set to __3__, major ticks with
							accompanying labels will appear for the values __3__ and __6__.
						

* 

__max__: A numeric value representing the maximum value of the scale (the value at which
							the scale will end).
						

* 

__min__: A numeric value representing the minimum value of the scale (the value at which
							the scale will start).
						

* 

__minorTicks__: Retrieves the minor tick settings. These settings control the look of the ticks
							marking the minor units of the scale. They are of type
							__Telerik.UI.Gauge._TickConfiguration__. To find all available settings go to:
							T:Telerik.UI.Gauge._TickConfiguration.
						

* 

__minorUnit__: A numeric value representing the interval between minor divisions of the scale.
						

* 

__ranges__: An array of ranges that will appear on the scale. These are a way to highlight a part
							of the scale. They could be used to mark a range of critical values that can be reached. For example, RPM range that is unsafe.
						

* 

__rangeSize__: The width of the ranges that will appear on the scale. If the property is not set, it will
							be calculated to 10% of the scale radius.
						

The code snippet below demonstrates the usage of these properties to customize the formatting and appearance of the scale.
					Note that for the purpose of this example, no value is set to the gauge.
				


 __html__
    


				<div id="linearGauge" data-win-control="Telerik.UI.RadLinearGauge" data-win-options="{
							labels: {
								color: '#336699',
								format: '{0:C}'
							},
							majorTicks: {
								color: '#000',
								width: 1,
								size: 15
							},
							majorUnit: 10000,
							max: 50000,
							min: 0,
							minorTicks: {
								color: '#0f9d46',
								width: 1,
								size: 10
							},
							minorUnit: 5000,
							ranges: [{
										from: 40000,
										to: 50000,
										color: '#ff0000'
									}, {
										from: 30000,
										to: 40000,
										color: '#ffcc00'
									}],
							rangeSize: 5,
							width: 500
						}">
				</div>



The following image displays the result from the above declaration and from the same data-win-options applied on a RadRadialGauge. ![Setting the scale](../Media/Controls\Gauge\gauge-scale.png)

# Related Topics
