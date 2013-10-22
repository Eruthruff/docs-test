---
title: Using DataSource with Data Storage
meta_title: Using DataSource with Data Storage
meta_description: description.
slug: 
tags:using,datasource,with,data,storage
publish:True
---


From Q3 2013 on, Telerik __DataSource__ features a new transport type which allows it to seamlessly bind to a local database created using
				__Telerik Data Storage__. By tying the two controls together, you eliminate the need of writing queries to the database. This way, you can
				bind all RadControls, that use the __DataSource__ component (__RadGrid__, __RadChart__, etc.), 
				directly to an existing local data storage created by the __Data Storage__ component.
				This article explains how to set up __DataSource__ to work with __Telerik Data Storage__ and describes some 
				specifics that you should have in mind.
			

# Section1Binding DataSource to a Telerik Data Storage Local Database

Follow the steps below to achieve integration between DataStorage and DataSource components.

* 

*
								Create and populate a database using __Data Storage__.
							* You must have a storage already created
							since __DataSource__ can work only with an already existing database.
						

You can learn more about creating and populating a database using __Data Storage__ here:
							[Getting Started with Data Storage](82cab44f-a2db-4a0c-9df0-89e89cd106bc).
						

* 

*Specify the custom transport name*. Set the __type__ property of the
							__DataSource__ instance to *"dataStorage"*. This will instruct the
							__DataSource__ that it needs to connect to a __Data Storage__ database.
						


 __js__
    


	dataSource: {
		type: "dataStorage",
		....
	}



* 

*Set up read operations*. For simple scenarios that use a single table from the database, you can just set the
							__transport.data.dbName__ and __transport.data.tableName__ properties to the names of the existing
							database and the table that you are going to read from, respectively.
						


 __js__
    


			read: {
				data: {
					dbName: "ProductDB",
					tableName: "Products"
				}



If you need to join tables, you can also set the __joinedTables__ property to an array of objects. Each object should represent
							a table that you are going to join to the current table. The objects should list the following options: __destinationTableName__
							(the table which you are joining to the current one), __sourceColumn__ (the column from the current table that you are using for the
							join), __destinationColumn__ (the column from the destination table that you are using for the join).
						


 __js__
    


			read: {
				data: {
					dbName: "ProductDB",
					tableName: "Products",
					joinedTables: [
					{
						destinationTableName: "Categories",
						sourceColumn: "catId",
						destinationColumn: "categoryId"
					}]
				}

>
								Because of a specific in the DataStorage table joins, currently, you must ensure that the two tables that you are joining do not have fields with
								matching names. This is done in two parts:
							

* 

Make sure the fields that you define do not have identical names in the two joined tables.

* 

Set the __serializeObject__ property of the __Telerik.Data.Database__ that you have
										created to *false*. Otherwise, a field will be added to each table, having one and the same name.
									>When joining tables, create, update and delete operations will be performed only on the initial table, specified in the read options.

* 

*Set up create, update and delete operations*. For this purpose, you just need to set the
							__transport.data.dbName__ and __transport.data.tableName__ properties for each operation.
						


 __js__
    


			create: {
				data: {
					dbName: "ProductDB",
					tableName: "Products",
				}
			},
			update: {
				data: {
					dbName: "ProductDB",
					tableName: "Products",
				}
			},
			destroy: {
				data: {
					dbName: "ProductDB",
					tableName: "Products",
				}



* 

*Enable sorting, filtering and paging*. To offload these operations to the __Data Storage__, set the
							__serverSorting__, __serverFiltering__ and __serverPaging__ properties to
							*true*. You can predefine filter and sort expressions, as well as page size and page index and they will be passed to
							the __Data Storage__.
						


 __js__
    


		serverSorting: true,
		serverFiltering: true,




 __js__
    


		sort: { field: "unitPrice", dir: "asc" },
		filter: { field: "unitPrice", operator: "gte", value: 10 },
		pageSize: 10,

>
								Grouping and aggregates cannot be performed by the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Data Storage</legacyBold>, since grouping produces a different output in
								SQLite context. Therefore, you cannot set the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">serverGrouping</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">serverAggregates</legacyBold> properties
								of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> to <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">true</legacyItalic> in this scenario.
							

* 

*Define a model*. In order for most operations to work correctly, you must define a model for your data using the
							__schema.model__. The model must define an id field (__schema.model.id__) if you want to perform
							CRUD operations.
						


 __js__
    


		schema: {
			model: {
				id: 'id',
				fields: {
					id: { editable: false },
					productName: { type: "string" },
					categoryName: { type: "string" },
					unitPrice: { type: "number" }
				}
			}



You can see the entire __DataSource__ definition in the code snippet below.
				


 __js__
    


						var ds = new Telerik.Data.DataSource({
							type: "dataStorage",
							transport: {
								read: { //needed to be able to fetch data
									data: {
										dbName: "ProductDB",
										tableName: "Products",
										joinedTables: [
										{
											destinationTableName: "Categories",
											sourceColumn: "catId",
											destinationColumn: "categoryId"
										}]
									}
								},
								create: { //needed to be able to insert new records
									data: {
										dbName: "ProductDB",
										tableName: "Products",
									}
								},
								update: { //needed to be able to update existing records
									data: {
										dbName: "ProductDB",
										tableName: "Products",
									}
								},
								destroy: { //needed to be able to delete records
									data: {
										dbName: "ProductDB",
										tableName: "Products",
									}
								}
							},
							schema: {
								model: {
									id: 'id', //required for CRUD operations
									fields: {
										id: { editable: false }
									}
								}
							},
							//optionally enable sorting, filtering and paging directly in the database
							serverSorting: true,
							serverFiltering: true,
							serverPaging: true,
							//optional sort and filter expressions
							sort: { field: "unitPrice", dir: "asc" },
							filter: { field: "unitPrice", operator: "gte", value: 10 },
							//optional paging settings
							pageSize: 10,
							page: 2
						});



Now, you can simply assign this __DataSource__ instance to a data-bound __RadControl__, for example __RadGrid__,
				and it will be bound to the data provided by __Data Storage__.
			

# Related Topics

 * [Overview]({{slug:overview}})

 * [Using Data Storage with RadControls]({{slug:using-data-storage-with-radcontrols}})
