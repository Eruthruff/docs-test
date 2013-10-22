---
title: Delete Operation
meta_title: Delete Operation
meta_description: description.
slug: 
tags:delete,operation
publish:True
---


This article explains the two ways to delete records from a table using __Data Storage__ API. The first one is through the
			  __remove(storeName, data)__ method of the __Database__ object. The other is to get ahold of the target table first 
			  through the __use(storeName)__ method and than use the shorthand __remove(data)__ method. Both approaches are 
			  described in more detail in the following sections.
		  

# Delete Records Using remove(storeName, data) method

The two arguments accepted by the __Database.remove()__ method are:
			  

* 

__storeName__: The name of the table whose data should be deleted.
					  

* 

__data__: The object containing the record that should be deleted.
					  

You can call the method multiple times and the data objects will be stored for deletion. To save the pending changes, call the
				  __sync()__ and __close()__ methods of the __Database__ object in this order.
			  

The record id will be used to match the passed data object to a row in the table. Then, the row in the database table will be deleted. If there is no 
				  matching record with the same id, no rows will be deleted.
			  

The example below demonstrates a delete action in a table.
			  


 __js__
    


							db = Telerik.Data.Database.open("ProductsDB");
							//id, name, category and price are variables containing string and numeric values, e.g. 21, "Pancakes", 3, 12
							var product = { id: dataItem.id, productName: dataItem.productName, categoryId: dataItem.categoryId, unitPrice: dataItem.unitPrice };
							db.remove(product);
							db.sync().then(function () {
								db.close();
								queryDb(); //query the database for latest state of data after delete
							});



# Delete Records Using remove(data) method

In this scenario, you first need to get a reference to the table. This is done via the __use(storeName)__ method. Once you have the table
				  reference, you can call the __remove(data)__ method one or more times.
			  

The __data__ argument that the __delete(data)__ method accepts must be an object containing the data item to be
				  deleted. Multiple calls to the method can be chained one after another. When all data is listed for delete, call the
				  __sync()__ method at the end of the chain to trigger the actual delete operations. The method returns a
				  __WinJS.Promise__ which you can use to close
				  the database connection once the delete operations have been finished (either successfully or with an error).
			  

The record id will be used to match the data object for deletion to a row in the table. Then, the row in the database table will be deleted. If there is no 
				  id match, no item will be deleted.
			  

Following is an example of a delete operation using the __remove(data)__ method.
			  


 __js__
    


							db = Telerik.Data.Database.open("ProductsDB");
							//id, productName, categoryId and unitPrice are variables containing string and numeric values, e.g. 21, "Pancakes", 3, 12
							var product = { id: dataItem.id, productName: dataItem.productName, categoryId: dataItem.categoryId, unitPrice: dataItem.unitPrice };
							db.use("Products")
							.remove(product)
							.sync().then(function () {
								db.close();
								queryDb(); //query the database for latest state of data after delete
							});



# Related Topics

 * [Create Operation]({{slug:create-operation}})

 * [Update Operation]({{slug:update-operation}})
