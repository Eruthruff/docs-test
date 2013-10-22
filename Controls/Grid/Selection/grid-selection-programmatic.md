---
title: Select Rows and Cells in Code
meta_title: Select Rows and Cells in Code
meta_description: description.
slug: 
tags:select,rows,and,cells,in,code
publish:True
---


When you want to preselect items, perform selection upon some user action, or clear the current selection, you can use the RadGrid public API for selection. This
				article describes the ways to select and deselect items in code.
			

# Selecting Rows and Cells Programmatically

Items in RadGrid can be selected using the __selection__ property of the control. To set selected items, assign it the collection of the
					DOM elements (TDs or TRs) or the corresponding jQuery objects of the cells/rows that you want to select. For cell selection you should pass the separate
					TD elements, while for row selection, the entire TR elements need to be passed.
				

Following is an example where upon click of a button, all alternating grid rows are selected:


 __html__
    


			<div id="grid2"></div>
			<button id="btn">Select alternating rows</button>
			<button id="btn2">Clear selection</button>




 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						dataSource: {
							data: [
								{ Name: "Lily", ID: 1 },
								{ Name: "Kate", ID: 2 },
								{ Name: "Dan", ID: 3 },
								{ Name: "Mark", ID: 4 }
							],
						}
					});
					btn.addEventListener("click", function () {
						grid.selectable = "multiple, row";
						grid.refresh();
						var selection = grid.element.querySelectorAll(".k-alt");
						grid.selection = selection;
					});

![grid-selection 2](../Media/Controls\Grid\grid-selection_2.png)

To alter the selected items, just set the property to a different set of cells/rows.

# Clearing RadGrid Selection Programmatically

When you want to clear the entire selection from RadGrid, both user-defined and programmatic, you can call the __clearSelection()__
					method of the control.
				

The example above can be extended to clear selection in RadGrid on button click with the following code snippet:


 __js__
    


					btn2.addEventListener("click", function () {
						grid.clearSelection();
					});



This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/SelectingRowsAndCellsInCode*.
        

# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})
