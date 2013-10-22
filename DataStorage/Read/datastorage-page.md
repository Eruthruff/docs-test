---
title: Page
meta_title: Page
meta_description: description.
slug: 
tags:page
publish:True
---


# 

Paging in __Data Storage__ is based on two methods—__skip(numberToSkip)__ and
					__take(numberToTake)__, used in this order. You first skip a number of records (those of previous pages) and then take the
					number of records that equals your page size. For example, when you implement paging for a control and you have page size of 5, if you need to
					take the items for the third page, you should skip 10 items (old page index*page size) and take the next 5 (page size) items. This is shown in the
					example below. Note that the actual paging takes place along with other operations after the __execute()__ method is called.
				


 __js__
    


							db = Telerik.Data.Database.open("SalesDB");
							db.get("Sales")
								.skip(10)
								.take(5)
								.execute().then(querySuccess);



The __skip(numberToSkip)__ and __take(numberToTake)__ methods are equivalent to the OFFSET and LIMIT
					functions in SQLite. That being said, the logic from the above example is equivalent to this statement:
				

	
					SELECT * FROM Sales LIMIT 5 OFFSET 10
				



# Related Topics[SQL Select](http://www.sqlite.org/lang_select.html)

 * [Overview]({{slug:overview}})
