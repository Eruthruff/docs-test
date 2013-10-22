---
title: Grouping
meta_title: Grouping
meta_description: description.
slug: 
tags:grouping
publish:True
---


The __DataSource__ component supports local and remote data grouping. You can use the __group__ property to assign one or
				more group expressions to the control. Grouping can also be done on the server (if the remote endpoint supports it) by using the __DataSource__ to
				pass the needed parameters.
			

# groupingDefine Group Expressions

Grouping is configured through the __group__ property that
					accepts an object or an array of objects of the form __{ field: "fieldName", dir: "asc" }__. The options meaning is as follows:
				

* 

__field__: The name of the field by which grouping will be performed.
						

* 

__dir__: the sort order of the created groups.
						

The example below shows a basic grouping scenario.


 __js__
    


				    var myDataSource1 = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://services.odata.org/V3/Northwind/Northwind.svc/Orders",
				                dataType: "json"
				            }
				        },
				        schema: {
				            data: "value"
				        },
				        group: [{ field: "OrderID", dir: "desc" }, { field: "ShipName", dir: "asc" }]
				    });
	
				    myDataSource1.read().then(function () {
				        //data is grouped
				        var data = myDataSource1.view;
				    });



You can also add aggregates to the groups by adding the __aggregates__ property to the group object. It has two
					options:
				

* 

__field__: The name of the field that will be aggregated in the group.
						

* 

__aggregate__: The aggregate function.
							Supported values are *"average"*, *"count"*, *"max"*,
							*"min"* and *"sum"*.
						


 __js__
    


				    var myDataSource2 = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://services.odata.org/V3/Northwind/Northwind.svc/Orders",
				                dataType: "json"
				            }
				        },
				        schema: {
				            data: "value"
				        },
				        group: [
	                        {
	                            field: "ShipCountry",
	                            dir: "desc",
	                            aggregates: [
	                                { field: "ShipCity", aggregate: "count" }
	                            ]
	                        }
				        ]
				    });



# Server Grouping

When bound to remote data, the Boolean __serverGrouping__ property defines how grouping is performed. If the value
					is set to __true__, the __DataSource__ sends group descriptors to the server and expects the grouped data.
					Note that based on the scenario, you may need to use the __transport.parameterMap__ property to
					modify the object that contains the grouping information sent to the remote endpoint. For more information, see the
					[](5764a8ba-3fe5-49dc-9d6c-7248f48939fc) article.
					The default value of the __serverGrouping__ property is *false*, meaning data is grouped
					locally inside the DataSource.
				

# Related Topics

 * [Group Header and Footer Cell Template]({{slug:group-header-and-footer-cell-template}})

 * [Group Aggregates]({{slug:group-aggregates}})
