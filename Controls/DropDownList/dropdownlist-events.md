---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadDropDownList, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the value of the RadDropDownList changes.
							

__e.target__: The RadDropDownList control whose value has changed. The new value can be accessed
								through *e.target.value*.
							

__close__

Fires when the dropdown list of RadDropDownList is closed.
							

__e.target__: The RadDropDownList control whose dropdown was closed.
							

__databinding__

Fires when the control is about to databind.
							

__e.target__: The RadDropDownList control whose is about to be bound.
							

__databound__

Fires immediately after the control is databound.
							

__e.target__: The RadDropDownList control whose has been bound.
							

__open__

Fires when the dropdown list of RadDropDownList is shown.
							

__e.target__: The RadDropDownList control whose dropdown has been opened.
							

__select__

Fires when an item is selected from the dropdown list.
							

__e.target__: The RadDropDownList control in which an item has been selected.
							

__e.item__: The jQuery object which represents the selected item.
							

The following example shows how to use the __select__ event to access information about the selected item:
				


 __html__
    


				<span id="myDropDownList" data-win-control="Telerik.UI.RadDropDownList" data-win-options="{
							dataSource: [
								{ Name: 'Item1', ID: 1 },
								{ Name: 'Item2', ID: 2 },
								{ Name: 'Item3', ID: 3 }
							],
							dataTextField: 'Name',
							dataValueField: 'ID',
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
