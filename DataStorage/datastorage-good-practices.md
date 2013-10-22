---
title: Good Practices
meta_title: Good Practices
meta_description: description.
slug: 
tags:good,practices
publish:True
---


# 

* 

Since database operations use heavy COM operations to transfer data through the ABI, you should carefully avoid the "N+1 select problem". In other
							words the data fetch strategy of the application should be optimized where possible.
						

* 

Make good use of the asynchronous operations in the Data Storage. For more information on asynchronous programming in Windows Store applications,
							go to [Asynchronous programming in JavaScript ](http://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).
						

* 

Carefully take decisions if the database should be fully normalized. Sometimes, it is better to keep some tables denormalized in order to avoid
							expensive join operations, especially in case of small amount of records in table.
						

# Related Topics
