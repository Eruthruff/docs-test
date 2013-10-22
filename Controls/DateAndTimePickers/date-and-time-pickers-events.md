---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of RadDatePicker and RadTimePicker
				and their most notable event arguments.
			

Both RadDatePicker and RadTimePicker have the same set of events with
				identical event arguments.
			

# Section1Events

Event Name

Description

Arguments

__change__

Fires when the date/time is changed via the selector.
							

__e.target__: The RadDatePicker/RadTimePicker control whose selection has changed. The new value can 
								be accessed through __e.target.value__.
							

__close__

Fires after the selector popup closes.
							

__e.target__: The RadDatePicker/RadTimePicker control which has been closed.

							

__open__

Fires after the selector popup opens.
							

__e.target__: The RadDatePicker/RadTimePicker control which has been opened.
							

Below you can see a sample where the __change__ event is handled to access the new picker value:


 __html__
    


				<div id="myPicker" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
							onchange: Sample.Helpers.change
						}">
				</div>
				<br />
				<p id="dateInfo" style="color: #336699"></p>




 __js__
    


	WinJS.Namespace.define("Sample.Helpers", {
		change: WinJS.Utilities.markSupportedForProcessing(function (e) {
			document.getElementById("dateInfo").innerText = "Selected date: " + e.target.value;
		})
	});



# Related Topics
