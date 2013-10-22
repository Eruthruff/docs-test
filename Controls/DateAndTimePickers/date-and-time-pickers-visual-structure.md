---
title: Visual Structure
meta_title: Visual Structure
meta_description: description.
slug: 
tags:visual,structure
publish:True
---


This article explains the visual elements of the RadDatePicker and RadTimePicker controls.

# Visual Structure![datepicker-visual-structure](../Media/Controls\DatePicker\datepicker-visual-structure.png)

# Description of Elements

Name

Description

[Header](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

The text that appears above the picker element when the __header__ property is set. It can be used to provide
								additional information about the purpose of the picker control instance.
							

[Picker](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

The element displayed by the RadDatePicker/RadTimePicker control when not focused. It consists of a text area containing the selected date,
								empty string or placeholder text, and a button that can also be used to trigger the selector.
							

[Selector](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

This is the element that appears upon focusing the RadDatePicker/RadTimePicker, which allows you to select a day, month and year (or hour,
								minute, period) and then confirm or cancel your selection.
							

[Selector Header](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

This is the text that appears at the top of the selector.
							

[Looping Lists](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

There is one looping list for each date/time fraction that needs to be selected. The list can be looped infinitely and contains the allowed
								values for the given part of the date or time. Selection is done by clicking/tapping the  chosen value or moving it to the center of the
								list (which is highlighted in blue).
							

[Selector Items](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

These are the elements used to build the looping lists. Each item represents a value (day, year, hour, period etc.).
							

[Buttons](4d0c0a79-502c-4b6d-95e6-d49d11b90875)

Positioned at the bottom of the selector, they are used to confirm (tick button) or cancel (cross button) the selection, made through the
								looping list. Upon clicking either button, the selector is closed. The difference is that in case of clicking the tick the selected value will
								be shown in the picker, while clicking the cross will lead to no change.
							

# Related Topics
