---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---
Make a change here.

The Telerik Data Storage ships in a separate installation from the RadControls for Windows 8 HTML suite. This article will explain how to add the Data
				Storage reference to your application and then, how to use it to build data-oriented applications.
			

* 

[Installing the Data Storage](#installation)

* 

[Referencing the Data Storage in Your Project](#references)

* 

[Using the Data Storage in JavaScript/HTML projects](#using)

* 

[Create a Database](#create)

* 

[Populate the Database](#populate)

* 

[Syncing Changes and Closing the Database Connection](#syncing)

* 

[Update Data in the Database](#update)

* 

[Removing Records from the Database](#removing)

* 

[Select Data from the Database](#select)

* 

[Getting a Scalar Value from the Database](#scalar)

* 

[Demo Application](#demo)

# installationInstalling the Data Storage
Make another change here.
To be able to install the Telerik Data Storage, you need to separately download its installation from your account. To do this, follow the steps
					below:
				

* 

Go to your [Telerik account](http://www.telerik.com/account/).
						

* 

Click on the __Products & Subscriptions__ link and then click the DevCraft Ultimate link or
							the Windows 8 product link.
						

* 

On the next page click the __Download Installer and other resources__ button.
						

* 

Locate __RadControls for Windows 8__ in the displayed list of products and click the __
								Browse all
								product files
							__ link.
						

* 

From the displayed list, click on __HTML Data Storage__ at the bottom of the list which will download a .zip file with the
							Data Storage SDK, an example application and short documentation.
						

* 

Extract the archive and run __Telerik.Storage.HTML.vsix__ to install the SDK.
						

# referencesReferencing the Data Storage in Your Project

To add the Telerik Data Storage to an app, do the following:

* 

Once the Data Storage SDK is installed, you can open a new or existing project, right-click the __References__ folder and select
							__Add Reference__ from the context menu.
						

* 

In the __References__ dialog select __Telerik Data Storage for Windows 8 HTML__. Note that this will automatically add a reference to
							__Microsoft Visual C++ Runtime Package__. This SDK is needed because the Telerik Data Storage runs native C++ code.
						

* 

In the <head> tag of the current page, add the following reference:

	
							<script src="///Telerik.Storage.HTML/js/Telerik.Data.js"></script>
						

>
						To deploy an application successfully on any machine, you must select the right Solution Platform since the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Data Storage</legacyBold>
						component uses native code that is CPU architecture dependent and must be rebuilt for all architectures (x86, ARM, x64). To do this, you need to
						open the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Configuration Manager</legacyBold> dialog that is accessible from <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Build\Configuration Manager...</legacyItalic>
						menu item of Visual Studio 2012. You must ensure that all projects in your solution use the same platform.
					>
						When you publish your application in the Windows Store, you need to build and deploy .appx packages for all platform configurations. This is the common
						requirement for all Windows Store applications that use native components. For more information, read this article on MSDN:
						<externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>Creating an app package</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh975357.aspx</linkUri></externalLink>.
					

# usingUsing the Data Storage in JavaScript/HTML projects

The lightweight JavaScript wrapper library over Telerik’s Data Storage engine defines the __Telerik.Data__ namespace. In this
					namespace, developers can apply CRUD operations using the __Database__ object, that tracks the internal state of the database and
					persisted data. The following steps are required in order to create a database and apply CRUD operations to it:
				

# createCreate a Database

You can create a database calling the __open(databaseName, location)__ static method of the Database class, passing the name
							and the location of the database. Possible locations for database file are : *"local"*, *"roaming"*
							and *"temporary"*. These locations correspond to the three data stores in Windows Store applications. For more information
							on the subject, go to [Managing application data](http://msdn.microsoft.com/en-us/library/windows/apps/hh465109.aspx).
						

	
							var db = Telerik.Data.Database.open("MyDBName", "roaming" );
						



This will create a new database in the roaming data store. If the database name matches an existing database, it will be opened.

# populatePopulate the Database

To insert tables in the database and rows into these tables, use the __insert(tableName, object)__ method.
							__tableName__ here stands for the string name of the table into which you want to insert the object. The method will
							create a table with the given name that will hold the object's data, passed as a second parameter.
							The only requirement for the objects used for table creation is the field with name *"id"* that keeps an integer value.
							This will be the primary key of this table.
							If the
						

	
							var person = { firstName: "Hardy", age: 12, inserted: new Date(), id: 1 };
							db.insert("persons", person);
						



As a result of this example a new table with name "persons" and fields "firstName", "age", "inserted" and "id" will be created.
						

It is a usual practice to persist a collection of objects, one by one, by calling the __insert__ method of the database
							multiple times.
						

# syncingSyncing Changes and Closing the Database Connection

In order to persist changes into the database, the asynchronous method __sync()__ should be called as follows:
						

	
							db.sync(); //call this to apply any CRUD operations done on the database
						



All the changes applied to the database should be finalized by calling the __close()__ method. Its invocation aborts
							any pending operations and release all unmanaged resources, associated with the database object. This method is necessary especially in case of
							error handling.
						

	
							db.close(); //release all unmanaged resources
						



It is a good practice to combine the __sync()__ and the __close()__ methods as follows:
						

	
							db.sync().then(function () {
							db.close();
							});
						



# updateUpdate Data in the Database

To update data from an existing record, call the __update(tableName, data)__ method. The first argument it accepts is
							the name of the table to update and the seconds—the updated data record. The Data Storage matches the passed object with the corresponding row in
							the database using its id.
						

	
							var person={ firstName: "Hardy", age:12, inserted: new Date(), id: 1 };
							db.update("persons", person);
							db.sync().then(function () {
							db.close();
							});
						



This logic will find the item with id=1 in the "persons" table and will apply the new values to it. Then, the changes will be synced and the
							database connection will be closed.
						

# removingRemoving Records from the Database

To remove an existing record, use the __remove(tableName, data)__ method. It accepts as first argument the name of the
							table from which you are going to delete a record. The second parameter can be:
						

* 

The id of the record to be deleted.

* 

The whole data object, containing the id value.

	
							var person = { firstName: "Hardy", age: 12, inserted: new Date(), bool: true, id: 1 };
							db.remove("persons", { id: 1 });
							//or
							db.remove("persons", person);

							db.sync().then(function () {
							db.close();
							});
						



Both lines using the __remove__ method will remove the record with id=1 from the "persons" table.
						

# selectSelect Data from the Database

To select the appropriate data from the database use the __query(sqlStatement, parameter)__ asynchronous method. The
							__sqlStatement__ is a string parameter, containing an SQL statement. __parameter__ is optional and
							must be an array of values that will be used as paramaters in the query.
						

	
							db.query("select * from persons").then(function (result) {
							//do something with the result object
							db.close();
							});

							//apply parameterized query
							db.query("select * from persons as x where x.id = @p1", [1]).then(function (result) {
							//do something with returned result list
							db.close();
							});
						



The first query returns the entire persons table data. The second query returns a single record from the persons table that has an id=1.

In order to prevent the application from a crash, use the Promise.done() method for error handling as follows:

	
							db.query("select * from persons").done(function (result) {
							//changes are persisted successfully
							//todo : do something with result object
							db.close();
							}, function (error) {
							if (error && error.message) {
							//todo: handle error according to the error object content
							db.close();
							}
							});

						



Note that for most scenarios using the fluent API of Data Storage. It guides you through all operations used for data selection and is easier
							to read and maintain. To learn more about performing read operations using Data Storage's fluent API, go to: 
							[Read Operations](e8255ea7-4da1-41fc-91a1-9401cef081a2).
						

# scalarGetting a Scalar Value from the Database

To execute a statement that returns a scalar value as a result of an aggregation operation use the __queryScalar(scalarSQL)__
							asynchronous method. __scalarSQL__ is an SQL query that returns a scalar result (e.g. count) or no result.
						

	
							db.queryScalar("select count(*) from persons").then(function (result) {
							//do something with scalar result
							db.close();
							});

							db.queryScalar("drop table persons").then(function () {
							db.close();
							});
						



# demoDemo Application

To see the Telerik Data Storage at work, you can run the demo application that ships with it (you will find it in the installation archive). There you will
					see different RadControls bound to data from the Data Storage, including a RadGrid with an external edit form.
				

Make sure you check the ReadMe.txt file before you try to run the application.

# Related Topics
