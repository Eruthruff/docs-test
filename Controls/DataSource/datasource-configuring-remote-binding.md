---
title: Configuring Remote Binding
meta_title: Configuring Remote Binding
meta_description: description.
slug: 
tags:configuring,remote,binding
publish:True
---


The main settings needed for binding the __DataSource__ control to remote data are contained in the __DataSource.transport__ and
				__DataSource.schema__ options. They are responsible for:
			

* 
__transport__: Specifies the settings for loading and saving data. This can be a remote or local/in-memory data. It
						includes specifying the URL of the source of data, the parameters to pass, the expected data type, etc. In other words, these are the settings to use
						for retrieving the data.
					

* 
__schema__: Responsible for describing the raw data format, or in other words, settings for processing the raw
						data, once it is retrieved. These include: specifying the field from the response containing the data items of interest or the groups of data items,
						specifying the field containing aggregates for the data, and providing a model for the returned data.
					

There is a third property related to remote data retrieval, that you may find useful when working with OData services—the __type__
				one which can be used to specify a predefined type of transport. Currently, only *"odata"* is supported as a value.
			

# data-transportConfiguring Data Transport

# Overview

To configure remote web service binding, use the __transport__ option during initialization.
						


 __js__
    


				    var dataSource = new Telerik.Data.DataSource({
				        transport: {
				            //use the read option for specifying a location to read data from
				            read: {
				                url: "http://search.twitter.com/search.json",
				                dataType: "json", //explicitly specify the expected format of the data
				                data: {
				                    //specify additional data to be sent to the remote service
				                    //value can also be a function that returns the actual value to be sent
				                    q: "telerik"
				                }
				            }
				        }
				    });

Once the __DataSource__ has been created with transport options, calling the __read()__ method will
							cause the component to make a web request to the remote service. The __read()__ method is asynchronous
							and returns a __WinJS.Promise__ object that can be used to wait for the returned result.
						>
								Note that the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">read()</legacyBold> method is automatically called when the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> is bound to a RadControl and there
								is no need to call it, unless the RadControl is initialized with the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">autoBind</legacyBold> property set to
								<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">false</legacyItalic>. The only cases when the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">read()</legacyBold> method should be called are when the
								<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">autoBind</legacyBold> property is set to <legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">false</legacyItalic> or when the data from the
								<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> will be used outside of a RadControl.
							


 __js__
    


				    //use the then() callback of the Promise object returned from read()
				    dataSource.read().then(function () {
				        //use data here
				        var data = dataSource.view;
				    });



# Properties
Here is a description of the transport options.

The __parameterMap__ property of the transport object can be specified for modifying the parameters
							that are sent to the remote endpoint. It is often used to encode the parameters in JSON format. Add text here. The property expects a
							function with a single options parameter. The parameter should contain key/value pairs that represent the request.
							One or more of the following keys will be present (depending on the configuration and current request type):
						

* 

__aggregate__: An object containing the current aggregate info. 
								

* 

__group__: An object containing the current filter info. Present if the data source is grouped and
									__serverGrouping__ is set to true.
								

* 

__filter__: An  object containing the current filter info. Present if the data source is filtered and
									__serverFiltering__ is set to true.
								

* 

__page__: The current page. Present if __serverPaging__ is set to true.
								

* 

__pageSize__: The current page size. Present if __serverPaging__ is set to true.
								

* 

__skip__: a A number indicating how many records to skip from the beginning (related to the current page).
									Present if __serverPaging__ is set to true.
								

* 

__sort__: An array containing the current sorting info. Present if the data source is sorted and
									__serverSorting__ is set to true.
								

* 

__take__: The same as pageSize. Present if __serverPaging__ is set to true.
								

The function should return another
							object, whose keys specify the parameter names and the values that are sent.
						


 __js__
    


				    var myDataSource = new Telerik.Data.DataSource({
				        transport: {
				            parameterMap: function (options) {
				                return {
				                    pageIndex: options.page,
				                    size: options.pageSize,
				                    //calls a custom function to convert to another format
				                    orderBy: convertSort(options.sort)
				                }
				            }
				        }
				    });



To be able to read data from the remote service, you should configure the __read__ set of options of the transport object, namely:
						
Some content here.
* 

__cache__: a boolean property indicating whether the browser should cache the requested pages.
								

* 

__contentType__: represents the content-type HTTP header sent to the server.
								

* 

__data__: The data to be sent to the server. For more information see the [jQuery.ajax](http://api.jquery.com/jQuery.ajax/) documentation.
								

* 

__dataType__: The type of data that you're expecting back from the server. For example, "json".
								

* 

__type__: The type of request to make ("POST", "GET", "PUT" or "DELETE"), default is "GET".
								

* 

__url__: The remote URL to call when retrieving new data.
								


 __js__
    


				    var dataSource1 = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://api.geonames.org/wikipediaSearchJSON",
				                data: {
				                    q: "bulgaria",
				                    username: "demo"
				                },
				                cache: false
				            }
				        },
				        schema: {
				            data: "geonames"
				        }
				    });



Additionally to __transport__, the __type__ property of the __DataSource__ can be used to
							specify a predefined type of transport. Currently, only __"odata"__ is supported.
						


 __js__
    


				    var dataSource2 = new Telerik.Data.DataSource({
				        type: "odata",
				        transport: {
				            read: "http://odata.netflix.com/Catalog/Titles"
				        }
				    });



# describing-dataDescribing fetched data

When binding to remote data, the __schema__ property is used to describe the raw data returned from the source.
					It exposes the following options:
				

* 

__aggregates__: specifies the field from the response which contains the aggregate results.
							If set to a function - the function will be called to return the aggregate results for the current response, e.g:
						


 __js__
    


				        schema: {
				            aggregates: "aggregates" // aggregate results are returned in the "aggregates" field of the response
				        }




 __js__
    


				        schema: {
				            aggregates: function(response) {
				                return response.aggregates;
				            }
				        }



The valid aggregate results should look like this:
						


 __js__
    


				        {
				            fieldName: {
				                functionName1: functionValue1,
				                functionName2: functionValue2
				            }
				        }




 __js__
    


				        {
				            unitsInStock: {
				                count: 2000
				            },
	
				            unitPrice: {
				                max: 250,
				                min: 20
				            }
				        }



* 

__data__: Specifies the field from the response which contains the data items. If set to a function -
							the function will be called to return the data items for the current response.
						


 __js__
    


				        schema: {
				            data: "items" // data items are returned in the "items" field of the response
				        }




 __js__
    


				        schema: {
				            data: function(response) {
				                return response.items;
				            }
				        }



* 

__errors__: Specifies the field from the response which contains any errors. If set to a function - the function will be
							called to return the errors for the current response (if present). If there are any errors the error event of the __DataSource__ will be raised.
						


 __js__
    


				        schema: {
				            errors: "exceptions" // errors are returned in the "exceptions" field of the response
				        }




 __js__
    


				        schema: {
				            errors: function(response) {
				                return response.errors;
				            }
				        }



* 

__groups__: Specifies the field from the response which contains the groups. If set to a function - the function will be called to
							return the groups for the current response.
							Used instead of the __schema.data__ setting if remote grouping operation is executed.
						


 __js__
    


				        schema: {
				            groups: "groups" // errors are returned in the "exceptions" field of the response
				        }




 __js__
    


				        schema: {
				            groups: function(response) {
				                return response.groups;
				            }
				        }



The returned groups should conform to the following format:


 __js__
    


				        [{
				            aggregates: {
				                field1Name: {
				                    function1Name: function2Value,
				                    function2Name: function2Value
				                },
				                field2Name: {
				                    function1Name: function1Value
				                }
				            },
				            field: fieldName, // the field name on which is grouped
				            hasSubgroups: true, // false if there are not sub group items and this is the top most group
				            items: [
	                        // either the inner group items (if hasSubgroups is true) or the data records
	                        {
	                            aggregates: {
	                                //nested group aggregates
	                            },
	                            field: nestedGroupFieldName,
	                            hasSubgroups: false,
	                            items: [
	                            // data records
	                            ],
	                            value: nestedGroupValue
	                        },
	                        //nestedgroup2, nestedgroup3, etc.
				            ],
				            value: value // value of the field on which is grouped
				        }
	                    // group2, group3, etc.
				        ]



* 

__model__: Describes the Model of the __DataSource__, which provides the ability to define schema for the fields. You can add validation
							to them, specify which ones are editable, nullable, etc. For example:
						


 __js__
    


				    var dataSource = new Telerik.Data.DataSource({
				        schema: {
				            model: {
				                id: "ProductID",
				                fields: {
				                    ProductID: {
				                        //this field will not be editable (default value is true)
				                        editable: false,
				                        // a defaultValue will not be assigned (default value is false)
				                        nullable: true
				                    },
				                    ProductName: {
				                        validation: {
				                            //set validation rules
				                            required: true
				                        }
				                    },
				                    UnitPrice: {
				                        //data type of the field {Number|String|Boolean|Date} default is String
				                        type: "number",
				                        // used when new model is created
				                        defaultValue: 42,
				                        validation: {
				                            required: true,
				                            min: 1
				                        }
				                    }
				                }
				            }
				        }
				    });



* 

__parse__: The name of a function which will be executed before the server response is
							used. Appropriate for preprocessing or parsing of the server response.
						


 __js__
    


				        schema: {
				            parse: function(response) {
				                // perform some processing over the response
				                return processResponse(response);
				            }
				        }



* 

__total__: The field from the response which contains the total number of data items. If set to a function -
							the function will be called to return the total number of data items for the current response. If not specified
							the length of the Array returned by __schema.data__ will be used.
						


 __js__
    


				        schema: {
				            total: "count" // total number of data items is returned in the "count" field of the response
				        }




 __js__
    


				        schema: {
				            total: function (response) {
				                return response.items.length;
				            }
				        }



* 

__type__: Specifies the response - *"xml"* or *"json"*. The default value is 
              *"json"*.
						


 __js__
    


				        schema: {
				            type: "xml"
				        }

>
						The <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">transport</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">schema</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">type</legacyBold> properties
						can be specified during initialization only. They are read-only after the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> instance is created.
					

# Related Topics
