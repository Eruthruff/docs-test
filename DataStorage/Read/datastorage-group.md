---
title: Group
meta_title: Group
meta_description: description.
slug: 
tags:group
publish:True
---


# 

You can perform grouping of dataset rows and get aggregates for these groups using a combination of the __group(propertyName)__ and
					__fields(fieldsObj)__ methods.
				

The __group(propertyName)__ method accepts a single string argument that is the name of the field which will be used for group
					evaluation.
				

To be able to access the aggregates of the resulting groups, you should list the required fields and aggregate functions using the
					__fields(fieldsObj)__ method.
				

The example below groups by salesQuota field and then counts the number of people having the same quota. Finally,	the __execute()__
					method is called to trigger the actual grouping.
				


 __js__
    


							db = Telerik.Data.Database.open("SalesDB");
							db.get("Sales")
								.group("salesQuota")
								.fields({
									salesQuota: "salesQuota",
									name: "name",
									count: "count(name)"
								})
								.execute().then(querySuccess);



This snippet is equivalent to a query with the following syntax:

	
					SELECT salesQuota, name, COUNT(name) AS count FROM Sales GROUP BY salesQuota
				



If you want to group by more than one field, use the __group(propertyName)__ method multiple times. You can see this done in the
					following code snippet where the query defines two group-by fields - bonus and salesQuota.
				


 __js__
    


							db = Telerik.Data.Database.open("SalesDB");
							db.get("Sales")
								.group("bonus")
								.group("salesQuota")
								.fields({
									name: "name",
									bonus: "bonus",
									salesQuota: "salesQuota",
									count: "count(name)"
								}).execute().then(querySuccess);



The corresponding SQL query would look like this:

	
					SELECT name, bonus, salesQuota, COUNT(name) AS count FROM Sales GROUP BY bonus, salesQuota
				



# Related Topics[SQL Select](http://www.sqlite.org/lang_select.html)

 * [Overview]({{slug:overview}})
