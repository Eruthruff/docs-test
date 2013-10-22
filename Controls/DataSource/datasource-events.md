---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of the __DataSource__ component and their most notable event arguments.
			

# eventsEvents

Event Name

Description
								

Arguments
								

__change__

Fires when the underlying data is changed.

__e.target__: The __DataSource__ control instance.
							

__error__

Fires when an error occurs during data retrieval.

__e.target__: The __DataSource__ control instance.
							

__e.errorThrown__: an object containing information about the thrown error. It includes:
								__description__, __message__, __number__ and
								__stack__ properties.
							

__e.status__: a string describing the type of the error.
							

__e.xhr__: The xhr object of the request.
							>
									If <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">schema.errors</legacyBold> is specified and the server response contains that field then the error event will be
									raised. The errors field of the event argument will contain the errors returned by the server.
								

__requestStart__

Fires before a data request to the remote service is made.

__e.target__: The __DataSource__ control instance.
							

__requestEnd__

Fires after a data request to the remote service is made.

__e.target__: The __DataSource__ control instance.
							

__e.requestType__: The type of the request. Could be "create", "read", "update" or "destroy".
							

__e.response__: The response returned by the finished request.
							

In the examples below, the __requestStart__ and __requestEnd__ events are used to inform the user about the data 
          retrieval process by populating a "div" HTML element with messages.
        

You can attach event handlers on initialization, as shown below:


 __js__
    


				    var dataSource = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://services.odata.org/V3/Northwind/Northwind.svc/Employees",
				                dataType: "json"
				            }
				        },
				        schema: {
				            data: "value"
				        },
				        onrequeststart: function (e) {
				            loadingInfo.innerHTML = "Fetching Data ... ";
				        },
				        onrequestend: function (e) {
				            loadingInfo.innerHTML = "Data Fetched!";
				        }
				    });



If you need to add the event handler dynamically, you could assign a handler function, as shown below:


 __js__
    


				    dataSource.onrequeststart = function (e) {
				        var loadingInfo = document.getElementById("loadingInfo");
				        loadingInfo.innerHTML = "Fetching Data ... ";
				    };
	
				    dataSource.onrequestend = function (e) {
				        loadingInfo.innerHTML = "Data Fetched!";
				    };
	
	                // OR
	
				    dataSource.onrequeststart = requestStartHandler;
				    dataSource.onrequestend = requestEndHandler;
	
				    function requestStartHandler(e) {
				        loadingInfo.innerHTML = "Fetching Data ... ";
				    }
	
				    function requestEndHandler(e) {
				        loadingInfo.innerHTML = "Data Fetched!";
				    }



# Related Topics
