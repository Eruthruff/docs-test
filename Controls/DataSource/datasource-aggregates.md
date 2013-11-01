---
title: Aggregates
meta_title: Aggregates
meta_description: description.
slug: 
tags:aggregates
publish:True
---


Using the DataSource component, developers can easily aggregate data and retrieve the results of aggregation. As with other operations, aggregation can
				be performed automatically by the DataSource or the control can be used to pass the needed aggregate descriptors and get the aggregation done on the
				server.
			

# aggregatesDefine Aggregates

The __aggregate__
					property of the component specifies an object or an array of objects that is used to describe the aggregations that need to be made on the next data
					read. These objects should define the following options:
				

* 

__field__: The name of the field that needs to be aggregated.
						

__aggregate__: The aggregate function. Accepted values are: *"average"*,
							*"count"*, *"max"*, *"min"*, and
							*"sum"*.
						

Once the data is read and the aggregates are calculated, the __
						aggregates
					__ property is used to retrieve the result of aggregation
					in the form of a series of nested objects with keys equal to the data fields and aggregate functions.
				


 __js__
    


				    var myDataSource = new Telerik.Data.DataSource({
				        data: [
	                        { orderId: 1, price: 10.23 },
	                        { orderId: 2, price: 14.30 },
	                        { orderId: 3, price: 123.41 },
	                        { orderId: 4, price: 45.10 },
	                        { orderId: 5, price: 45.10 }
	                    ],
				        aggregate: [
	                        { field: "orderId", aggregate: "count" },
	                        { field: "price", aggregate: "sum" }
				        ]
				    });
	
				    myDataSource.read().then(function (data) {
				        //data is aggregated and aggregates can be retrieved
				        var orderIdCount = myDataSource.aggregates.orderId.count;
				        var totalPrice = myDataSource.aggregates.price.sum;
				    });



# Server Aggregates

When bound to remote data, the Boolean __serverAggregates__ property defines how aggregation is performed. If the value
					is set to __true__, the DataSource sends aggregate descriptors to the server and expects the aggregated data as part of the
					result. Note that based on the scenario, you may need to use the __transport.parameterMap__ property to
					modify the aggregation info to the remote endpoint. For more information, see the [](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)
					article.
					The default value of the __serverAggregates__ property is __false__, meaning data is aggregated locally inside the DataSource.
				

# Related Topics
