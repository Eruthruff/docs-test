---
title: Tooltip
meta_title: Tooltip
meta_description: description.
slug: 
tags:tooltip
publish:True
---


Both RadSlider and RadRangeSlider display a tooltip with the current value of the control while moving the slider. The number shown in
      the tooltip can be formatted and even templated. This article describes how this can be achieved and what specifics to have in mind.

# Configuration

The tooltip is visible by default. You can disable it by setting the __enabled__ property of the tooltip object 
        to __false__.
		

	
					<div data-win-control="Telerik.UI.RadSlider" data-win-options="{
						tooltip: {
							enabled: false
						}
					}">
					</div>
				



	
					var slider = new Telerik.UI.RadSlider(document.getElementById('slider'), { tooltip: {enabled: false} });
				



To change this after initialization of the control, use the following code:

	
					var control = document.getElementById("slider").winControl;
					control.tooltip.enabled = false;
				



# Formatting Values

The value of the slider tooltip can be formatted using the __format__ property.


 __js__
    


					var slider1Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("slider1"), {
						min: 0,
						max: 2,
						smallStep: 0.1,
						largeStep: 0.5,
						tooltip: {
							format: "{0:N1}"
						}
					});



The format string supports a subset of the syntax available in Java and C#. 
					Here "N1" indicates that the value should show one digit after the decimal separator.
				>If a tooltip template is set, the value of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">format</legacyBold> property will be ignored and the template will be used instead. 

# Templates

You could also provide a template for the content of the tooltip. You could assign the template a string value containing HTML and binding expressions. 
				The template provides access to the value.


 __js__
    


					var slider2Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("slider2"), {
						min: 0,
						max: 2,
						smallStep: 0.1,
						largeStep: 0.5,
						tooltip: {
							template: '&lt;span &gt;${value}&lt;/span&gt;'
						}
					});



Tooltip content can also be defined with a the following syntax:
				


 __js__
    


					var slider3Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("slider3"), {
						min: 0,
						max: 2,
						smallStep: 0.1,
						largeStep: 0.5,
						tooltip: {
							template: '&lt;span &gt;#=value#&lt;/span&gt;'
						}
					});



The binding context of the two slider controls exposes the following information:

* 

*__RadSlider:__*

* 

__value__: The current value of the slider.
								

* 

*__RadSlider:__*

* 

__selectionStart__: The start value of the current range selection.
								

* 

__selectionEnd__: The end value of the current range selection.
								

# Related Topics
