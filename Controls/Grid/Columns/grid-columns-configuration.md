---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


To provide you with more flexibility and cut down on the amount of code needed for setting columns in simple scenarios, RadGrid supports both
				declaratively defined and auto-generated columns.
			

# Auto-generated Columns

Auto-generated columns are, by default, created if you do not assign an array of options to the __columns__ property of the control.
					In such cases, each field from the provided data source is presented by a column in the grid. Note that when columns are automatically generated,
					all fields are processed as they are of string type.
				

Auto-generated columns work both with local and remote binding and this makes them an easy way to visualize simple sets of data or
					ones that are already processed for display to the user (user-friendly string representation of any dates and numbers).
				

A simple example of a grid declaration that will produce three columns is shown below:


 __html__
    


				<div data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{ Name: 'Peter', Age: 23, Points: 22.6 },
									{ Name: 'Mary', Age: 30, Points: 24 },
									{ Name: 'Mark', Age: 27, Points: 28.8 }
								]
							}
						}">
				</div>



# Defining Columns in the RadGrid Constructor

If you want to display only a subset of the data that you have retrieved in your app, you can list the columns in the grid, along with any additional
					customizations you need for them.
				

When you define a column, if it is intended to display data, the first and most important property to set for it is __field__.
					It should point to the name of the field in the control’s data source which you want the column to visualize.
				


 __html__
    


				<div data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{ Name: 'Peter', Age: 23, Points: 22.6 },
									{ Name: 'Mary', Age: 30, Points: 24 },
									{ Name: 'Mark', Age: 27, Points: 28.8 }
								]
							},
							columns: [
								{field: 'Name', title: 'Participant'},
								{field: 'Age'},
								{field: 'Points', title: 'Score'}
							]
						}">
				</div>



The rest of the available settings for grid columns are described below:

# Setting Header Text/Title

To provide a title for a column that will appear in its header cell, assign a string value to the __title__ option.
						

# Enable/Disable Encoding

You can specify whether column content should be HTML encoded using the __encoded__ property, which accepts
							*true* or *false* as a value. Disable encoding in the columns if the data contains HTML markup.
						

# 
						Formatting Cell Values
					

To apply formatting on column cells, use the __format__ property.
						


 __html__
    


				<div data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{ Name: 'Peter', Age: 23, Points: 22.6 },
									{ Name: 'Mary', Age: 30, Points: 24 },
									{ Name: 'Mark', Age: 27, Points: 28.8 }
								]
							},
							columns: [
								{ field: 'Name', title: 'Participant'},
								{ field: 'Age'},
								{ field: 'Points', title: 'Score', format: '{0:N2}'}
							]
						}">
				</div>



You can find all formatting options listed in this article: [](0c3b0ea5-3850-4c90-86b3-5d20f2a18c1e).
						

# Setting Attributes to Column Cells

To set an attribute (class, style, etc.) to a cell in RadGrid, you can use the __attributes__ property for data cells, 
							the __headerAttributes__ property for header cells, and the __footerAttributes__ for footer cells. 
							They accept as a value an object, where you can list as keys the attribute names and as values - the attribute values. Note that if you are 
							assigning an attribute, which is a reserved word in JavaScript, you should
							enclose this key in quotation marks.
						

For a sample usage of the __attributes__ property, check the
							[Conditional formatting](771b6aef-d78b-45f2-a3c8-fba9d08c1915) article.
						

# Disabling Sorting and Filtering for Certain Columns

By default, when you enable sorting and/or filtering for the RadGrid control, all data columns are respectively sortable and/or filterable. If you want
							to prevent a column from sorting and filtering the grid, set its __sortable__ and __filterable__ properties to
							*false*.
						


 __html__
    


				<div data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{ Name: 'Peter', Age: 23, Points: 22.6 },
									{ Name: 'Mary', Age: 30, Points: 24 },
									{ Name: 'Mark', Age: 27, Points: 28.8 }
								],
								schema: {
									model: {
										fields: {
											Name: {type: 'string'},
											Age: {type:'number'},
											Points: {type: 'number'}
										}
									}
								}
							},
							columns: [
								{ field: 'Name', title: 'Participant'},
								{ field: 'Age', sortable: false},
								{ field: 'Points', title: 'Score', filterable: false}
							],
							sortable: 'single',
							filterable: true
						}">
				</div>



Using the __filterable__ property, you can also define a filter template for the column. You can learn how here: 
						[](81095a71-8bfd-43ed-aed5-d377ab3d8775).
					

# Defining Aggregates

When showing group aggregates in RadGrid, you need to define for each column what aggregate functions you are going to use. This is done
							via the __aggregates__ property, which accepts a string array as its value. For more details, check out the
							[Grouping article](65508059-6b67-4c50-b60a-e365fae67884).
						

# Hide Columns

If you need to not show a column initially, you can set its __hidden__
							property to *true*. Later, upon some user action, you can use the __showColumn()__
							and __hideColumn()__ to control visibility of columns. For more info, check this help article:
							[](fbb96399-dfbe-4826-ac0f-c5d6e698f244).
						

# Setting column width

To specify a fixed width for a column, set its __width__ property to a numeric value. The numeric value will be assigned as
							pixel width to the grid column.
						

# Limiting the Possible Column Values for Editing and Filtering

If the defined column represents data that can be limited to a subset of possible entries, you can list these values through the
							__values__ property of the column. This way, in filtering and editing operations, instead of a textbox, the edit/filter element
							will display a RadDropDownList with a limited set of entries.
						


 __html__
    


				<div id="grid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: Sample.ds,
							columns: [
								{ field: 'Name', title: 'Participant', width: 140},
								{ field: 'Points', title: 'Score', width: 100},
								{ field: 'Sport', values: ['Running', 'Swimming', 'Tennis', 'Cycling'], width: 200}
							],
							editable: {
								enabled: true
							},
							filterable: true
						}">
				</div>

![grid-columns-values](../Media/Controls\Grid\grid-columns-values.png)

# Related Topics
