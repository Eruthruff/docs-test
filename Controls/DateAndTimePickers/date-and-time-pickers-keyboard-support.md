---
title: Keyboard Support
meta_title: Keyboard Support
meta_description: description.
slug: 
tags:keyboard,support
publish:True
---


RadDatePicker and RadTimePicker offer keyboard support for navigating the selector, and for numeric input that facilitates selection of dates and time. 
				Below you can find a description of the available options for these two features.
			

# Section1Keyboard Navigation

Below you can find a list of the recognized keys by the built-in keyboard support logic of the picker controls:

* 

Focus the inline part (picker): __TAB__ key (when the picker is next in the tab order).
						

* 

Open the Selector Popup part: __Enter__ key.
						

* 

Move through the three looping lists: __Left/Right Arrow__ keys or __TAB__ key.
						

* 

Go up or down (increase or decrease value) within the currently expanded list: __Up/Down Arrow__ key.
						

* 

Commit the selection: __Enter__ key.
						

* 

Cancel the selection: __Cancel__ key.
						

# Numeric Input

To make it easier to navigate to a given date or time, especially if it is not close to the currently selected one, RadDatePicker and RadTimePicker 
					offer the possibility to input digits when one of the looping lists is focused. You can type in the number representing a day, year, hour, etc. and 
					the list will navigate to it.
				

If the last chosen digit invalidates your input (so it does not correspond to a valid day, month, hour, etc.), the selection is changed to the closest
					valid number. For example, if you have focused the looping list for on a month and you input 16, the list selection will be navigated to 12. 
					However, if	you input 0, navigation will go to 1.
				

# Related Topics
