---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The two types of sliders for Windows 8 are HTML/JavaScript components that are represented by the corresponding
				__RadSlider__ and __RadRangeSlider__ types.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating Sliders

You can initialize the two types of sliders in a straightforward and similar way.
						

To create a __RadSlider__ in the HTML markup, add an empty __div__ element
							with a __data-win-control__ attribute
							with a value of __Telerik.UI.RadSlider__ or __RadRangeSlider__.
						

	
							<div data-win-control="Telerik.UI.RadSlider">
							</div>
						



	
							<div data-win-control="Telerik.UI.RadRangeSlider">
							</div>
						



Alternatively, you can create a RadSlider programmatically through JavaScript by first
							defining a __div__ element with an id and then passing it
							as a first argument to the RadSlider constructor:
						

	
							<div id="mySlider">
							</div>
						



	
							var slider = new Telerik.UI.RadSlider(document.getElementById("mySlider"));
						



	
							<div id="myRangeSlider">
							</div>
						



	
							var rangeSlider = new Telerik.UI.RadRangeSlider(document.getElementById("myRangeSlider"));
						



Defining __RadSlider__ or __RadRangeSlider__ without setting any options will result in initializing the 
              default versions of the controls. For __RadSlider__ the default scale is from 0 to 10 with the measure staying at 0. Here is an 
              image for reference:
            ![slider-gettingstarted](../Media/Controls\Slider\slider-gettingstarted.png)

For __RadRangeSlider__ the default scale is from 0 to 10 with the whole range of the scale being initially selected. Here is an 
              image for reference:
            ![slider-range-gettingstarted](../Media/Controls\Slider\slider-range-gettingstarted.png)

# optionsSetting RadSlider Options

You can set the options of the two types of sliders in a straightforward and similar way.
						

Just like any other Windows Runtime JavaScript control, the RadSlider options can be defined
								through the __data-win-options__ attribute.
							

	 Define a vertical slider. 



	 Define a vertical range slider. 



Alternatively, you can programmatically pass an options object as a second argument
								to the control constructor.
							

	
								// Define a vertical slider.
								var slider = new Telerik.UI.RadSlider(document.getElementById("mySlider"), {
									orientation: "vertical"
								});
							



	
								// Define a vertical range slider.
								var rangeSlider = new Telerik.UI.RadRangeSlider(document.getElementById("myRangeSlider"), {
									orientation: "vertical"
								});
							



Here is an image of the controls with the __orientation__ property value set to *"vertical"*:
              ![slider-vertical-gettingstarted](../Media/Controls\Slider\slider-vertical-gettingstarted.png)

# accessingAccessing and Modifying Slider Controls

You can get ahold of the RadSlider/RadRangeSlider object the same way as the native WinJS components—find its DOM element and access its
							__winControl__ property.
						

	
							var slider = document.getElementById("mySlider").winControl;
						



Once you have a reference to the control, you can modify its properties as required.

	
							slider.decimals = 3;
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var slider = new Telerik.UI.RadRangeSlider(document.getElementById("mySlider"), {
								onslide: slideHandlerFnName
							});
							// OR
							var slider = new Telerik.UI.RadRangeSlider(document.getElementById("mySlider"), {
								onslide: function(e) {//...}
							});
						

>
								If you attach the event handler using the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">on[eventname]</legacyBold> property in HTML mark-up, you would need to mark the handler 
								function as safe in your JavaScript code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							slider.addEventListener("slide", slideHandlerFnName);
						



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Tooltip]({{slug:tooltip}})

 * [Events]({{slug:events}})
