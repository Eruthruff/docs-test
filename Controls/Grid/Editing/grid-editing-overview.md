---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


From Q2 2013 RadGrid offers full editing capabilities. Thanks to its built-in DataSource, you can implement most editing scenarios by just adjusting
				the controls settings.
			

Editing can be performed in three modes - row editing, single cell editing and batch cell editing. All are handled automatically by the RadGrid
				and its DataSource.
			

By providing a __model__ for the fields in RadGrid, you can define which of them are editable and also which should be
				validated. Then RadGrid automatically performs validation and notifies the user about missing or invalid values.
			

This help article will introduce you to the prerequisites needed to enable editing in RadGrid and the control's behavior in create, update and delete scenarios.

# Prerequisites

To take advantage of the automatic editing capabilities of RadGrid, you need to first set its __dataSource__ properly. This includes
					setting its __create__, __update__ and __destroy__ options, and providing a proper model for
					your data. You can find more detailed instructions here: [](142aaf90-387f-4688-9e64-11e31edbdf75)

# Enabling RadGrid Editing

To enable basic editing in RadGrid, you need to set its __editable.enabled__ option to *true*.
					When you do so, the cell editing mode will be triggered. The following behaviors related to insert, update and delete will be observed:
				

# Insert

The service column will appear, displaying a plus icon. Upon clicking it, a new row will appear in RadGrid for insert. You can control where
							the insert item will appear, using the __editable.createAt__ property. It accepts *"top"* and
							*"bottom"* values. However, you should have in mind that the newly inserted record is added at the bottom of your defined
							data source, so after the insert is done, the row will appear at the bottom of the RadGrid control.
						

To submit the newly inserted item, the user needs to do the following, based on the edit mode:

* 

__mode: "cell"__: The user needs to double-tap a cell from another row to trigger a submit.
								

__mode: "cellBatch"__: The user needs to double-tap a cell from another row. Then, when all edits are done, tap the
									Save Changes button in the service column to submit the batch edit. Until this button is pressed, a Cancel action will delete the new row.
								

__mode: "row"__: The user needs to double-tap another row to trigger a submit.
								

# Update

On double-clicking a cell, it will become editable. On the left, there is a big X button, which will cancel any changes you apply
							to the cell content. If you decide to save the changes you have made, double click another cell.
						

If there is a properly defined model for the data, the edit control that is rendered in the cell will be determined by the
							data type of the underlying field. The possible scenarios are:
						

* 

__numeric fields__ use RadNumericBox.
								

* 

__date fields__ use RadDatePicker.
								

* 

__boolean fields__ use a checkbox.
								

* 

__string fields__ use a regular input.
								

If there are validation rules defined for a field, if the new valie does not fulfill them, a popup with validation message will
							appear and the cell will not exit edit mode, until its content is corrected.
						

Once a cell is edited, it is marked with a colored triangle at the top right corner. This way, the end-user can easily see which
							cells have been edited.
						

The behavior for this and other edit modes is described here: [](0e7ed261-b633-4538-9d68-ef58ddd4cdea).
						

# Delete

When you enable row editing in RadGrid (set __editable.mode__ to *"row"*) and the control enters
							edit mode, apart from the Cancel button, a Delete button appears. Its icon is a trash can and upon clicking it, a confirmation message will be
							displayed next to it. If the user taps the icon or the message, the record will be deleted.
						>
                Note that as of Q2 2013, when a cell or row is put in edit mode, selection is automatically disabled and all selected items are cleared. Once the 
                cell editor is closed selection is turned back on without restoring previously selected items.
              

# Related Topics

 * [Configuring Data Editing]({{slug:configuring-data-editing}})

 * [Editing Configuration]({{slug:editing-configuration}})

 * [Edit Modes]({{slug:edit-modes}})

 * [Validation]({{slug:validation}})

 * [Events]({{slug:events}})
