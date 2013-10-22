---
title: RadLinearGauge Specifics
meta_title: RadLinearGauge Specifics
meta_description: description.
slug: 
tags:radlineargauge,specifics
publish:True
---


Here you can see examples and description of the properties and features specific to RadLinearGauge.

# Controlling the orientation of the gauge

Normally, RadLinearGauge is vertically oriented. You can change this, based on your requirement, by setting the
					__vertical__ property of the control to __false__.
				


 __js__
    


					var orientationGaugeCtrl = new Telerik.UI.RadLinearGauge(document.getElementById("orientationGauge"), {
						value: 24,
						min: 10,
						max: 30,
						vertical: false,
						pointer: {
							color: "#1e98e4"
						}
					});

![Horizontal linear gauge](../Media/Controls\Gauge\gauge-linear-horizontal.png)

# Mirroring the Scale

The ticks and labels are normally shown on the left side of the scale if the gauge is vertical and under the scale  when the gauge is horizontally oriented.
					When the __mirror__ property is set to true, they will be rendered on the right side (vertical gauge) and above the scale
					(horizontal gauge). The following code snippet renders a linear gauge with mirrored scale.
				


 __js__
    


					var mirroredGaugeCtrl = new Telerik.UI.RadLinearGauge(document.getElementById("mirroredGauge"), {
						value: 24,
						min: 10,
						max: 30,
						mirror: true,
						pointer: {
							color: "#1e98e4"
						}
					});

![gauge-linear-mirrored](../Media/Controls\Gauge\gauge-linear-mirrored.png)

# Setting the Pointer

You can access and customize the pointer of RadLinearGauge through its __pointer__ property. This property gets the pointer settings
					represented by the internal __Telerik.UI.Gauge._LinearPointerConfiguration__ class.
					To see all properties exposed by it, check T:Telerik.UI.Gauge._LinearPointerConfiguration. These properties
					allow you to customize track appearance, shape, size and other, basic styles of the pointer.
				

The following code snippets declare a gauge with different pointer shapes. When the pointer shape is set to "barIndicator" (the dafault value), you can
					also customize the __track__ used by the pointer. The track appearance is controlled by the properties listed in the
					T:Telerik.UI.Gauge._LinearPointerTrackConfiguration internal class.
				


 __js__
    


					var barIndicatorPointerGaugeCtrl = new Telerik.UI.RadLinearGauge(document.getElementById("barIndicatorPointerGauge"), {
						value: 24,
						min: 10,
						max: 30,
						pointer: {
							color: "#1e98e4",
							shape: "barIndicator",
							track: {
								color: "#b3e0f1"
							}
						}
					});




 __js__
    


					var arrowPointerGaugeCtrl = new Telerik.UI.RadLinearGauge(document.getElementById("arrowPointerGauge"), {
						value: 24,
						min: 10,
						max: 30,
						pointer: {
							color: "#1e98e4",
							shape: "arrow",
							track: {
								color: "#b3e0f1"
							}
						}
					});

![Gauge pointer shapes](../Media/Controls\Gauge\gauge-linear-pointers.png)

# Hiding the Scale Line

If you want to display only the ranges and pointer, without the scale line, you can set the __line.visible__ property
					of RadLinearGauge to *false*. You can use this in a scenario where you want to display only the colored ranges
					and the pointer, similarly to the following example:
				


 __js__
    


					var hiddenLineGaugeCtrl = new Telerik.UI.RadLinearGauge(document.getElementById("hiddenLineGauge"), {
						min: 0,
						max: 20,
						value: 5,
						ranges: [{
							from: 0,
							to: 10,
							color: '#1e98e4'
						}, {
							from: 10,
							to: 20,
							color: '#40607f'
						}],
						pointer: {
							shape: 'arrow'
						},
						line: {
							visible: false
						}
					});

![gauge-linear-hidden-line](../Media/Controls\Gauge\gauge-linear-hidden-line.png)

# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})
