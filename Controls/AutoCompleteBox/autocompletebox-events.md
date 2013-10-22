---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This help article describes the events fired by RadAutoCompleteBox, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the value of the RadAutoCompleteBox changes.
							

__e.target__ - the RadAutoCompleteBox control whose value has changed. The new value can be accessed
								through *e.target.value*.
							

__close__

Fires when the dropdown list of RadAutoCompleteBox is closed.
							

__e.target__ - the RadAutoCompleteBox control whose dropdown was closed.
							

__databinding__

Fires when the control is about to databind.
							

__e.target__ - the RadAutoCompleteBox control which is about to be bound.
							

__databound__

Fires immediately after the control is databound.
							

__e.target__ - the RadAutoCompleteBox control which has been bound.
							

__open__

Fires when the dropdown list of RadAutoCompleteBoxis shown.
							

__e.target__ - the RadAutoCompleteBox control whose dropdown has been opened.
							

__select__

Fires when an item is selected from the dropdown list.
							

__e.target__ - the RadAutoCompleteBox control in which an item has been selected.
							

__e.item__ - the jQuery object which represents the selected item. 
							

The following example shows how to use the __select__ event to access information about the selected item:
				


 __html__
    


				<span id="myAutoCompleteBox" data-win-control="Telerik.UI.RadAutoCompleteBox" data-win-options="{
							dataSource: [
								{ Name: 'Item1'},
								{ Name: 'Item2'},
								{ Name: 'Item3'}
							],
							dataTextField: 'Name',
							onselect: Sample.Helpers.itemSelected
						}"></span>
				<span id="selection" style="color: #33ccff"></span>




 __js__
    


	WinJS.Namespace.define("Sample.Helpers", {
		itemSelected: WinJS.Utilities.markSupportedForProcessing(function (e) {
			var itemIndex = e.item.index();
			var dataItem = e.target.dataItem(itemIndex);
			document.getElementById("selection").innerText = "Selected: " + dataItem.Name;
		})
	});



# Related Topics
