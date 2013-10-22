---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article will introduce you to the options for setting and customizing RadSlider and RadRangeSlider controls:

* 

[Common settings](#common)

* 

[RadSlider settings](#slider)

* 

[RadRangeSlider settings](#range-slider)

# commonCommon Configuration

# Basic Slider Settings

The following properties give you control over the slider allowed value range and steps between the min and max value:

* 

__min__: Represents the minimum value of the slider.
								

* 

__max__: Represents the maximum value of the slider.
								

* 

__largeStep__: The value by which the main division of the slider will be made. In case of keyboard
									navigation, this would be the step by which the slider value will change on pressing the PageUp/Down buttons on a focused
									slider.
								

* 

__smallStep__: The delta with which the value changes when the user drags the slider handle.
								


 __js__
    


					var slider1Ctrl = new Telerik.UI.RadSlider(document.getElementById("slider1"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						value: 25
					});

![Basic settings (RadSlider)](../Media/Controls\Slider\slider-basic-settings.png)


 __js__
    


					var rangeSlider1Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("rangeSlider1"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						selectionStart: 25,
						selectionEnd: 40
					});

![Basic settings (RadRangeSlider)](../Media/Controls\Slider\slider-range-basic-settings.png)

# Changing the Slider Orientation

You can make the slider render vertically by changing its __orientation__ property to __'vertical'__ , default
							is __'horizontal'__.
						


 __js__
    


					var rangeSlider2Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("rangeSlider2"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						orientation: "vertical"
					});

![Slider Orientation](../Media/Controls\Slider\slider-range-orientation.png)

# Modifying the Tooltip

By default, the slider controls show a tooltip displaying the current value, while dragging the handle. To format, hide or
							customize the tooltip, use the __tooltip__ options of the control. They expose three properties:
						

* 

__enabled__: A boolean value indicating whether the tooltip will be shown to the user.
								

* 

__format__: The format of the slider tooltip. If a tooltip template is set, the value of
									this property will be ignored and the template will be used instead.
								>
										The applied format will also influence the appearance of the slider tick labels.
									

* 

__template__: Used to set the template string that will be used for the content of the
									slider tooltip. The template can contain text, HTML and binding expressions.
								

The binding context of __RadSlider__ contains a variable, __value__, which holds the current
									value of the slider.
								

There are two values in RadRangeSlider's tooltip template binding context—__selectionStart__ and
									__selectionEnd__.
								

A non-empty value for the __template__ property overrides the tooltip format.
								


 __js__
    


					var slider3Ctrl = new Telerik.UI.RadSlider(document.getElementById("slider3"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						tooltip: {
							template: "Set #=value#"
						}
					});

![Customizing the RadSlider tooltip](../Media/Controls\Slider\slider-tooltip.png)


 __js__
    


					var rangeSlider3Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("rangeSlider3"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						tooltip: {
							template: "Set range: #=selectionStart# to #=selectionEnd#"
						}
					});

![Customizing the RadRangeSlider tooltip](../Media/Controls\Slider\slider-range-tooltip.png)

More information on customizing the slider tooltip can be found [
										here](0103d186-5238-4627-8cd5-723dc7b01c3f).
								

# Setting the Slider Ticks

Using the __tickPlacement__ property, you can change the location of the tick marks in the slider.
							The available options are *"minorOutside"*, *"minorMajorOutside"*,
							*"inside"* and *"none"*. The default value is *"minorMajorOutside"*.
						
					


 __js__
    


					var slider4Ctrlder = new Telerik.UI.RadSlider(document.getElementById("slider4"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						tickPlacement: "minorOutside"
					});

![Tick placement](../Media/Controls\Slider\slider-tick-placement.png)

# Disabling the Control

If you want to temporarily (until some condition is fulfilled) disable the slider, set its __enabled__
							property to false. In such cases, no user interaction with the control will be possible.
						


 __js__
    


					var slider5Ctrlder = new Telerik.UI.RadSlider(document.getElementById("slider5"), {
						min: 0,
						max: 50,
						smallStep: 5,
						value: 20,
						enabled: false
					});



# sliderRadSlider Settings

This section will introduce you to the options specific to the RadSlider control only.

# Setting the Increase/Decrease Buttons of RadSlider

You can display buttons for increasing and decreasing the value selected in RadSlider. To do so, change the value of the
							__showButtons__ property to __true__ (it is false by default). This will display an
							increase and decrease buttons above and below the slider respectively.
						

To display tooltips for these buttons, you can assign text for them to the __increaseButtonTooltip__
							and __decreaseButtonTooltip__ properties of the control.
						


 __js__
    


					var slider6Ctrl = new Telerik.UI.RadSlider(document.getElementById("slider6"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						orientation: "vertical",
						showButtons: true,
						decreaseButtonTooltip: "Decrease",
						increaseButtonTooltip: "Increase"
					});

![Increase/decrease buttons](../Media/Controls\Slider\slider-buttons.png)

# Getting/Setting Value of RadSlider

You can get the current value of the RadSlider or assign a new value manually through the __value__
							option. It is a single numeric value, as opposed to the array of values used by RadRangeSlider.
						


 __js__
    


					var slider7Ctrl = new Telerik.UI.RadSlider(document.getElementById("slider7"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						value: 20
					});



# range-sliderRadRangeSlider Settings

Below follows description of the specifics of the RadRangeSlider control.

# Manually Selecting a Range of RadRangeSlider

If you want to preselect a range in RadRangeSlider, you can set the __selectionStart__ and
							__selectionEnd__ properties to numeric values belonging to the interval defined by the slider's min
							and max values.
						

You can also use these properties to access the ends of the currently selected range.


 __js__
    


					var rangeSlider6Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("rangeSlider6"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						selectionStart: 10,
						selectionEnd: 30
					});



# Getting/Setting Values of RadRangeSlider

You can get the currently selected range of values of the RadRangeSlider or assign a new one manually through the __values__
							option. __values__ is an array of two numeric values - the start and end values of the currently selected range.
						


 __js__
    


					var rangeSlider7Ctrl = new Telerik.UI.RadRangeSlider(document.getElementById("rangeSlider7"), {
						min: 0,
						max: 100,
						smallStep: 5,
						largeStep: 10,
						selectionStart: 10,
						selectionEnd: 30,
						onchange: function (e) {
							var range = e.target.values;
							var minVal = range[0];
							var maxVal = range[1];
							document.getElementById("sliderSelection").innerText = "Selected range from " + minVal + " to " + maxVal + ".";
						}
					});



# Related Topics
