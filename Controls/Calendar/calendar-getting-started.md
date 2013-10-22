---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The __RadCalendar__ control for Windows 8 is a powerful HTML/JavaScript component for visualizing and selecting dates. It provides intuitive UI, fast and fluid
				navigation, templates, easy to use API, etc. Configuring it requires minimum effort and saves you loads of time for achieving the same result from scratch.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to a HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# createCreating a RadCalendar

To create a __RadCalendar__ in the HTML markup, add an empty div element with a data-win-control attribute with value of __Telerik.UI.RadCalendar__.
						

	
							<div id="myCalendar" data-win-control="Telerik.UI.RadCalendar">
							</div>
						



You can achieve the same result in JavaScript - just define the host div element on the page and then instantiate a new __RadCalendar__
							by passing a reference to the div DOM object in the control constructor:
						

	
							var calendar = new Telerik.UI.RadCalendar(document.getElementById("myCalendar"));
						



By defining __RadCalendar__ without any properties set, a default version of the control will be initialized. The user can 
              select any date from January 1st 1900 to December 31st 2099 and today's date will be shown in the calendar's footer. Here is an image of the basic 
              calendar setup.
            ![calendar-gettingstarted](../Media/Controls\Calendar\calendar-gettingstarted.png)

# optionsSetting RadCalendar Options

Same as with the rest of the Windows Runtime JavaScript controls, __RadCalendar__'s properties can be set through the data-win-options attribute of
							the host element:
						

	
							<div id="myCalendar" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
							start: 'year'
							}">
							</div>
						



In JavaScript, you can pass an options object as a second argument to the RadCalendar constructor:

	
							var calendar = new Telerik.UI.RadCalendar(document.getElementById("myCalendar"), {
							start: "year"
							});
						



# referencing
						Referencing the RadCalendar Control Instance
					

As described in
							[this MSDN article about adding controls to a Windows Store app](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493.aspx), any control in a Windows Runtime JavaScript application requires a call to
							__WinJS.UI.processAll()__ for proper initialization. The same holds true for any of the Telerik UI controls. Once,
							the WinJS framework has initialized all the controls on the page, the __RadCalendar__ control instance associated with a host HTML element can be
							retrieved using the winControl expando property of the host HTML element.
						

	Define your RadCalendar control in the HTML



	
							WinJS.Utilities.ready(function () {
							WinJS.UI.processAll().then(function () {
							//wait for the processAll() method to finish, then find the
							//calendar control from the host element's winControl property
							var calendarElement = document.getElementById("myCalendar");
							var myCalendarControl = calendarElement.winControl;
							console.log(myCalendarControl instanceof Telerik.UI.RadCalendar); //true
							});
							});
						



# propertiesModifying RadCalendar Properties

Once __RadCalendar__ is loaded and the control is referenced in JavaScript, it exposes an extensive set of properties, methods and events.

						

	
							args.setPromise(WinJS.UI.processAll().then(function () {
							var calendar = document.getElementById("myCalendar").winControl;
							calendar.start = "year";
							}));
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var calendar = new Telerik.UI.RadCalendar(document.getElementById("myCalendar"), {
							onnavigate: navigateHandlerFnName
							});
							// OR
							var calendar = new Telerik.UI.RadCalendar(document.getElementById("myCalendar"), {
							onnavigate: function(e) {//...}
							});
						

>
								Note that if you attach the event handler as shown above, but in HTML mark-up, you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							calendar.addEventListener("navigate", navigateHandlerFnName);
						



# selectingSelecting a date in code

A date can be selected in __RadCalendar__ by a user action (tap on the date cell) or in code. To select a date in code, assign its value property a
							__Date__ object:
						

	
							calendar.value = new Date(2013, 7, 22);
						



# getting-selectionGetting the selected date

To get the currently selected date in __RadCalendar__, again use the value property:

	
							var selectedDate = calendar.value;
						



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Day Template]({{slug:day-template}})

 * [Keyboard Support]({{slug:keyboard-support}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Events]({{slug:events}})

 * [Navigate RadCalendar in Code]({{slug:navigate-radcalendar-in-code}})
