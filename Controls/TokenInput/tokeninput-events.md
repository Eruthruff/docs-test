---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadTokenInput, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the value of the RadTokenInput changes.
							

__e.target__: The RadTokenInput control whose value has changed. The new value can be accessed
								through *e.target.value*.
							

__close__

Fires when the dropdown list of RadTokenInput is closed.
							

__e.target__: The RadTokenInput control whose dropdown was closed.
							

__databinding__

Fires when the control is about to databind.
							

__e.target__: The RadTokenInput control that is about to be bound.
							

__databound__

Fires immediately after the control is databound.
							

__e.target__: The RadTokenInput control that has been bound.
							

__open__

Fires when the dropdown list of RadTokenInput is shown.
							

__e.target__: The RadTokenInput control whose dropdown has been opened.
							

__select__

Fires when an item is selected from the dropdown list of RadTokenInput.
							

__e.target__: The RadTokenInput control in which an item has been selected.
							

__e.item__: The jQuery object that represents the selected item.
							

Here follows an example of using the __select__ event to access information about the selected item.
				


 __html__
    


				<span id="myTokenInput" data-win-control="Telerik.UI.RadTokenInput" data-win-options="{
							dataSource: [
								{ Name: 'Pears', ID: 1 },
								{ Name: 'Apples', ID: 2 },
								{ Name: 'Strawberries', ID: 3 },
								{ Name: 'Bananas', ID: 4 },
								{ Name: 'Raspberries', ID: 5 },
								{ Name: 'Cherries', ID: 6 }
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
