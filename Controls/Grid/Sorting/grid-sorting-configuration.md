---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


RadGrid supports both single-column and multi-column sorting. On top of that, you can choose whether the sort modes will include switching back to unsorted
				mode. This is controlled by a single property - __sortable__ which is explained below. Furthermore, you can pre-define sort expressions
				that will be applied to the grid on inital load.
			

# Sort Modes

The __sortable__ property will recognize the values listed in the table below, representing different sort modes:
				

Value

Meaning

__none__

Sorting is disabled. This is the default value.

__single__

Single column sorting—the grid records can be ordered in ascending or descending order based only on a single column. This is done by
								clicking/tapping its header. On clicking/tapping another column's header, sorting in the first column is cleared and the new one is applied.
							

__multiple__

Multi-column sorting—the grid records can be ordered in ascending or descending order based on one or more fields. This is done
								by clicking/tapping one column header until the desired order is achieved and then clicking/tapping another one to do even more specific
								sorting—usually when there can be multiple records with identical values for their fields.
							

__single, allowUnsort__

Same as single, with the difference that you can also unsort the sorted column by clicking/tapping its header.

__multiple, allowUnsort__

Same as multiple, but you can also unsort columns.>
						You can set the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">sortable</legacyBold> property to a Boolean value. When set to true, the mode used will be
						"single, allowUnsort".
					


 __js__
    


					var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						sortable: "multiple, allowUnsort",
						dataSource: {
							data: [
								{ Product: "Southwestern Twisted Chips", Price: 6.99 },
								{ Product: "Top Shelf Combo Appetizer", Price: 9.49 },
								{ Product: "Blue Cheese and Hazelnut Shortbread", Price: 10.69 },
								{ Product: "Avocado Feta Salsa", Price: 6.99 },
								{ Product: "Red Cherry Boost", Price: 6.99 },
							],
							schema: {
								model: {
									fields: {
										Product: { type: "string" },
										Price: { type: "number" }
									}
								}
							}
						},
						columns: [
							{ field: "Product" },
							{ field: "Price", format: "{0:C}" }
						]
					});



The following image displays the above-defined grid sorted first by price ascending and then by product descending.![grid-sorting](../Media/Controls\Grid\grid-sorting.png)>
						If you have not specified the data type of the data source fields, they are all considered as strings, meaning that they will be
						sorted alphabetically by default. If you have numeric or date fields, make sure you specify a model for your data. An example is available in this article:
						<link xlink:href="fb1a1e88-99a3-4a08-9206-18f241fd3f72" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" /> (see the <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Using different data types</legacyItalic> section).
					>
						If you want to disallow sorting for certain columns, make sure you set <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">sortable</legacyBold> to <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">false</legacyItalic> in
						these columns' options object. For an example see the <link xlink:href="fbb96399-dfbe-4826-ac0f-c5d6e698f244" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Columns</link> article.
					

# Performing Server Sorting

If you are binding RadChart to data that is coming from a remote endpoint that supports such data operations, you can push sorting to the
					server. This is done via the dataSource itself and setting the __serverSorting__ option on the data source to true. When you
					delegate sorting to the server,	you need to be prepared to receive the default parameter, which is orderBy. This field will contain the field name
					of the column to sort by in the dataset.
				

# Related Topics
