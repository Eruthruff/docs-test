---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of RadSlider and RadRangeSlider and their most notable event arguments.
		  

# Section1Events

Event Name

Description

Arguments

__change__

Fires when the value of the slider is changed.
						  

__e.target__: The RadSlider/RadRangeSlider control which value has changed. 
						  

__e.value__: The new value. For *RadSlider* this is a single numeric value, 
							  while for *RadRangeSlider* the returned value is an array of two numeric values representing the 
							  two ends of the newly selected range.
						  

__slide__

Fires when the user drags the drag handle to a new position.
						  

__e.target__: The RadSlider/RadRangeSlider control instance.
						  

__e.value__: For *RadSlider* this is a single numeric value representing
							  the point that the user has just moved the slider to,
							  while for *RadRangeSlider* the returned value is an array of two numbers representing the
							  two ends of the newly selected range.
						  

Below you can see a sample where the __change__ event is handled to access the new RadRangeSlider range.


 __html__
    


				<div id="slider1" style="width: 300px" data-win-control="Telerik.UI.RadRangeSlider" data-win-options="{
					onchange: Slider.Helpers.change
				}">
				</div>
				<p id="sliderInfo" style="color: #33ccff"></p>




 __js__
    


	WinJS.Namespace.define("Slider.Helpers", {
		change: WinJS.Utilities.markSupportedForProcessing(function (e) {
			document.getElementById("sliderInfo").innerText = "Slider range was changed to: " + e.value[0] + "-" + e.value[1] + ".";
		})
	});



# Related Topics
