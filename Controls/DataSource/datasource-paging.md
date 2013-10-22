---
title: Paging
meta_title: Paging
meta_description: description.
slug: 
tags:paging
publish:True
---


The __DataSource__ can be used for automatic paging of both local and remote data. You just need to specify the page parameters and the control will fetch
				the corresponding records. There is also an option to use the __DataSource__ to pass parameters for paging on the server by enabling server paging and
				offloading the page operations to the remote server if such exists.
			

# pagingEnable Paging

You can set paging both during initialization, and after the control is initialized. To perform paging during initialization, set the
					__pageSize__ and __page__ properties in the constructor. Their meaning is as follows:
				

* 

__pageSize__: Indicates the number of records to be retrieved for a page of data.
						

* 

__page__: Indicates the current page index.
						


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
				        pageSize: 12,
				        page: 3
				    });
	
				    myDataSource1.read().then(function () {
				        //data is paged
				        var data = myDataSource1.view;
				    });




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
				    });
	
				    myDataSource2.pageSize = 12; //set page size 12
				    myDataSource2.page = 3;      //navigate to page 3  
	                
				    myDataSource2.read().then(function () {
				        //data is paged
				        var data = myDataSource2.view;
				    });



In the above example, the Promise success callback can be used to retrieve the paged data, as well as many
					other data source properties, like __total__ and __totalPages__.
				

# Server Paging

When using remote data binding, the Boolean __serverPaging__ property specifies whether paging parameters
					should be sent to the data source. If __true__, the __DataSource__ sends page size and page index parameters
					and expects the remote endpoint to return the paged data. Note that, based on the scenario, you may need to use the
					__transport.parameterMap__ property to modify the parameters sent to the remote endpoint. For more information,
					see the [](5764a8ba-3fe5-49dc-9d6c-7248f48939fc) article.
					The default value of the __serverPaging__ property is __false__, meaning that
					data is paged internally by the __DataSource__ component.
				

# Related Topics
