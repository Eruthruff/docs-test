---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadNumericBox for Windows 8 is an HTML/JavaScript component that allows the user to choose a numeric value
				(numeric, percentage or currency) either by typing it manually in the input provided by the component
				or by using the increment/decrement spin buttons.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadNumericBox

To create a RadNumericBox in the HTML markup, add an empty __span__
							or __div__ element with a __data-win-control__ attribute
							with a value of __Telerik.UI.RadNumericBox__:
						

	
							<span data-win-control="Telerik.UI.RadNumericBox">
							</span>
						



Alternatively, you can create a RadNumericBox programmatically through JavaScript by first
							defining a __span__ element with an __id__ set and then passing it
							as a first argument to the NumericBox constructor:
						

	
							<span id="myNumericBox">
							</span>
						



	
							var numericBox = new Telerik.UI.RadNumericBox(document.getElementById("myNumericBox"));
						



Defining __RadNumericBox__ without setting any properties will result in the default __RadNumericBox__ 
              setup. The number is limited to two digits after the floating point and the increment/decrement step of the control is 1. Here is an image of the 
              __RadNumericBox__.
            ![numericbox-gettingstarted](../Media/Controls\NumericBox\numericbox-gettingstarted.png)

# optionsSetting RadNumericBox Options

Just like any other Windows Runtime JavaScript control, the RadNumericBox options can be defined
							through the __data-win-options__ attribute:
						

	 Define a currency type numeric box with 2 digits precision. 



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						

	
							// Define a currency type numeric box with 2 digits precision.
							var numericBox = new Telerik.UI.RadNumericBox(document.getElementById("myNumericBox"), { format: "c2" });
						



To see all available configuration options in the API, go to T:Telerik.UI.RadNumericBox.
						

# accessingAccessing and Modifying RadNumericBox

You can get ahold of the RadNumericBox object the same way as the native WinJS components: find its DOM element and access its
							__winControl__ property.
						

	
							var numericBox = document.getElementById("myNumericBox").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							numericBox.decimals = 3;
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches.
						

	
							var numericBox = new Telerik.UI.RadNumericBox(document.getElementById("myNumericBox"), {
								onspin: spinHandlerFnName 
							});
							// OR
							var numericBox = new Telerik.UI.RadNumericBox(document.getElementById("myNumericBox"), {
								onspin: function(e) {//...}
							});
						

>
								If you attach the event handler in the HTML mark-up, you need to mark the handler function as safe
								in your code using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							numericBox.addEventListener("spin", spinHandlerFnName);
						



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})[Formatting numbers in RadNumericBox](5be00934-bb4a-4d64-b7e1-1dc3434ed4b7)

 * [Events]({{slug:events}})
