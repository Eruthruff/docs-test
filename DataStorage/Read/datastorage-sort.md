---
title: Sort
meta_title: Sort
meta_description: description.
slug: 
tags:sort
publish:True
---


# sort

To get a sorted data set from a table, use the __sort(propertyName, direction)__ method. The method receives two arguments:
				

* 

__propertyName__: The name of the field (table column) that you want to sort by.
						

* 

__direction__: The sort order – *"asc"* for ascending or *"desc"*
							for descending.
						

To apply the sort expression, call the __execute()__ method.
				

The following example shows how to apply a single sort expression to the data retrieved from a Sales table in a SalesDB database.


 __js__
    


							db.get("Sales")
								.sort("name", "asc")
								.execute().then(querySuccess);



The above example will produce the same result as calling the __query__ method with the following SQL expression:
				

	
					SELECT * FROM Sales ORDER BY name ASC
				



To apply multiple sort expressions, use the __sort(propertyName, direction)__ method multiple times. At the end, call the
					__execute()__ method to trigger the chain of sort expressions.
				

This example shows how to apply multiple sort expressions.


 __js__
    


							db.get("Sales")
								.sort("salesQuota", "desc")
								.sort("name", "asc")
								.execute().then(querySuccess);



The above logic is equivalent to the following SQL expression:

	
					SELECT * FROM Sales ORDER BY salesQuota DESC, name ASC
				



# Related Topics[SQL Select](http://www.sqlite.org/lang_select.html)

 * [Overview]({{slug:overview}})
