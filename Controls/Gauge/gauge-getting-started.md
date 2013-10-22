---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


RadGauge for Windows 8 is an HTML/JavaScript component that uses SVG to render high-quality data visualizations. It provides a rich set of APIs for 
				visualizing data in two different ways:
			

* 

Radial gauge - RadRadialGauge

* 

Linear gauge - RadLinearGauge

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a Gauge

To create a RadLinearGauge or RadRadialGauge in the HTML markup, add an empty __div__ element with a __data-win-control__ attribute
							with value of __Telerik.UI.RadLinearGauge__ or __Telerik.UI.RadRadialGauge__:
						

	
							<div data-win-control="Telerik.UI.RadRadialGauge">
							</div>
						



Alternatively, you can create a gauge programmatically through JavaScript by first defining a __div__ element
							with an id and then passing it as a first argument to the gauge constructor:
						

	
							<div id="myGauge">
							</div>
						



	
							var gauge = new Telerik.UI.RadRadialGauge(document.getElementById("myGauge"));
						



Both the examples above render a __RadRadialGauge__ with its default property values - a scale from 0 to 100 with the 
              gauge pointer pointing at 0. For __RadLinearGauge__ the default scale is from 0 to 50.
            ![gauge-radial-gettingstarted](../Media/Controls\Gauge\gauge-radial-gettingstarted.png)

# optionsSetting Gauge Options

Just like any other Windows Runtime JavaScript control, Gauge options can be defined through the __data-win-options__
							attribute:
						

	
							<div data-win-control="Telerik.UI.RadLinearGauge" data-win-options="{theme:'light'}">
							</div>
						



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						

	
							var gauge = new Telerik.UI.RadLinearGauge(document.getElementById("myGauge"), { theme: "light" });
						



Below you can see the full declaration of a RadRadialGauge with:
						

* 

Scale from 0 to 6.

* 

A major unit tick showing for each integer value in the scale.

* 

A pointed value of 4. The color of the pointer is a shade of blue.

* 

Two defined ranges - from 5.5 to 6, colored in red; from 4.5 to 5.5 colored in orange. These ranges have a width of 3px.

	
							var gauge = new Telerik.UI.RadRadialGauge(document.getElementById('myGauge'), {
								min: 0,
								max: 6,
								majorUnit: 1,
								theme: "light",
								value: 4,
								pointer: {
									color: "#1E98E4"
								},
								ranges: [{
									from: 5.5,
									to: 6,
									color: "red"
								}, {
									from: 4.5,
									to: 5.5,
									color: "orange"
								}],
								rangeSize: 3
							});
						



The resulting gauge looks like this:![gauge-radial-ranges](../Media/Controls\Gauge\gauge-radial-ranges.png)

Visit the API documentation to see all available configuration options for T:Telerik.UI.RadLinearGauge 
							or T:Telerik.UI.RadRadialGauge.
						

# accessAccessing and Modifying RadGauge/RadLinearGauge

You can get ahold of the gauge object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						

	
							var gauge = document.getElementById("myGauge").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							autocomplete.max = 220;
						



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [RadLinearGauge Specifics]({{slug:radlineargauge-specifics}})

 * [RadRadialGauge Specifics]({{slug:radradialgauge-specifics}})
