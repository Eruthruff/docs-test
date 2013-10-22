---
title: Expand/Collapse Rows in Code
meta_title: Expand/Collapse Rows in Code
meta_description: description.
slug: 
tags:expand/collapse,rows,in,code
publish:True
---


You can easily perform rows expand/collapse programmatically in hierarchy scenarios. RadGrid exposes two methods—__expandRow(masterRow)__
				and __collapseRow(masterRow)__—which facilitate such action. This article explains how to use these methods.
			

# Hierarchy Expand/Collapse in Code.

Both __expandRow__ and __collapseRow__ methods accept a single argument—the DOM element(s) or corresponding
					jQuery object of the master row(s) that should be expanded/collapsed. The following code sample demonstrates how you can expand/collapse all master rows in
					RadGrid, based on the expanded state of the first row. The logic implemented is as follows:
				

* 

Access all master rows in RadGrid by class name.

* 

Get the first row element and access its expand/collapse icon by its unchanging __"k-icon"__ class name.
						

* 

Check the second class name of the icon—if it is __"k-plus"__, the row is collapsed and should be expanded, otherwise, it
							should be collapsed. Based on this logic, the relevant method is called for all rows.
						


 __js__
    


						var masterRows = grid.element.getElementsByClassName("k-master-row");
						var firstRow = masterRows[0];
						var icon = firstRow.getElementsByClassName("k-icon")[0];
						if (icon.classList.contains("k-plus")) {
							grid.expandRow(masterRows);
						}
						else {
							grid.collapseRow(masterRows);
						}



This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/HierarchyExpandCollapseInCode*.
        

# Related Topics

 * [Access Items and Data]({{slug:access-items-and-data}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
