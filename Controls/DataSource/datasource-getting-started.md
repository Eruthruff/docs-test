---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The __DataSource__ is a data component that serves as an abstraction over local and remote data. Furthermore, it is used to retreive data and maintain its structure,
				in addition to performing sorting, paging, filtering, editing and grouping of data, and calculating aggregates upon it.
			

# prerequisitesPrerequisites for Using the DataSource Control

If you have already taken the steps needed for adding a UI control to the page, you do not need to do anything else to be able to use the
					__DataSource__ component. In case you do not have another Telerik control in the page, follow the steps listed in the following article, apart from those
					used to reference CSS files:
				

[Adding RadControls to a HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# local-dataBinding to Local Data

To create a __DataSource__ instance bound to a local data array, pass the array as the __data__ property
					during initialization.
				


 __js__
    


				    var internetUsers = [{ country: "US", value: 67.96 }, { country: "Mexico", value: 68.93 }];
				    var dataSource1 = new Telerik.Data.DataSource({
				        data: internetUsers
				    });
	
				    dataSource1.read().then(function () {
				        var data = dataSource1.view;
				    });



Alternatively, you can pass the local data array directly as a first argument to the constructor:
				


 __js__
    


				    var internetUsers = [{ country: "US", value: 67.96 }, { country: "Mexico", value: 68.93 }];
				    var dataSource2 = new Telerik.Data.DataSource(internetUsers);
				    
				    dataSource2.read().then(function () {
				        var data = dataSource2.view;
				    });



In this example, the variable, *internetUsers*, is a __DataSource__ instance that is initialized to represent an in-memory
					cache of the *internetUsers* array.
				>
						The data represented is not loaded in the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> until the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.read()</legacyBold> method is called.
					>
						When the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> is a part of a UI control (the dataSource object in all databound RadControls), explicit invocation of the 
						<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">read()</legacyBold> method is
						not needed since the controls do it automatically.
					

# remote-dataBinding to Remote Data

The __DataSource__ provides a flexible API for binding to remote web services that can return data formatted as JSON or XML.
				

To configure remote web service binding, use the __transport__ option during initialization. Below you can see a simple
					example. For full description of how to set remote binding, check this article:
				

[Configuring Remote Binding](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)


 __js__
    


				    var dataSource3 = new Telerik.Data.DataSource({
				        transport: {
				            //use the read option for specifying a location to read data from
				            read: {
				                url: "http://services.odata.org/V3/Northwind/Northwind.svc/Employees",
				                dataType: "json", //specify the type of expected data explicitly
				            }
				        },
				        schema: {
	                        data: "value"
				        }
				    });
				    //when the data is already needed, call read
				    dataSource3.read().then(function () {
				        var data = dataSource3.view;
				    });

>
						Same as with local binding, the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> will not fetch the data until the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">read()</legacyBold> method is called.
					>
						When the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> is a part of a UI control (the dataSource object in all databound RadControls), explicit invocation of the 
						<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">read()</legacyBold> method is
						not needed since the controls do it automatically.
					>
						The <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">transport</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">schema</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">type</legacyBold> properties used with binding to remote
						data can be specified during initialization only. They are read-only after the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> instance is created.
					

For information about the built-in capabilties of the control for working with the assigned data, check the specific articles from the 
					*Other Resources* list
					below.
				

# Related Topics

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})

 * [Configuring Data Editing]({{slug:configuring-data-editing}})

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})

 * [Paging]({{slug:paging}})

 * [Sorting]({{slug:sorting}})

 * [Filtering]({{slug:filtering}})

 * [Grouping]({{slug:grouping}})

 * [Aggregates]({{slug:aggregates}})
