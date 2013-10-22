---
title: Selection
meta_title: Selection
meta_description: description.
slug: 
tags:selection
publish:True
---


This article explains the changes in the HTML output and the additional CSS classes of RadGrid in the different scenarios with selection enabled.

# HTML output with "cell" selection mode

In this selection mode, when a cell is selected, no additional HTML is added. The selected *td* element is assigned a class, which can be 
          used for styling.
        


 __html__
    


		<table class="k-selectable">
			<tbody>
				<tr>
					<td>Cell 1</td>
	                <td>Cell 2</td>
	                <td class="k-state-selected">Cell 3</td>
	                <td>Cell 4</td>
				</tr>
			</tbody>
		</table>



Class/selector name

Description

__.k-grid .k-state-selected__

The selected cell which background property is changed.
              

# HTML output with "row" selection mode

Same as the previous selection mode, when a row is selected, no additional HTML is added. The selected *tr* element is assigned a class name.
        


 __html__
    


		<table class="k-selectable">
			<tbody>
				<tr class="k-state-selected">
					<td>Cell 1</td>
	                <td>Cell 2</td>
	                <td>Cell 3</td>
	                <td>Cell 4</td>
				</tr>
			</tbody>
		</table>



Class/selector name

Description

__.k-grid .k-state-selected > td__

All of the cells in the selected row.
              >
                  Note that this time the class is assigned to the row and therefore the CSS selector for styling the selected cells is 
                  different than in the previous selection mode.
                

# HTML output with "multiple, row"/"multiple, cell" selection modes

With these two selection modes, when cells/rows are selected, two *span* elements are added to the top-left and two other are
          added to the bottom-right corner of the selection area. They form an "L" shape and serve as selection editing controls. The user can expand or reduce the
          selection through them.
        >
            Note that if a CTRL key "jump" selection is used to select cells or rows that are not adjacent or do not form a rectangle, the <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">span</legacyItalic> 
            elements, that are initially in the top-left and the bottom-right corner of the selection area, will no longer be available.
          

The additional classes for the selected rows/cells are applied as in the previous selection modes depending on whether you 
          have *"multiple, cell"* or *"multiple, row"* selection mode enabled.
        


 __html__
    


		<table class="k-selectable">
			<tbody>
				<tr class="k-state-selected">
					<td>
	                    Cell 1
	                    <span class="t-expand t-nw">
	                        <span></span>
	                        <span></span>
	                    </span>
					</td>
	                <td>Cell 2</td>
	                <td>Cell 3</td>
	                <td>
	                    Cell 4
	                    <span class="t-expand">
	                        <span></span>
	                        <span></span>
	                    </span>
	                </td>
				</tr>
			</tbody>
		</table>



Class/selector name

Description

__.k-grid .k-state-selected__

All of the selected cells if the selection mode is *"multiple, cell"*.
              

__.k-grid .k-state-selected > td__

All of the cells in the selected rows if the selection mode is *"multiple, row"*.
              

__.k-grid .t-expand span__

The *span* elements in the top-left and the bottom-right corner.
              

__.k-grid .t-expand.t-nw span__

The *span* elements in the top-left corner. In case you want to style them differently than the
                *span* elements in the bottom-right corner, you can use this selector.
              

__.k-grid .t-expand.t-active span__

When the *span* elements in the top-left or the bottom-right corner are clicked and dragged to expand or reduce the selection, 
                a new class __t-active__ is added to them. You can use this selector to style both the top-left and the bottom-right corner 
                *span* elements in their active state.
              

__.k-grid .t-expand.t-nw.t-active span__

The *span* elements in the top-left corner in their active state if you want to 
                style them differently than the *span* elements in the bottom-right corner.
              

# Related Topics
