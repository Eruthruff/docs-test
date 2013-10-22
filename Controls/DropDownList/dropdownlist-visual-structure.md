---
title: Visual Structure
meta_title: Visual Structure
meta_description: description.
slug: 
tags:visual,structure
publish:True
---


This article explains the visual elements of the RadDropDownList control.

# Visual Structure![Visual structure](../Media/Controls\DropDownList\dropdownlist-visual-structure.png)

# Description of Elements

Name

Description

Toggle Area

As opposed to RadAutoCompleteBox and RadComboBox, where a textbox allows filtering the list items, RadDropDownList's
								text area is readonly (it always contains the text of the currently selected list item). It can be clicked/tapped, similarly to the
								toggle button at the right - to toggle the dropdown list.
							

Dropdown List

Could also be referred to as *"popup"* or *"dropdown"*. All items
								are contained in this list which appears upon clicking/tapping anywhere in the toggle area.
							

List Item

Could also be referred to as *"item"*, *"option", etc.*. Represents a single data
								item from the control's datasource. The value visible in the item comes from the field in the datasource, assigned as a
								__dataTextField__. If such a field is not assigned, the text value is the string representation of the object to which
								the item is bound.
							

# Related Topics
