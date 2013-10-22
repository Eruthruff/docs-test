---
title: Configuring Data Editing
meta_title: Configuring Data Editing
meta_description: description.
slug: 
tags:configuring,data,editing
publish:True
---


To enable __Telerik.Data.DataSource__ to perform data editing operations, you need to configure its __schema.model__ and
				__transport__.
			

# Section1Configure the DataSource for remote CRUD (Create, Read, Update, Destroy) data operations

The __DataSource__ is configured for remote CRUD operations, using the __transport.create__, 
          __transport.update__ and __transport.delete__ options. Below you can see the available options and their meaning:
				

__transport.create__ is the configuration used when the __DataSource__ saves newly created data items. Those 
          are items added to the data source via the __add__ or __insert__ methods (these could be called implicitly 
          by a RadControl like __RadGrid__ during editing).
				

__transport.update__ is the configuration used when the data source saves updated data items. Those are data items whose fields have
					been updated.
				

__transport.destroy__  configuration used when the data source destroys data items. Those are items removed from the data source via
					the __remove__ method (it could be called implicitly by a RadControl like __RadGrid__ during editing).
				

These properties accept a *string*, an *Object* or a *function* as a
					parameter:
				

* 

If the value is a *function* the data source invokes that function
							instead of making an AJAX call.
						

* 

If the value is a *string* the data source uses this string as the
							URL of the remote service.
						

* 

If the value is an *Object* the properties listed below will be recognized.

The available options that can be passed via the Object parameter are:
				

* 

__contentType__: The content-type HTTP header sent to the server. Default is *"application/x-www-form-urlencoded"*.
						

* 

__data__: Additional parameters which are sent to the remote service.
						

* 

__dataType__: The type of result expected from the server. Commonly used values are *"json"*
              and *"xml"*. Make sure you set this property for all requests to external data sources.
						

* 

__type__:The type of request to make (*"POST"*, *"GET"*, 
              *"PUT"* or *"DELETE"*), default is *"GET"*.
						

* 

__url__: The URL to which the request is sent. If set to function the data source will invoke it and use the result as
							the URL.
						

For more information on the above options, check the [jQuery.ajax() documentation](http://api.jquery.com/jQuery.ajax/).
				

A sample definition of a __DataSource__ configured for editing is shown below:
				


 __js__
    


				    var dataSource = new Telerik.Data.DataSource({
				        transport: {
				            read: "http://myapi.mysite.com/Products",
				            update: {
				                url: "http://myapi.mysite.com/Products/Update",
				                type: "POST"
				            },
				            destroy: {
				                url: "http://myapi.mysite.com/Products/Destroy",
				                type: "POST"
				            },
				            create: {
				                url: "http://myapi.mysite.com/Products/Create",
				                type: "POST"
				            }
				        }
				    });



# Configure the Data Model

For the __DataSource__ to work correctly with data items, distinguish them and treat their fields with accordance to their actual
					data type, you need to define a model. This is done through the __schema.model__ property. The available options are:
				

* 

__id__: The name of the field which acts as an identifier of the model. The field is expected to have unique values.
							The __id__ must be set in order for automatic editing capabilities in RadControls like __RadGrid__ to work.
						

* 

__fields__: A set of key/value pairs that configure the model fields. The key specifies the name of the field. Quote the
							key if it contains spaces or other symbols which are not valid for a JavaScript identifier.
						

* 

__defaultValue__: Specifies the value which will be used for the field when a new model instance is created. Default settings
							depend on the type of the field. Default for "string" is *""*, for "number" is *0* and 
              for "date" is *new Date()* (today).
						

* 

__editable__: Specifies if the field is editable or not. The default value is *true*.
						

* 

__nullable__: Specifies if the __defaultValue__ setting should be used. The default is 
              *false*.
						

* 

__parse__: Specifies the function which will parse the field value. If not set default parsers will be used.
						

* 

__type__: Specifies the the type of the field. The available options are *"string"*, 
              *"number"*, *"boolean"*, *"date"*.
							The default is *"string"*.
						

* 

__validation__: Specifies the validation options which will be used.
						

An example model declaration is shown below (For the purposes of the example, the __transport__ property setup is omitted):


 __js__
    


				    var dataSource = new Telerik.Data.DataSource({
				        //..
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
				                        validation: { //set validation rules
				                            required: true
				                        }
				                    },
				                    UnitPrice: {
				                        //data type of the field {Number|String|Boolean} default is String
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

>
            The <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">transport</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">schema</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">type</legacyBold> properties used with binding to
            remote data can be specified during initialization only. They are read-only after the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> instance is created.
          

# Related Topics
