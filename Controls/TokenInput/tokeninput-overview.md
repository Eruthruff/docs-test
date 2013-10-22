---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---
![tokeninput-overview](../Media/Controls\TokenInput\tokeninput-overview.png)

The RadTokenInput control for Windows Runtime JavaScript applications is similar to the recipients field in Facebook in that it displays a list of values
				and allows the selection of multiple values from this list. It is designed to work in Windows Store applications using JavaScript. Below you 
        can see an example of how RadTokenInput can be used in a real application scenario.
			![tokeninput-overview-example](../Media/Controls\TokenInput\tokeninput-overview-example.png)

# Architecture

A token input control, in general, is used to display a predefined list of values and allow the user to select multiple values from it. When a value
					is selected, a visual element, called a token, is displayed in the input box. By default it contains only the text value of the selection. Usually, you can
					also define a template to make it display additional content , for example, an image.
				

# RadTokenInput

RadTokenInput implements the architecture described above. When its input box is focused, the control displays a list of values that can be selected
					by the user and autocompletes their input with the matching values. When a value is selected, it is displayed as a token. The token can contain plain text
					or a template.
				

RadTokenInput exposes many [configuration options](b7757db2-984a-43ba-8c74-efb8e613ed85) related to data binding, filtering,
					selection, and appearance.
				

Furthermore, it allows you to provide [item template](4c5db45e-de1f-401e-a79e-aceae48f54e5) and
					[tag template](17f87026-ae80-46e2-b792-8a35ccdfdf29) to customize its items and tags content.
				

# Related Topics
