---
title: Enabling RadControls IntelliSense
meta_title: Enabling RadControls IntelliSense
meta_description: description.
slug: 
tags:enabling,radcontrols,intellisense
publish:True
---


When you access a control using the __winControl__ property on a control wrapper element, Intellisense is unable to determine the type
				of the control and cannot display a list of its properties and methods. To be able to use IntelliSense with RadControls, from Q2 2013 on, there are two new helper
				method collections exposed by the __Telerik.UI__ namespace—__find__ that is a group of methods that find a control of
				a given type, instantiated on an element matching a supplied selector; and __to__ that is also a group of methods that return the
				passed object, cast to their corresponding type. The following sections clarify the usage of the two groups of methods.
			

# Section1Using Telerik.UI.find.[ControlName] methods

This is a collection of methods for accessing the different control types directly. For example, if you want to access a RadChart control, you should use 
					the __Telerik.UI.find.__ method. To access RadSlideHubTile, you would only need to 
					replace *Chart* with *SlideHubTile*.
				

These helper methods are especially useful in single page navigation (Navigation template). There, while you are in the __ready__ event
					handler, you should only access elements inside the *element* argument (passed to the __ready__ method).
					In this scenario, it is very easy to get a reference to a RadControl with working IntelliSense, using a single line of code:
				

	
					ready: function (element, options) {
					var chart = Telerik.UI.find.Chart("#chart1", element);
					chart.redraw();
					}
				



# Using Telerik.UI.to.[ControlName] methods

Similar to the above, __Telerik.UI.to__ is a group of methods, one per each control class in the suite. They are used to "cast" a 
					control, accessed through the __winControl__ expando property, to the proper type, so that you can use IntelliSense with it. For 
					example, consider you have the following definition in HTML:
				

	
					<div id="calendar" data-win-control="Telerik.UI.RadCalendar"></div>
				



Now, you want to apply some changes to RadCalendar. To access it and be able to use IntelliSense, you can use the following code:

	
					var calendar = document.querySelector("#calendar").winControl;
					calendar = Telerik.UI.to.Calendar(calendar);
				



If the control was a RadRangeSlider, for example, you would only need to replace *Calendar* with *RangeSlider* in
					the JavaScript logic.
				

# Related Topics
