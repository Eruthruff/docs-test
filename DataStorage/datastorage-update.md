---
title: Update Operation
meta_title: Update Operation
meta_description: description.
slug: 
tags:update,operation
publish:True
---


This article explains the two ways to update data in a table using __Data Storage__ API. The first one is through the 
				__update(storeName, data)__ method of the __Database__ object. The other is to get ahold of the target table first 
				through the __use(storeName)__ method and than use the shorthand __update(data)__ method. Both approaches are 
				described in more detail in the following sections.
			

# Update Records Using update(storeName, data) method

The two arguments accepted by the __Database.update()__ method are:
				

* 

__storeName__: The name of the table whose data should be updated.
						

* 

__data__: The object containing the record with the updated values.
						

You can call the method multiple times and the data objects will be stored for update. To save the pending changes, call the
					__sync()__ and __close()__ methods of the __Database__ object in this order.
				

The record id will be used to match the updated data object to a row in the table. Then, all differences from the passed data item will be applied to the one
					in the database. If there is no id match, no update will take place.
				

The example below demonstrates a data update in a table.
				


 __js__
    


						db = Telerik.Data.Database.open("ProductsDB");
						//id, name, category and price are variables containing string and numeric values, e.g. 21, "Pancakes", 3, 12
						var product = { id: id, productName: name, categoryId: category, unitPrice: price };
						db.update("Products", product);
						db.sync().then(function (e) {
							db.close();
							queryDb(); //query the database for latest state of data after update
						});



# Update Records Using update(data) method

In this scenario, you first need to get a reference to the table. This is done via the __use(storeName)__ method. Once you have the table
					reference, you can call the __update(data)__ method one or more times.
				

The __data__ argument that the __update(data)__ method accepts must be an object containing the data values
					of the row that needs to be updated. Multiple calls to the method can be chained one after another. When all data is listed for update, call the 
					__sync()__ method at the end of the chain to trigger the actual update operations. The method returns a 
					__WinJS.Promise__ which you can use to close
					the database connection once the update operations have been finished (either successfully or with an error).
				

The record id will be used to match the updated data object to a row in the table. Then, all differences from the passed data object will be applied to 
					the one in the database. If there is no id match, no update will take place for the current item.
				

Following is an example of update using the __update(data)__ method.
				


 __js__
    


						db = Telerik.Data.Database.open("ProductsDB");
						var product = { id: id, productName: name, categoryId: category, unitPrice: price };
						db.use("Products")
						.update(product)
						.sync().then(function (e) {
							db.close();
							queryDb(); //query the database for latest state of data after update
						});



# Related Topics

 * [Create Operation]({{slug:create-operation}})

 * [Delete Operation]({{slug:delete-operation}})
