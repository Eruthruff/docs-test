---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadCalendar, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the selected date is changed.
							

__e.target__ - the RadCalendar control that triggered the event.
							

__navigate__

Fires when the control navigates.
							

__e.target__ - the RadCalendar control that triggered the event.
							

Here follows an example of using the __change__ event to access the selected date:
				


 __html__
    


				<div id="calendar1" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
					onchange: Events.change
				}">
				</div>
				<p id="info" style="color: #ff6a00"></p>




 __js__
    


	WinJS.Namespace.define("Events", {
		change: WinJS.Utilities.markSupportedForProcessing(function (e) {
			var calendar = e.target;
			info.innerText = "Selected date is: " + calendar.value.toDateString();	
		})
	});



# Related Topics
