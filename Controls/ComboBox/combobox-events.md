---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadComboBox, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the value of the RadComboBox changes.
						  

__e.target__: The RadComboBox control whose value has changed. The new value can be accessed
							  through *e.target.value*.
						  

__close__

Fires when the dropdown list of RadComboBox is closed.
						  

__e.target__: The RadComboBox control whose dropdown was closed.
						  

__databinding__

Fires when the control is about to databind.
						  

__e.target__: The RadComboBox control which is about to be bound.
						  

__databound__

Fires immediately after the control is databound.
						  

__e.target__: The RadComboBox control that has been bound.
						  

__open__

Fires when the dropdown list of RadComboBox is shown.
						  

__e.target__: The RadComboBox control which dropdown has been opened.
						  

__select__

Fires when an item is selected from the dropdown list.
						  

__e.target__: The RadComboBox control in which an item has been selected.
						  

__e.item__: The jQuery object which represents the selected item.
						  

Here is an example of using the __select__ event to access information about the selected item:
			  


 __html__
    


				<span id="myComboBox" data-win-control="Telerik.UI.RadComboBox" data-win-options="{
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
