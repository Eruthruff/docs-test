---
title: Virtual Scrolling
meta_title: Virtual Scrolling
meta_description: description.
slug: 
tags:virtual,scrolling
publish:True
---


Without much effort, you can do a great performance optimization for a __RadGrid__ displaying large sets of data. What
				virtual scrolling (or data virtualization) does is to render only the currently needed data in the grid. Data records that are outside of the visible part of the
				scrollable area are not loaded. The __DataSource__ used to bind __RadGrid__ takes care of
				retrieving only the needed records and they are then visualized by the grid.
			

# Virtual Scrolling

To enable virtual scrolling, do the following:
				

* 

Set the __scrollable__ property to *"virtual"*.
						

* 

Provide a value to the __dataSource.pageSize__ property, which corresponds to the number of items you want to show at a time.
							This value will determine the initial number of items loaded in the grid.
						

* 

Set height to RadGrid, such that all items from one page of data will be visible.

When binding RadGrid to remote data, make sure that you specify a function returning the total number of records in the remote source of data.
					Otherwise virtual scrolling will not work correctly when it retrieves remotely paged data. The example below demonstrates a scenario of remote
					binding with virtual scrolling enabled:
				


 __js__
    


					var ds = new Telerik.Data.DataSource({
						transport: {
							read: {
								url: 'http://services.odata.org/Northwind/Northwind.svc/Order_Details',
								dataType: 'json'
							}
						},
						schema: {
							data: 'value',
							total: Scrolling.total
						},
						pageSize: 10
					});
					ds.read().then(function () {
						var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
							dataSource: ds,
							scrollable: "virtual",
							columns: [
								{ field: "OrderID", title: "Order ID" },
								{ field: "ProductID", title: "Product ID" },
								{field: "UnitPrice", title: "Unit Price"},
								{field: "Quantity", title: "Quantity"},
								{field: "Discount", title: "Discount"}
							],
							height: 400
						});
					});




 __js__
    


	WinJS.Namespace.define("Scrolling", {
		total: function (response) {
			return response.value.length;
		}
	});

><legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Current limitations of scrolling</legacyBold>>Virtual scrolling does not work with grouping enabled.>Virtual scrolling does not work with hierarchy.>
						When scrolling is enabled, multiple cell selection on the last column in RadGrid can only be performed using the top-left handle of the currently
						selected cell(s). The right one is covered by the scrollbar.
					

# Tip: How to Make the Scrollbar Always Visible

For smaller screen devices, if you want to have a scrollbar always visible in virtual scrolling mode in the grid, add the following CSS to your app:
				

	
					/*show virtual scrollbar*/
					.k-scrollbar.k-scrollbar-vertical {
						-ms-overflow-style: scrollbar;
					}
				



# Related Topics
