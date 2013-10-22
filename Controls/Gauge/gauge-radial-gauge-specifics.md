---
title: RadRadialGauge Specifics
meta_title: RadRadialGauge Specifics
meta_description: description.
slug: 
tags:radradialgauge,specifics
publish:True
---


Here you can see examples and description of the properties and features specific to RadRadialGauge.

# Defining the Start and End Angles

Using the __startAngle__ and __endAngle__ properties of RadRadialGauge you can define the angle at which the radial scale will
					start and end. The scale is rendered clockwise, where a start angle of 0 is equal to 180 degrees in the polar coordinate system.
				

By setting the startAngle and endAngle properties accordingly, you can easily create half- and quarter-circle gauges. The below example demonstrates how a quarter
					gauge can be defined:
				


 __js__
    


					var startEndAngleGaugeCtrl = new Telerik.UI.RadRadialGauge(document.getElementById("startEndAngleGauge"), {
						startAngle: 90,
						endAngle: 180,
						value: 50,
						pointer: {
							color: "#1E98E4"
						},
						width: 400
					});

![gauge-radial](../Media/Controls\Gauge\gauge-radial.png)

# Positioning the Ranges

You can define the distance of ranges from the edge of the scale by setting a value to the __rangeDistance__ property. It accepts both positive
				and negative numeric values. A positive value will show the ranges closer to the center of the gauge, while a negative will render the ranges outside of the circle of
				the scale.
			


 __js__
    


					var rangesPositioningGaugeCtrl = new Telerik.UI.RadRadialGauge(document.getElementById("rangesPositioningGauge"), {
						min: 0,
						max: 6,
						majorUnit: 1,
						theme: "light",
						value: 4,
						ranges: [{
							from: 5.5,
							to: 6,
							color: "red"
						}, {
							from: 4.5,
							to: 5.5,
							color: "orange"
						}],
						rangeSize: 3,
						rangeDistance: 30,
						width: 400
					});

![Positioning the ranges](../Media/Controls\Gauge\gauge-radial-range-distance.png)

# Setting the Pointer

You can access and customize the appearance of the pointer of RadRadialGauge through the control's __pointer__ property. This property gets the 
					pointer settings represented by the internal __Telerik.UI.Gauge._RadialPointerConfiguration__ class.
					To see the properties exposed by it, check T:Telerik.UI.Gauge._RadialPointerConfiguration. These properties
					allow you to customize the colors and size of the pointer.
				

The example below sets custom colors to the pointer and the pointer cap, as well as a size to the cap. The __capSize__ property
					accepts values from 0 to 1 representing the part of the whole circle, drawn by the gauge, that will be taken up by the cap.
				


 __js__
    


					var customizedPointerGaugeCtrl = new Telerik.UI.RadRadialGauge(document.getElementById("customizedPointerGauge"), {
						min: 0,
						max: 6,
						majorUnit: 1,
						majorTicks: {
							size: 10
						},
						minorTicks: {
							size: 6
						},
						value: 4,
						pointer: {
							capColor: "#336699",
							capSize: 0.1,
							color: "#33ccff"
						},
						width: 400
					});

![Setting the pointer](../Media/Controls\Gauge\gauge-radial-pointer.png)

# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})
