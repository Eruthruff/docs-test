---
title: Filter
meta_title: Filter
meta_description: description.
slug: 
tags:filter
publish:True
---


# filter

Filtering is initially done by calling the __filter(propertyName, operator, value)__ method. The method receives three arguments:
			  

* 

__propertyName__: The name of the field (table column) that you want to filter by.
					  

* 

__operator__: The filter operator. Accepted values are are <, <=, >, >=, =, ==, !=, and <>.
					  

* 

__value__: The value to filter by.
					  

To apply the filter, call the __execute()__ method.
			  

Here you can see an example that applies a single filter to the data retrieved from a Sales table in a SalesDB database.


 __js__
    


							db = Telerik.Data.Database.open("SalesDB");
							db.get("Sales")
								.filter("name", "like", "R%")
								.execute().then(querySuccess);



The above example will produce the same result as calling the __query__ method with the following SQL expression:
			  

	
				  SELECT * FROM Sales WHERE name LIKE 'R%'
			  



To apply multiple filter expressions, use the __and(propertyName, operator, value)__ and
				  __or(propertyName, operator, value)__ methods after the initial filtering applied through the
				  __filter(propertyName, operator, value)__ method. As their names suggest, __and(propertyName, operator, value)__
				  adds a filter expression using the *AND* logical operator while __or(propertyName, operator, value)__ adds
				  a filter expression using the *OR* logical operator.
			  

Here is an example of two filter expressions chaining. You can see that the __execute()__ method is called at the end. This method
				  triggers the entire chain of expressions.
			  


 __js__
    


							db.get("Sales")
								.filter("name", "like", "R%")
								.and("bonus", ">", 100)
								.execute().then(querySuccess);



The above example will produce the same result as calling the __query__ method with the following SQL expression:
			  

	
				  SELECT * FROM Sales WHERE name LIKE 'R%' AND bonus  > 100
			  



# Related Topics[SQL Select](http://www.sqlite.org/lang_select.html)

 * [Overview]({{slug:overview}})
