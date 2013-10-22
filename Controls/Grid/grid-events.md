---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadGrid, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__change__

Fires when the grid selection has changed.
							

__e.target__ - The RadGrid instance.
							

__columnhide__

Fires when a column in RadGrid is hidden.
							

__e.column__ - The hidden column object.
							

__e.target__ - The RadGrid instance.
							

__columnshow__

Fires when a column in RadGrid is shown.
							

__e.column__ - The shown column object.
							

__e.target__ - The RadGrid instance.
							

__columnreorder__

Fires when a column in RadGrid is reordered.
							

__e.column__ - The reordered column object.
							

__e.newindex__ - The new column index.
							

__e.oldindex__ - The previous column index.
							

__e.target__ - The RadGrid instance.
							

__columnresize__

Fires when a column in RadGrid is resized.
							

__e.column__ - The resized column object.
							

__e.newWidth__ - The new column width.
							

__e.oldWidth__ - The old column width.
							

__e.target__ - The RadGrid instance.
							

__databinding__

Fires when the grid is about to receive data from the data source.
							

__e.items__ - The data items to which RadGrid is about to bind.
							

__e.target__ - The RadGrid instance.
							

__databound__

Fires when the grid is about to receive data from the data source.
							

__e.target__ - The RadGrid instance.
							

__detailCollapse__

Fires when a grid detail row is collapsed.
							

__e.detailRow__ - The jQuery element representing detail row.
							

__e.masterRow__ - The jQuery element representing master row.
							

__e.target__ - The RadGrid instance.
							

__detailExpand__

Fires when a grid detail row is expanded.
							

__e.detailRow__ - The jQuery element representing detail row.
							

__e.masterRow__ - The jQuery element representing master row.
							

__e.target__ - The RadGrid instance.
							

__detailInit__

Fires when the grid detail table is initialized.
							

__e.data__ - The data for the master row.
							

__e.detailCell__ - The jQuery element representing detail cell
							

__e.detailRow__ - The jQuery element representing detail row.
							

__e.detailTable__ - The detail table object.
							

__e.masterRow__ - The jQuery element representing master row.
							

__e.parentTable__ - The master table object.
							

__e.target__ - The RadGrid instance.
							

__edit__

Fired when the user edits or creates a data item.
							

__e.container__ - The jQuery object representing the container element. That element contains the editing UI.
							

__e.model__ - The data item which is going to be edited. Use its __isNew__ method to check if the
								data item is new (created) or not (edited).
							

__e.target__ - The RadGrid instance.
							

__remove__

Fires when the user deletes a row.
							

__e.model__ - The data item to which the table row is bound.
							

__e.row__ - The jQuery object representing the current table row.
							

__e.target__ - The RadGrid instance.
							

__save__

Fired when a data item is saved.
							

__e.model__ - The data item to which the table row is bound.
							

__e.row__ - The jQuery object representing the current table row.
							

__e.target__ - The RadGrid instance.
							

__e.values__ - The values entered by the user. Availabe only when the editable.mode option is set to
								*"cell"* or *"cellBatch"*.
							

__savechanges__

Fired when the user saves all changes he made in RadGrid. In cell batch mode, this happens when the "Save changes" button in the service column is
								pressed. In cell and row edit mode, the event is raised after each edit.
							

__e.target__ - The RadGrid instance.
							

The following example shows how to use the __detailExpand__ event to display information about the last expanded master row:
				


 __html__
    


				<div id="myGrid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: Sample.categories,
					columns: [
						{ field: 'ID', width: 40 },
						{ field: 'Name', title: 'Category' }
					],
					detailTable: {
						dataSource: Sample.data,
						parentRelation: {
							masterField: 'ID',
							detailField: 'CategoryID'
						},
						columns: [
							{ field: 'ID', width: 40 },
							{ field: 'Name' },
							{ field: 'Price'}
						]
					},
					ondetailexpand: Sample.detailExpand
				}">
				</div>
				<p id="gridInfo" style="color: #336699"></p>




 __js__
    


		WinJS.Namespace.define("Sample", {
			detailExpand: WinJS.Utilities.markSupportedForProcessing(function (e) {
				var dataItem = e.dataItem;
				document.getElementById("gridInfo").innerHTML = "Last expanded row ID:" + e.masterRow.find("td:nth-child(2)").text();
			}),
			data: data,
			categories: categories
		});



# Handling Events in a Hierarchical Grid

If you want to have an event attached to all levels of a hierarchical RadGrid (using declarative relations), you need to declare
					the event handler in all detail table definitions. Note that __e.target__ will return the table view, corresponding
					to the current child table. However, you can extract information from it the same way as you would from the RadGrid instance,
					since it exposes identical properties and methods.
				

# Related Topics
