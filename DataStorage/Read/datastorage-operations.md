---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


You can execute read operations in __Data Storage__ by either writing SQL queries and passing them to the __query()__
				method or using the Data Storage API. The latter option is easier to use and maintain but as of current does not cover all read scenarios (for example,
				join operations). This article will explain the two ways to perform read operations when using the __Data Storage__ component.
			

# sqlUsing SQL Statements

You can execute SQL queries that you have written against the database. The syntax of a query must conform to the SQLite synax.
					See reference here: [SQL As Understood By SQLite](http://www.sqlite.org/lang_select.html).
				

Once you build an expression, use the __query()__ method to execute it. The method returns a
					__WinJS.Promise__ object. When the promise is fulfilled, an array with the resulting data records is passed to the
					*onComplete* function.
				

The example below shows how to get a filtered data set using the __query()__ method.
				


 __js__
    


		function queryDb(sql) {
		}



In this and the rest of the examples in this article, __querySuccess()__ is a function that processes the returned data and closes
					the database connection:
				


 __js__
    


		function querySuccess(result) {
			showResults(result);
			db.close();
		}



The __query()__ method can be used for simple select scenarios or when you already have your SQL statements prepared. In most
					scenarios, it will be easier and faster to query your data using the Data Storage API described in the next section.
				

# apiUsing Data Storage Fluent API

To get data easily and without long SQL statements, you can use the __Data Storage__ fluent API. You can join tables, apply multiple
					group, filter and sort expressions without the need of maintaining long SQL strings. Furthermore, using IntelliSense, the fluent API guides you through
					the exact order of execution of functions. This is done by dynamically updating the list of available methods to call upon typing.

				

To be able to query data using the __Data Storage__ method chaining, start with the __get(tableName)__ method
					that receives the name of the table, that you want to query, as an argument. Then, you can optionally apply various data functions using the
					methods from the fluent API. Finally, call the __execute()__ method which will trigger the entire chain of methods and perform a
					read operation.
				

To control the selected data items, you can also use the __distinct()__ and __fields(fieldsObj)__ methods.
					__distinct()__ removes duplicate records from the query result based on the selected fields. __fields(fieldsObj)__
					receives an object argument which lists the fields that should be fetched.
				

The order in which you can call operations is listed below. Any method can be skipped if not needed. You will be prompted by IntelliSense about the
					possible methods that you could call at each step. If you do not follow the correct order, you will receive the following error: *
						JavaScript runtime error: Object doesn't
						support property or method '...'
					*.
				

* 

[join](3590da4e-a4ce-46e8-8430-e26cc19b5bc0)

*Can be called multiple times.*

* 

[group](bc7c4f32-9b92-4fe4-9c18-4b972d50b5be)

*Can be called multiple times.*

* 

distinct
						

*Can be called one time.*

* 

[filter](8657842e-a12e-411c-aaec-9eda1d0d55ed)

*Can be called one time. For applying additional filter expressions, use __and__ and 
						__or__*.
					

* 

[sort](b2c199f2-e74b-408c-834d-53d9b9d4b004)

*Can be called multiple times.*

* 

[skip/take](9ad836f4-79c9-4bcd-b499-62bd00f20e6c)

*Can be called one time.*

* 

fields

*Can be called one time.*>
						Keep in mind that the actual operations are not performed until the entire method chain is triggered by the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">execute()</legacyBold>
						method.
					

# Related Topics

 * [Getting Started]({{slug:getting-started}})[SQL Select](http://www.sqlite.org/lang_select.html)
