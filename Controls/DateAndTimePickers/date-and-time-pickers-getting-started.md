---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadDatePicker/RadTimePicker for Windows 8 is an HTML/JavaScript component that by default shows the system date/time in the picker
				as specified by the system short date/time format. It also shows those date/time elements in
				a selector that match the same short date/time format. These and few other elements of the control
				can also be customized to fit in your application requirements.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating the RadDatePicker/RadTimePicker

You can initialize the RadDatePicker/RadTimePicker in a way that is similar to the rest of the
							RadControls for Windows 8 HTML components.
						

# RadDatePicker

To create a RadDatePicker in the HTML markup, add an empty __div__ element
									with a __data-win-control__ attribute
									with a value of __Telerik.UI.RadDatePicker__:
								


 __html__
    


				<div data-win-control="Telerik.UI.RadDatePicker">
				</div>



Alternatively, you can create a RadDatePicker programmatically through JavaScript by first
									defining a __div__ element with an id and then passing it
									as a first argument to the RadDatePicker constructor:
								


 __html__
    


				<div id="myDatePicker">
				</div>




 __js__
    


				    var datePicker = new Telerik.UI.RadDatePicker(document.getElementById("myDatePicker"));



Both ways produce the same result. Here is an image of the control and its usage.
                ![datepicker-gettingstarted](../Media/Controls\DatePicker\datepicker-gettingstarted.png)

# RadTimePicker

To create a RadTimePicker in the HTML markup, add an empty __div__ element
									with a __data-win-control__ attribute
									with a value of __Telerik.UI.RadTimePicker__:
								


 __html__
    


				<div data-win-control="Telerik.UI.RadTimePicker">
				</div>



Alternatively, you can create a RadTimePicker programmatically through JavaScript by first
									defining a __div__ element with an id and then passing it
									as a first argument to the RadTimePicker constructor:
								


 __html__
    


				<div id="myTimePicker">
				</div>




 __js__
    


				    var timePicker = new Telerik.UI.RadTimePicker(document.getElementById("myTimePicker"));



Both ways produce the same result. Here is an image of the control and its usage.
                ![timepicker-gettingstarted](../Media/Controls\TimePicker\timepicker-gettingstarted.png)

# OptionsSetting RadDatePicker/RadTimePicker Options

You can set the options of the RadDatePicker/RadTimePicker in a way that is similar to the rest of the RadControls for Windows 8 HTML components.
						

# RadDatePicker

Just like any other Windows Runtime JavaScript control, the RadDatePicker options can be defined
									through the __data-win-options__ attribute:
								


 __html__
    


	            <!-- Define a date picker allowing the user to choose only month and day during the current year. -->
				<div data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
	                    displayValueFormat: 'MM/dd'
	                }">
				</div>



Alternatively, you can programmatically pass an options object as a second argument
									to the control constructor:
								


 __js__
    


				    // Define a date picker allowing the user to choose only month and day during the current year.
				    var datePicker = new Telerik.UI.RadDatePicker(document.getElementById("myDatePicker"), { format: "MM/dd" });



# RadTimePicker

Just like any other Windows Runtime JavaScript control, the TimePicker options can be defined
									through the __data-win-options__ attribute:
								


 __html__
    


				<div data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
	                     displayValueFormat: 'hh:mm'
	                }">
				</div>



Alternatively, you can programmatically pass an options object as a second argument
									to the control constructor:
								


 __js__
    


				    // Define a time picker allowing the user to choose only hour and minute.
				    var timePicker = new Telerik.UI.RadTimePicker(document.getElementById("myTimePicker"), { format: "hh:mm" });



To see all available configuration options, go to T:Telerik.UI.RadDatePicker

# accessingAccessing and Modifying Date/Time Pickers

You can get ahold of the RadDatePicker/RadTimePicker object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						


 __js__
    


				    var picker = document.getElementById("myPicker").winControl;



Once you have a reference to the control, you can modify its properties as required:


 __js__
    


				    picker.autoSizeWidth = true;



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						


 __js__
    


				    var picker = new Telerik.UI.RadDatePicker(document.getElementById("myPicker"), {
				        onchange: changeHandlerFnName 
				    });
				    // OR
				    var picker = new Telerik.UI.RadDatePicker(document.getElementById("myPicker"), {
				        onchange: function(e) {
				            //...
				        }
				    });

>
								Note that if you attach the event handler as shown above but in HTML mark-up you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							


 __js__
    


				    picker.addEventListener("change", changeHandlerFnName);



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Keyboard Support]({{slug:keyboard-support}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Events]({{slug:events}})
