---
title: Column Resize/Reorder
meta_title: Column Resize/Reorder
meta_description: description.
slug: 
tags:column,resize/reorder
publish:True
---


This article explains the changes in the HTML output and additional CSS classes of RadGrid in scenarios with column resizing
				or reordering enabled.
			

# HTML output with resizing enabled

When resizing is enabled there is no change in the header cells’ content. The difference in rendering comes when a column
					enters resizable mode (after you press and hold its header). A *div* element is added to
					each header's cell that wraps its content, as well as a *span* element used to display the
					resize handle.
				


 __html__
    


		<thead>
			<tr>
				<th class="k-header t-selected">
					<div class="t-wrapper">Header 1</div>
					<span class="t-resize-handle"></span>
				</th>
				<th class="k-header">Header 2</th>
			</tr>
		</thead>



Class/selector name

Description

__.t-selected __

Indicates the selected state of the column header.>
									One additional class is added to the header cell when the cell enters resizable mode. If the cell is the 
									last visible cell in the header row, the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.t-last-column</legacyBold> is added to its existing
									classes.
								

__.k-header .t-wrapper__

Wrapper for the content of the header cell when resizing starts.
							

__.k-header .t-resize-handle__

The resize handle which appears when the column enters resizable mode. The icon in the resize handle is made of symbols from Segoe UI Symbol, 
								using the __:before__ and __:after__ CSS pseudo-elements.
							

# HTML Output with Reordering Enabled

When reordering is enabled, the only thing which is changed is that when a column header is tapped and being dragged, the 
				__.t-dragged__ class is added to the table header cell to highlight the dragged cell.

# Related Topics

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
