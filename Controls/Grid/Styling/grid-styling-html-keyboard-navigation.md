---
title: Keyboard Navigation
meta_title: Keyboard Navigation
meta_description: description.
slug: 
tags:keyboard,navigation
publish:True
---


This topic lists the CSS selectors you can use to apply custom styling to __RadGrid's__ built-in keyboard support.
      

# 

__RadGrid's__ keyboard support logic does not add any additional HTML elements when navigating through the grid. Instead, the selected 
          elements are assigned a class name, which can be used for styling.
        


 __html__
    


		<table>
			<tbody>
				<tr>
					<td class="k-state-focused">Cell 1</td>
	                <td>Cell 2</td>
	                <td>Cell 3</td>
	                <td>Cell 4</td>
				</tr>
			</tbody>
		</table>



Class/selector name

Description

__.k-grid tr > .k-state-focused__

The focused grid cell.
              

__.k-grid tr > .k-state-selected.k-state-focused__

The focused grid cell when it is also selected.
              

__.k-grid .k-grouping-row > .k-state-focused__

A grouping row when it is focused.
              

__.k-grid-header .k-header.k-state-focused__

A grid header when it is focused.
              

# Related Topics
