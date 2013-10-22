---
title: Expand/Collapse Groups in Code
meta_title: Expand/Collapse Groups in Code
meta_description: description.
slug: 
tags:expand/collapse,groups,in,code
publish:True
---


You can programmatically expand and collapse RadGrid groups, using the RadGrid public API. This help article shows an example of how to use the
				__expandGroup(groupHeader)__ and __collapseGroup(groupHeader)__ methods to expand and collapse a certain
				group.
			

# Section1Expand/Collapse Groups in Code

The __expandGroup__ and __collapseGroup__ methods accept a single argument, which is the DOM element
					or corresponding jQuery object, containing the headers of the groups that you want to expand/collapse. Following is an example of how to expand/collapse
					all groups in RadGrid, based on the expanded state of the first group.
				

The main logic in the following code snippet is represented by these steps:

* 

Access all group headers in RadGrid by class name.

* 

If the headers array has length greater than 0 (the control is indeed grouped), access the first header and the icon inside it.
							The icon is accessed by its first class name assigned.
						

* 

Check whether the icon has expand class or collapse class applied. Based on that, call either the __expandGroup__ method or
							__collapseGroup__ method and pass to it the group headers.
						


 __js__
    


						var groupHeaders = grid.element.querySelectorAll(".k-grid-content tr.k-grouping-row");
						if (groupHeaders.length > 0) {
							var firstGroup = groupHeaders[0];
							var icon = firstGroup.getElementsByClassName("k-icon")[0];
							if (icon.classList.contains("k-i-collapse")) {
								grid.collapseGroup(groupHeaders);
							}
							else {
								grid.expandGroup(groupHeaders);
							}
						}



You can also pass a single header to expand or collapse a single group.

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/GroupExpandCollapseInCode*.
        

# Related Topics

 * [Access Items and Data]({{slug:access-items-and-data}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
