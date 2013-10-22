---
title: API Methods
meta_title: API Methods
meta_description: description.
slug: 
tags:api,methods
publish:True
---


The __DataSource__ component exposes a number of methods for fetching and manipulating data. They are listed in the sections below.
			

# fetchMethods for Fetching Data

The following table lists the methods that you can use to get data using __DataSource__.
				

Method

Arguments

Description

Example (__ds__ is a __DataSource__ instance in all examples below)
								

__fetch__

None

Fetches data using the current filter/sort/group/paging information. If data is not available or remote operations
								are enabled, data is requested through the transport, otherwise operations are executed over the available data.
							


 __js__
    


						ds.sort = { field: "UnitPrice", dir: "asc" };
						ds.pageSize = 3;
						ds.page = 1;
						ds.fetch();



__query__

__queryObj__: An object containing page, sort, filter and group settings. The settings syntax is the
								same as when they are specified inside the __DataSource__ constructor.
							

Executes a query over the data. Available operations are paging, sorting, filtering, grouping. If data is not available
								or remote operations are enabled, data is requested through the transport. Otherwise operations are executed over the
								available data.
							


 __js__
    


						var query = {
							sort: { field: "UnitPrice", dir: "asc" },
							group: { field: "CategoryID" },
							filter: { field: "UnitPrice", operator: "gt", value: 7 }
						};
						ds.query(query);



__read__

None

Reads the data into the __DataSource__ using the __transport.read__ definition.
							


 __js__
    


						var dataSource = new Telerik.Data.DataSource({
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Categories",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						});
						dataSource.read().then(function () {
							//use result in the promise complete function
							grid.columns = []; //grid is an existing RadGrid control
							grid.dataSource = dataSource;
							grid.refresh();
						});



# get-itemsMethods for Working with Data

This section lists the methods that can be used to access specific items from the __DataSource__ underlying data and get information
					about them.
				

Method

Arguments

Description

Example (__ds__ is a __DataSource__ instance in all examples below)
								

__at__

__index__: The numeric index at which the item is placed in the __DataSource__.
							

Returns the data record at the specified index.
							


 __js__
    


						var productName = ds.at(3).ProductName;
						info.innerText = "Found " + productName + ".";



__getById__

__id__: The ID of the item to retrieve. The ID of a model is defined through the
								__schema.model.id__ option of the __dataSource__.
							

Retrieves an item from the __DataSource__ by a given ID.
							


 __js__
    


						var productName = ds.getById(2).ProductName;
						info.innerText = "Found " + productName + ".";



__getByUid__

__uid__: The uid of the item to retrieve. You need to first get ahold of the item to access and
								store its uid.
							

Retrieves an item from the DataSource by its uid field.
							


 __js__
    


						var item = ds.at(2);
						info.innerText = "Before sort found " + item.ProductName;
						var uid = item.uid;
						ds.sort = { field: "ProductName", dir: "desc" };
						ds.fetch().then(function () {
							var searchedItem = ds.getByUid(uid);
							info.innerHTML += "<p>After sort found " + searchedItem.ProductName;
						});



__indexOf__

__item__: An object taken from the __DataSource__ underlying data.
							

Retrieves the index of a specified object from the underlying data. The object must be a part of the __DataSource__ instance.
							


 __js__
    


						var item = ds.getById(2);
						info.innerText = "Found product " + item.ProductName + " at position " + ds.indexOf(item);



# modifyMethods for Modifying Data

This section lists methods that are used when inserting and removing data from __DataSource__. They include
					methods that check the current state of the data, cancel or push applied changes.
				

Method

Arguments

Description

Example (__ds__ is a __DataSource__ instance in all examples below)
								

__add__

__item__: A JavaScript object containing the new data.
							

Adds a new data item to the __DataSource__.
							


 __js__
    


						ds.add({
							ProductID: 22,
							ProductName: "Grandma's Pancakes",
							CategoryID: 3,
							UnitPrice: 12
						});



__insert__

__index__: The index to insert the new item at.
							

__item__: A JavaScript object containing the new data.
							

Inserts a new item into the __DataSource__ at the specified index.
							


 __js__
    


						ds.insert(20, {
							ProductID: 21,
							ProductName: "Fruit salad",
							CategoryID: 3,
							UnitPrice: 15
						});



__remove__

__item__: An object taken from the __DataSource__ underlying data.
							

Removes the specified item from the __DataSource__.
							


 __js__
    


						var itemToRemove = ds.getById(20);
						ds.remove(itemToRemove);



__hasChanges__

None
							

Gets a boolean value indicating whether data in the __DataSource__ has changed.
							


 __js__
    


						info.innerText = "Has unsaved changes: " + ds.hasChanges();



__cancelChanges__

None
							

Cancels any changes made to the data since the last sync.
							


 __js__
    


						if (ds.hasChanges()) {
							ds.cancelChanges();
						}



__sync__

None
							

Synchronizes changes through the transport. Any pending CRUD operations will be sent to the web service if such is used.
								The __DataSource__ will send one request per item change and change type (create, update, delete).
							


 __js__
    


						var itemToRemove = ds.getById(20);
						ds.remove(itemToRemove);
						ds.sync();



# Related Topics

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})

 * [Configuring Data Editing]({{slug:configuring-data-editing}})
