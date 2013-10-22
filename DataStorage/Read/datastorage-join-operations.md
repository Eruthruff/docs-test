---
title: Join Operations
meta_title: Join Operations
meta_description: description.
slug: 
tags:join,operations
publish:True
---


The __Data Storage__ component supports joining data from two or more tables and then executing operations on it, all using the
				component's fluent API. This article explains what a join operation is and how to perform it in __Data Storage__.
			

# Join Operations

The logic of join operations in __Data Storage__ is same as with the SQL join. The columns of the two tables are joined based
					on matches between the two provided fields. For example, consider you have these two tables:
				Categories![datastorage-join-categories](../Media/DataStorage\datastorage-join-categories.png)Products![datastorage-join-products](../Media/DataStorage\datastorage-join-products.png)

The result from joining these two tables on the CategoryID field on both sides will be:![datastorage-join-categories-products](../Media/DataStorage\datastorage-join-categories-products.png)

# Section1Joining Tables Using Data Storage API

To join two tables, use the __join(tableName, tableFieldName, dataFieldName)__ method. The three arguments it takes are:
				

* 

__tableName__: The string name of the table that should be joined to the current data.
						

* 

__tableFieldName__: The field in the joined table which should be used to join the data.
						

* 

__dataFieldName__: The field in the current table which should be used as a foreign key.
						

You can use the __join(tableName, tableFieldName, dataFieldName)__ method multiple times if you need to get a view from multiple
					tables.
				

Once you join the tables, you can get only a specific subset of their fields, using the __fields(fieldsObj)__ method. It receives
					an object listing all the fields that you need. To differentiate between the two tables, prefix the field name with its owner table name and a dot, e.g.
					"Categories.Description". Defining the fields that you want to fetch is especially important when there are fields with identical names in the tables that
					you join.
				

Following is an example of joining two tables – Categories and Products. After the join, the resulting table is sorted by CategoryName. Note that the
					operations in the method chain are performed on the data in the same order as defined but after the __execute()__ method triggers
					them.
				


 __js__
    


					db = Telerik.Data.Database.open("ProductsDB");
					//select the Products table and then chain all operations
					db.get("Categories")
					.join("Products", "CategoryID", "ID")
					.sort("Categories.CategoryName", "asc")
					.fields({
						categoryName: "Categories.CategoryName",
						productName: "Products.ProductName",
						unitPrice: "Products.UnitPrice"
					})
					.execute()
					.then(querySuccess);



If you populate a __RadGrid__ with the result from this query, it will look like this (using auto-generated columns):
				![datastorage-join-result](../Media/DataStorage\datastorage-join-result.png)

# Related Topics

 * [Overview]({{slug:overview}})[SQL Select](http://www.sqlite.org/lang_select.html)

 * [Overview]({{slug:overview}})
