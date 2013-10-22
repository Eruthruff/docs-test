---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


Different selection modes are supported in RadGrid. You can choose between cell and row, single and multiple selection. Same as other features, this one is easily
				set, using a single property—__selectable__.
			

# Selection Modes

Below you can see the values accepted by the selectable properties and their meaning:

Value

Meaning

__none__

Selection is disabled.

__cell__

A single cell can be selected in the grid.

__row__

A single row can be selected in the grid.

__multiple, cell__

Selection of multiple cells is allowed. On touch devices it is performed by holding the grip (highlighted angle
								of the first selected cell) and dragging. On devices using mouse and keyboard, the same approach is supported using the mouse; or instead of holding
								the grip, you can press and hold the Ctrl key.
							

__multiple, row__

Selection of multiple rows is allowed. On touch devices it is performed by holding one of the grips (highlighted
								angles of the first selected row) and dragging. On devices using mouse and keyboard, the same approach is supported using the mouse; or instead of holding
								the grip, you can press and hold the Ctrl key.
							>
            Note that as of Q2 2013, when a cell or row is put in edit mode, selection is automatically disabled and all selected items are cleared. Once the
            cell editor is closed selection is turned back on without restoring previously selected items.
          

To see how the selection modes work, you can run the following code:


 __html__
    


				<div id="selectionOptions">
					<input id="radio1" type="radio" value="cell" name="selection" checked="checked" /><label for="radio1">cell</label>
					<input id="radio2" type="radio" value="row" name="selection" /><label for="radio2">row</label>
					<input id="radio3" type="radio" value="multiple, cell" name="selection" /><label for="radio3">multiple, cell</label>
					<input id="radio4" type="radio" value="multiple, row" name="selection" /><label for="radio4">multiple, row</label>
				</div>
				<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{Name: 'Lily', ID: 1},
									{Name: 'Kate', ID: 2},
									{Name: 'Dan', ID: 3},
									{Name: 'Mark', ID: 4}
								],
							},
							selectable: 'cell'
						}">
				</div>




 __js__
    


					var radioButtons = selectionOptions.getElementsByTagName("input");
					for (var i = 0; i < radioButtons.length; i++) {
						radioButtons[i].addEventListener("click", function (e) {
							var mode = e.target.value;
							var grid = grid1.winControl;
							grid.selectable = mode;
							grid.refresh();
						});
					}



The result will look like this:![grid-selection](../Media/Controls\Grid\grid-selection.png)

# Related Topics
