---
title: Sorting
meta_title: Sorting
meta_description: description.
slug: 
tags:sorting
publish:True
---


The __DataSource__ component can perform sorting when bound to local or remote data. Using the __sort__ property you can pass
				one or multiple sort expressions. There is also an option to use the __DataSource__ to pass parameters for sorting on the server by enabling server
				sorting and sending the required parameters.
			

# sortingDefine Sort Expressions

The __sort__ property is set when sorting needs to be applied to the data. The property can contain either an object with format
					__{ field: "fieldName", dir: "asc" }__, or an array of objects with the same format for specifying multiple
					sort expressions. The meaning of the __sort__ property options is as follows:
				

* 

__field__: The name of the field that needs to be sorted.
						

* 

__dir__:  The sort direction. Accepted values are: *"asc"* for ascending and
							*"desc"* for descending.
						


 __js__
    


				    var myDataSource = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://services.odata.org/V3/Northwind/Northwind.svc/Employees",
				                dataType: "json"
				            }
				        },
				        schema: {
				            data: "value"
				        },
				        sort: [
	                        { field: "LastName", dir: "desc" },
	                        { field: "FirstName", dir: "asc" }
				        ]
				    });
	
				    myDataSource.read().then(function () {
				        //data is sorted
				        var data = myDataSource.view;
				    });



# Server Sorting

When binding to remote data, the __serverSorting__ Boolean property can be used to specify how data is sorted.
					If set to __true__, the __DataSource__ sends the sort expressions to the remote endpoint and expects the sorted
					data back. Note that based on the scenario, you may need to use the __transport.parameterMap__ property to
					modify the array of expressions sent to the remote endpoint. For more information, see the [](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)
					article.
					The default value of the __serverSorting__ property is *false*, meaning data is sorted locally, by the
					__DataSource__ itself.
				

# Related Topics
