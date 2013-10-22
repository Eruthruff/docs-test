---
title: Create Master/Detail Grids
meta_title: Create Master/Detail Grids
meta_description: description.
slug: 
tags:create,master/detail,grids
publish:True
---


This article will explain how to achieve a master-detail grid scenario. In more detail the scenario is as follows:

* 

There are two RadGrid controls on the page.

* 

The first grid has single row selection enabled.

* 

On selecting a row in the first grid, the second is populated with data, related to the first grid selection.

Because of the common data layer in all data-bound controls in the RadControls for Windows 8/HTML suite, you can easily replace the second grid with a
				chart or gauge and visualize data about the selected row.
			

# Implementation

You can follow the steps below to create a master-detail grid scenario in your app.

* 

Define the wrapper elements:


 __html__
    


				<h3>Categories</h3>
				<div id="grid1"></div>
				<h3>Products</h3>
				<div id="grid2"></div>



* 

Define the master grid. In its constructor, declare an event handler for the
							[change event](05b8e184-d500-4f3c-a1a6-ac68a0965ba1) and enable single row selection.
						


 __js__
    


					var masterGrid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Categories",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						},
						columns: [
							{ field: "CategoryName", title: "Category Name" },
							{ field: "Description" }
						],
						selectable: "row",
						height: 350,
						onchange: loadChildRecords
					});



* 

Define the detail grid. At first, you can set its __autoBind__ property to
							*false*, so it does not bind until an item in the master grid is selected.
						


 __js__
    


					var detailGrid = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
					autoBind: false,
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Products",
									dataType: "json"
								}
							},
							schema: {
								data: "value",
								model: {
									fields: {
										OrderDate: { type: "date" }
									}
								},
							},
						},
						columns: [
							{ field: "ProductID", title: "ID" },
							{ field: "ProductName", title: "Product Name" },
							{field: "QuantityPerUnit", title: "Quantity"}
						],
						height: 300
					});



* 

In the __change__ event handler, access the selected row's data item. This is done by getting
							the row element from the event args and passing it to the __dataItem__ method. The data item is
							the entry from the data source that corresponds to the given row. From it, you can access fields that you need for
							filtering the detail grid.
						

Once you have the needed values, you should build a filter object for the child RadGrid's data source. More
							details on filtering a DataSource component are available here: [](69ac0343-692f-402f-a04d-0d00498f34da).
						

Finally, apply the filter to the grid and call __read()__ for its data source, so it can bind to the
							filtered data.
						


 __js__
    


		function loadChildRecords(args) {
			var grid = args.target;
			var selectedRow = grid.selection;
			var dataItem = grid.dataItem(selectedRow);
			var filter = { field: "CategoryID", operator: 'eq', value: dataItem.CategoryID };
	
			var childGrid = document.getElementById("grid2").winControl;
			childGrid.dataSource.filter = filter;
			childGrid.dataSource.read();
		}



The resulting grids are shown below:![grid-howto-master-detail](../Media/Controls\Grid\grid-howto-master-detail.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/MasterDetailGrid*.
        

# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Events]({{slug:events}})

 * [Overview]({{slug:overview}})

 * [Filtering]({{slug:filtering}})
