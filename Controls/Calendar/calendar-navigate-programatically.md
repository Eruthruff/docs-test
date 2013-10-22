---
title: Navigate RadCalendar in Code
meta_title: Navigate RadCalendar in Code
meta_description: description.
slug: 
tags:navigate,radcalendar,in,code
publish:True
---


RadCalendar exposes API for any kind of navigation among its views. Thanks to it, you can programmatically navigate between months, years, different views, etc.
			

# Navigate RadCalendar in code

The public navigation methods exposed by RadCalendar are:

Method

Description

__navigate(value, view)__

Accepts a __Date__ object as first argument and a string, representing one of the calendar views. Navigates to the
								view that contains the date.
							

__navigateDown(value)__

Accepts a single __Date__ argument. Navigates down one view and then to the provided date.
							

__navigateToFuture()__

Navigates to the next month in month view, year in year view, etc.

__navigateToPast()__

Navigates to the previous month in month view, year in year view, etc.

__navigateUp()__

Navigates up one view.

Following is an example, where RadCalendar is programatically navigated using external buttons.


 __xml__
    


				<div id="calendar1" data-win-control="Telerik.UI.RadCalendar"></div>
				<div id="picker" data-win-control="Telerik.UI.RadDatePicker"></div>
				<button id="navigateBtn">navigate(value, view)</button>
				<button id="navigateDownBtn" disabled="disabled">navigateDown(value)</button>
				<button id="navigateToFutureBtn">navigateToFuture()</button>
				<button id="navigateToPastBtn">navigateToPast()</button>
				<button id="navigateUpBtn">navigateUp()</button>



Each button from the above mark-up has its __click__ event attached and when it is fired, the respective navigation is called upon
					RadCalendar:
				


 __js__
    


					navigateBtn.addEventListener("click", function () {
						calendar1.winControl.navigate(picker.winControl.value, "month");
					});




 __js__
    


					navigateDownBtn.addEventListener("click", function () {
						calendar1.winControl.navigateDown(picker.winControl.value);
						if (calendar1.winControl.view.name == "month") {
							navigateDownBtn.disabled = true;
						}
						navigateUpBtn.disabled = false;
					});




 __js__
    


					navigateToFutureBtn.addEventListener("click", function () {
						calendar1.winControl.navigateToFuture();
					});




 __js__
    


					navigateToPastBtn.addEventListener("click", function () {
						calendar1.winControl.navigateToPast();
					});




 __js__
    


					navigateUpBtn.addEventListener("click", function () {
						calendar1.winControl.navigateUp(new Date(2001, 0, 1));
						if (calendar1.winControl.view.name == "century") {
							navigateUpBtn.disabled = true;
						}
						navigateDownBtn.disabled = false;
					});



With this set up, you can select a date from the RadDatePicker and then navigate RadCalendar to it using the "navigate()" or "navigateDown(value)" button.
					You can also use the other three buttons to switch between views and time periods.
				

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Calendar/NavigateProgrammaticaly*.
        

# Related Topics
