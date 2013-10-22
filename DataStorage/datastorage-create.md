---
title: Create Operation
meta_title: Create Operation
meta_description: description.
slug: 
tags:create,operation
publish:True
---


This article explains the two ways to populate a table using Data Storage API. The first one is through the __insert(storeName, data)__
				method of the __Database__ object. The other is to get ahold of the target table first through the __use(storeName)__
				method and than use the shorthand __insert(data)__ method. Both approaches are described in more detail in the following sections.
			

# Insert Records Using insert(storeName, data) method

The two arguments accepted by the __Database.insert()__ method are:
				

* 

__storeName__: The name of the table into which data should be inserted. If the table does not exist, it will be created.
						

* 

__data__: The object containing the record to be inserted.
						

You can call the method multiple times and the data objects will be stored for insert. To save the pending changes, call the
					__sync()__ and __close()__ methods of the __Database__ object in this order.
				

The example below demonstrates multiple inserts into a table done with a *for* cycle.
				


 __js__
    


						db = Telerik.Data.Database.open("ProductsDB");
						//id, name, category and price are variables containing string and numeric values, e.g. 21, "Pancakes", 3, 12
						var product = { id: id, productName: name, categoryId: category, unitPrice: price };
						db.insert(product)
						db.sync().then(function (e) {
							db.close();
							queryDb(); //query the database for latest state of data after insert
						});

>
						The inserted items must have a field called <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">id</legacyBold> which carries unique values for each record. This field will be used to
						recognize records when you update and delete them.
					

# Insert Records Using insert(data) method

In this scenario, you first need to get a reference to the table. This is done via the __use(storeName)__ method. Once you have the table
					reference, you can call the __insert(data)__ method one or more times.
				

The __data__ argument that the __insert(data)__ method accepts must be an object containing the data values
					to be inserted. Multiple calls to the method can be chained one after another. When all data is listed for insert, call the __sync()__
					method at the end of the chain to trigger the actual insert operations. The method returns a __WinJS.Promise__ which you can use to close
					the database connection once the insert operations have been finished (either successfully or with an error).
				

Following is an example of insert using the __insert(data)__ method.
				


 __js__
    


						db = Telerik.Data.Database.open("ProductsDB");
						//id, name, category and price are variables containing string and numeric values, e.g. 21, "Pancakes", 3, 12
						var product = { id: id, productName: name, categoryId: category, unitPrice: price };
						db.use("Products")
						.insert(product)
						.sync().then(function (e) {
							db.close();
							queryDb(); //query the database for latest state of data after insert
						});

>
						The inserted items must have a field called <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">id</legacyBold> which carries unique values for each record. This field will be used to
						recognize records when you update and delete them.
					

# Related Topics

 * [Delete Operation]({{slug:delete-operation}})

 * [Update Operation]({{slug:update-operation}})
