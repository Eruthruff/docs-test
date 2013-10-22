---
title: Database Indexes
meta_title: Database Indexes
meta_description: description.
slug: 
tags:database,indexes
publish:True
---


# Section1

Database indexes are lookup tables used to speed up Read operations and, most of all, filtering by the indexed fields in large tables.
					They are briefly described in this document: [](http://www.tutorialspoint.com/sqlite/pdf/sqlite_indexes.pdf)
					The __Data Storage__ component exposes public API that allows you to easily add indexes to your database. The
					__addIndex()__ method adds an index for a given table and field in the current data store. It accepts the
					following arguments(they are all required for proper functioning of the indexes):
				

* 

__storeName__: The name of the data table that you want to create an index for.
						

* 

__fieldName__: The name of the field (column) that you want to use in the index.
						

* 

__indexName__: The name that you want to give to the index.
						

* 

__unique__: A Boolean value indicating whether the indexed data field values are unique or not. If they are
							unique, you will not be able to insert a new row that has the same combination of index field values as an already existing one.
						

* 

__sortOrder__: The sort order for the index. Valid values are *"asc"* for
							ascending and *"desc"* for descending.
						

* 

__position__: A numeric value specifying the position (0-based) of the current index column in the index table. This
							parameter is useful for query performance optimizations.
						

The following example creates an index using the name field of the Sales table. The index is named "nameIndex", it is defined as
					unique, sorted in ascending order and placed at position 0 in the index table.
				


 __js__
    


						db.addIndex("Sales", "name", "nameIndex", true, "asc", 0);



You can add multiple indexes based on your data base structure and data operations.>Currently, an index can be dropped only by dropping the table it is created for.

# DOs and DON'Ts

You can use indexes for performance optimizations when:

* 

You work with large table(s) of data.

* 

You are going to perform mostly Read operations.

Do not use indexes when:

* 

You work with small data sets.

* 

You are going to perform frequent and numerous Create, Update and Delete operations on the table.

* 

The column that you want to index contains many null values.

For further information about indexes in SQLite, check out the links in the __See Also__ section below.
				

# Related Topics[CREATE INDEX As Understood By SQLite](http://www.sqlite.org/lang_createindex.html)[The SQLite Query Planner](http://www.sqlite.org/optoverview.html)[Query Planning for SQLite](http://www.sqlite.org/queryplanner.html)
