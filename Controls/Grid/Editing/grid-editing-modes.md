---
title: Edit Modes
meta_title: Edit Modes
meta_description: description.
slug: 
tags:edit,modes
publish:True
---


RadGrid offers different behaviors when being edited - you can edit whole rows, numerous cells with a batch update or each cell separately. These
				behaviors are controlled by the __mode__ option in the __editable__ settings. This article describes
				RadGrid's behavior when the different edit modes are used.
			

# Section1Single cell editing

When __editable.mode__ is set to *cell*, you can edit cells in RadGrid, each separately.
					Following is a description of the order of actions when using this mode:
				![grid-editing-cell-mode](../Media/Controls\Grid\grid-editing-cell-mode.png)

* 

To enter edit mode, the end-user should double click/tap the target cell. Alternatively the end-user can create a new row with the "Create a 
            new row" button(B).

* 

The cell becomes editable and displays an edit control(A) and a cancel button(C), which will clear any changes that have been made
							during the current edit and will cause the cell to exit edit mode. In case the end-user has used the "Create a new row" button(B), the first 
              cell of the new row becomes editable.
						

* 

If the user wants to keep the change, they can double click/tap any other cell. Then the change will be committed and the cell
							will exit edit mode. The cell that was double-clicked/tapped will now enter edit mode.
						

* 

Once a change in a cell is confirmed, the data is updated in the DataSource. Since each change in it triggers a refresh in
							RadGrid, every successful edit in the control will cause it to refresh. Note that this may be an expensive operation, especially
							when the grid has a big output.
						>For the reasons described above, single cell editing is recommended only for simple scenarios with smaller data sets.

# Batch cell editing

With __editable.mode__ set to *cellBatch*, multiple cells can be edited before committing
					their changes. The difference in UI is that a "Save Changes"(E) and "Cancel Changes"(F) buttons are displayed in the service column. They are
					used to perform the batch changes in __RadGrid__. Here is a description of the order of actions with this mode enabled:
				![grid-editing-cell-batch-mode](../Media/Controls\Grid\grid-editing-cell-batch-mode.png)

* 

To enter edit mode, the end-user should double click/tap the target cell. Alternatively the end-user can create a new row with the "Create a
              new row" button(D).
            

* 

The cell becomes editable and displays an edit control(A) and a cancel button(B). The cancel button will clear any changes that have
              been made to the cell since the last global save of changes and will cause the cell to exit edit mode. In case the end-user has used the 
              "Create a new row" button(D), the first cell of the new row becomes editable.
            

* 

If the user wants to keep the change locally and edit a different cell, they can double click/tap any other cell. Then the change
							will be kept (without being pushed to the DataSource) and the cell will exit edit mode. The cell that was double-clicked/tapped
							will now enter edit mode. The edited cell will be marked as dirty (edited)(C), so the user can easily see where changes will be
							applied on submit.
						

* 

To perform a batch update on the DataSource, the user should press the "Save Changes" button(E) in the service column. Only then
							any of the modifications applied on cell values will be updated in the underlying data. Therefore, there is a single __RadGrid__
							refresh. This provides better performance with larger grids or such containing other controls that need to be recreated on
							refresh.
						

# Row editing

Row editing is enabled by setting __editable.mode__ to "row". In this scenario when a cell is double-clicked/tapped
					the entire row, to which it belongs, becomes editable. On exiting edit mode, changes are immediately pushed to the DataSource. Following
					is a description of the order of actions when row editing is performed.
				![grid-editing-row-mode](../Media/Controls\Grid\grid-editing-row-mode.png)

* 

To enter edit mode, the end-user should double click/tap a cell in the target row. Alternatively the end-user can create a new row with the "Create a
              new row" button(C).
            

* 

The row becomes editable and displays an edit control(A) in each cell and a cancel button(B) over its top left corner. The cancel button will clear
              any changes that have been made to the row and will cause it to exit edit mode. In case the end-user has used the
              "Create a new row" button(D), the new row becomes editable.
            

* 

If the user wants to keep the change, they can double click/tap any other row. Then the changes will be committed and the row
							will exit edit mode. The row that was double-clicked/tapped will not enter edit mode.
						

* 

Once the changes in a row are confirmed, the data is updated in the DataSource. Since each change in it triggers a refresh in
							RadGrid, every successful edit in the control will cause it to refresh. Therefore, this edit mode is most suitable for cases
							where usually an edit in the data source is made on per row basis. When cells from multiple rows should be edited at once, the
							batch cell update would be a better performing option.
						

# Related Topics
