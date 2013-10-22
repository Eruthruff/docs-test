---
title: Access Items and Data
meta_title: Access Items and Data
meta_description: description.
slug: 
tags:access,items,and,data
publish:True
---


For different customization scenarios, you need to access various parts of RadGrid or the data corresponding to them. This article explains
				how you could access different items - rows, headers, footers and also how to access data from data bound parts of the grid.
			

# rowsAccessing Rows

Rows are not represented by specific JavaScript objects, so you can access them as DOM elements. The simplest selector that you can
					use to get all rows in RadGrid is :
				

	
					gridElement.querySelectorAll(".k-grid-content tr”)
				



However, in hierarchy and grouping scenarios, there are additional *tr* elements in the grid table,
					representing headers/footers. Following is an example showing how to filter them out.
				


 __js__
    


						var gridElement = document.getElementById("grid1").winControl.element;
						var rows = gridElement.querySelectorAll(".k-grid-content tr:not(.k-header), .k-grid-content tr:not(.k-grouping-row)");



# headerAccessing the Header

The grid header row can also be accessed using a query selector. It is contained inside a *div*
					element, outside of the grid table, with a __.k-grid-header__ class name.
				


 __js__
    


						var gridElement = document.getElementById("grid1").winControl.element;
						var header = gridElement.querySelector(".k-grid-header tr");



Note that if you have a hierarchy scenario and you need to access only a certain header, you need to provide a more specific
					selector, based on the level of the table you are targeting.
				

# footerAccessing the Footer

The footer row itself has a __.k-footer-template__ class name, so a simple selector can be used for it in
					non-hierarchical scenarios.
				


 __js__
    


						var gridElement = document.getElementById("grid1").winControl.element;
						var footer = gridElement.querySelector("tr.k-footer-template");



When the grid is hierarchical and has footers at the different levels, you need to provide a more specific
					selector, based on the level of the table you are targeting.
				

# selectionAccessing Selected Cells and Rows

When cell/row selection is enabled in RadGrid, you may want to access the currently selected items. This is easily
					done using the __selection__ property of the control. It gets the DOM elements of the selected rows/cells.
				


 __js__
    


						var grid = document.getElementById("grid1").winControl;
						var selectedRows = grid.selection;



# selection-dataAccessing Data Associated with Selection

To access data associated with a selected row, you can pass the row element to the __dataItem__ method of
					RadGrid. It accepts a row element and returns the corresponding data item from the data source of the control. Then, you can access
					all properties belonging to this item, even those that are not associated with grid columns.
				


 __js__
    


						var grid = document.getElementById("grid1").winControl;
						var selectedRows = grid.selection;
						if (selectedRows.length > 0) {
							var data = grid.dataItem(selectedRows[0]);
							info1.innerText = "First selected category: " + data.Name;
						}



If you have a reference to a selected cell, you need to first get its parent row and then pass it to the
					__dataItem__ method:
				

	
					var row = grid.selection[0].parentNode;
					var data = grid.dataItem(row);
				



# hierarchyAccessing Rows from a Child Table in Hierarchy

To get the rows only from a currently expanded child table, you should first get the table element and then search inside it
					using the selector from the sample below.
				


 __js__
    


						var grid = document.getElementById("grid1").winControl;
						if (grid.detailTables.length > 0) {
							var detailGridElement = grid.detailTables[0].element;
							var detailRows = detailGridElement.querySelectorAll(".k-grid-content .t-table-view tbody tr");
							info1.innerText = "First details table has " + detailRows.length + " detail rows.";
						}



# parentAccessing Parent Row and Table

If you have a reference to a child grid table in a hierarchy scenario and you want to access its parent row and table, you
					can use the RadGrid API directly.
				


 __js__
    


						var grid = document.getElementById("grid1").winControl;
						if (grid.detailTables.length > 0) {
							var detailGrid = grid.detailTables[0];
							var parentRow = detailGrid.parentRow;
							var parentTable = detailGrid.parentTable;
						}



# group-headersAccessing Group Headers

To access all group headers in RadGrid, you can get them by class name:


 __js__
    


						var gridElement = document.getElementById("grid2");
						var groupHeaders = gridElement.querySelectorAll(".k-grid-content tr.k-grouping-row");



If static headers are enabled, note that the headers at the top are not part of the grid table, so you need to get them
					separately:
				


 __js__
    


						var gridElement = document.getElementById("grid2");
						var staticHeaders = gridElement.querySelectorAll(".t-fixedGroupHeader tr.k-grouping-row");



# group-footersAccessing group footers

Group footers are accessed the same way as regular group headers, only the second class name in the selector should be changed:
				


 __js__
    


						var gridElement = document.getElementById("grid2");
						var groupFooters = gridElement.querySelectorAll(".k-grid-content tr.k-group-footer");



# Related Topics

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
