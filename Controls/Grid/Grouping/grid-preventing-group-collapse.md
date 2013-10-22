---
title: Prevent Groups Collapse
meta_title: Prevent Groups Collapse
meta_description: description.
slug: 
tags:prevent,groups,collapse
publish:True
---


You can easily prevent the user from collapsing groups by removing the collapse icon from the DOM. This would be useful in scenarios where your requirement is to
				always show groups expanded or to perform only programmatic expand/collapse of groups (when you want to change the user experience for
				interacting with groups	in RadGrid).
			

# Preventing Groups Collapse

The easiest way to achieve this is to remove the collapse icon from the DOM—this would result in two things:

* 

There will be no visual clue of the headers being collapsible.

* 

RadGrid performs a check whether there is an icon with the __k-i-collapse__ class name applied in the header element
							before collapsing it. If there isn't, the logic for group collapse does not run. This means that even clicking the header does not
							collapse the group.
						

To hide the icon, you can [attach the databound event](05b8e184-d500-4f3c-a1a6-ac68a0965ba1) and use the code from
					the following code snippet:
				


 __js__
    


		function preventCollapse(e) {
			$(".k-grouping-row .k-icon", e.target.element).remove();
		}

>
						If you attach the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">databound</legacyBold> event using the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">addEventListener</legacyBold> method, after RadGrid is
						created, you may need to call grid.<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">refresh()</legacyBold> for RadGrid to capture the event and hide the icon.
					

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/PreventingGroupsExpandCollapse*.
        

# Related Topics

 * [Access Items and Data]({{slug:access-items-and-data}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
