---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


RadGrid supports automatic filtering of the displayed records. You can choose between applying filter expressions manually or letting the user provide
				filter criteria. Below you will find both scenarios explained.
			

# Enabling Filtering for RadGrid

To allow filtering in RadGrid, set its __filterable__ property to *true*. This will
					show a filter button in the column header. When the user clicks/taps the button, a pop-up filter item will appear for each data column. This item
					consists of:
				

* 

__Filter options list__: A pop up containing the relevant filter functions to the current data type. If you do not provide
							a model for your data, you will get the options for the string data type. If
							[in the model you specify a different data type](fb1a1e88-99a3-4a08-9206-18f241fd3f72) for a given field,
							the filter menu shown for its corresponding column will contain a different set of functions. For example, "Is greater than" for numbers and
							"Is before" for dates.
						

The table below this list, describes the filter functions supported by the different data types:

* 

__Filter value control__: This will be a normal text input for string fields, a RadNumericBox for numeric fields and
							RadDatePicker for date fields. These are used to provide a values to filter by.
						

* 

__Filter icon__: Clicking/tapping this icon triggers filtering in RadGrid in case a filter value is provided. If a
							filter value is not provided, the filter item is closed and the grid remains unchanged.
						

* 

__Expand/collapse button__: When this button is clicked/tapped, a set of controls for adding a second
							filter expression is displayed, plus a two-item list that allows the user to pick a group function (AND, OR). The function will be used when grouping
							the two filter expressions.
						

* 

__Clear button__: Used to clear the filter criteria for the column to which the filter item belongs.
						

string

number

date

Is equal to

Is equal to

Is equal to

Is not equal to

Is not equal to

Is not equal to

Starts with

Is greater than or equal to

Is after or equal to

Contains

Is greater than

Is after

Does not contain

Is less than or equal to

Is before or equal to

Ends with

Is less than

Is before

This image shows the appearance of the filter item in RadGrid:![grid-filtering](../Media/Controls\Grid\grid-filtering.png)

When a column is filtered, its appearance (background and header) is changed to notify the user that it is a filtered column. This is shown in the image
					below:
				![grid-filtering_1](../Media/Controls\Grid\grid-filtering_1.png)>
						To disallow filering for a certain column, make sure you set <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">filterable.enabled</legacyBold> to <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">false</legacyItalic> in its 
						options object. For an example, see the <link xlink:href="fbb96399-dfbe-4826-ac0f-c5d6e698f244" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Columns</link> article.
					

The following code sample shows a grid with enabled filtering, where:

* 

Filtering is enabled for the grid and disabled for its first column.

* 

A model is defined to specify the types of fields.


 __js__
    


					var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						filterable: true,
						dataSource: {
							data: [
								{ Product: "Southwestern Twisted Chips", Price: 6.99, AvailableSince: new Date(2012, 7, 4) },
								{ Product: "Top Shelf Combo Appetizer", Price: 9.49, AvailableSince: new Date(2012, 3, 14) },
								{ Product: "Blue Cheese and Hazelnut Shortbread", Price: 10.69, AvailableSince: new Date(2012, 5, 21) },
								{ Product: "Avocado Feta Salsa", Price: 6.99, AvailableSince: new Date(2012, 3, 14) },
								{ Product: "Red Cherry Boost", Price: 6.99, AvailableSince: new Date(2012, 2, 28) },
							],
							schema: {
								model: {
									fields: {
										Product: { type: "string" },
										Price: { type: "number" },
										AvailableSince: { type: "date" }
									}
								}
							}
						},
						columns: [
							{ field: "Product", filterable: false },
							{ field: "Price", format: "{0:C}" },
							{ field: "AvailableSince", title: "Available Since", format: "{0:MM/dd/yyyy}" }
						]
					});



# Related Topics
