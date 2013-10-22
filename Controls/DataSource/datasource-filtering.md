---
title: Filtering
meta_title: Filtering
meta_description: description.
slug: 
tags:filtering
publish:True
---


The __DataSource__ supports filtering its data. This is achieved by assigning it one or more filter expressions. Filtering can be performed
				both automatically by the control and on the server by passing it the filter expressions.
			

# filteringDefine Filter Expressions

To achieve filtering, assign the __filter__
					property of the component an expression in the format __{ field: "fieldName", operator: "eq", value: 12 }__ or an
					array of such expressions. The options meaning is as follows:
				

* 

__field__: The field by which the data source should be filtered.
						

* 

__operator__: The filter function (see the table below) and __value__ is the filter value.
						

* 

__value__: The value to which each field value should be compared.
						

Possible values for the __operator__ field are:
				

Logic

Accepted values

Equal To

__"eq"__, __"=="__, __"isequalto"__,
								__"equals"__, __"equalto"__, __"equal"__

Not Equal To

__"neq"__, __"!="__, __"isnotequalto"__,
								__"notequals"__, __"notequalto"__, __"notequal"__,
								__ne__

Less Than

__"lt"__, __"<"__, __"islessthan"__,
								__"lessthan"__, __"less"__

Less Than Or Equal To

__"lte"__, __"<="__, __"islessthanorequalto"__,
								__"lessthanequal"__, __"le"__

Greater Than

__"gt"__, __">"__, __"greaterthan"__, __"greater"__

Greater Than Or Equal To

__"gte"__, __">="__, __"greaterthanorequalto"__,
								__"greaterthanequal"__, __"ge"__

Starts With

__"startswith"__

Ends With

__"endswith"__

Contains

__"contains"__

Below you can see a basic __DataSource__ filtering definition:
				


 __js__
    


				    var myDataSource = new Telerik.Data.DataSource({
				        data: [
	                        { title: "The Lord of the Rings: The Two Towers", year: 2002 },
	                        { title: "Batman Begins", year: 2005 },
	                        { title: "Inception", year: 2010 }
	                    ],
				        filter: { field: "year", operator: "gt", value: 2003 }
				    });
	
				    myDataSource.read().then(function () {
				        //data is filtered to Batman Begins and Inception
				        var data = myDataSource.view;
				    });



# Define Complex Filter Expressions

To form a more complex filtering expressions, use the __logic__ and __filters__ properties of the
					__filter__. The __logic__ property value must be either *"and"* or
					*"or"* meaning the filter expression will be a logical conjunction or a logical disjunction. The default __logic__
					value is *"and"*. The __filters__ property takes an array of basic filter expressions used for forming the complex
					filter expression.
				

In the example below, the data is filtered to all data entries that have an "year" field value less than *2004* or
					greater than *2006*.
				


 __js__
    


				    var myDataSourceExtended = new Telerik.Data.DataSource({
	                    data: [
	                        { title: "The Lord of the Rings: The Two Towers", year: 2002 },
	                        { title: "Batman Begins", year: 2005 },
	                        { title: "Inception", year: 2010 }
	                    ],
				        filter: {
				            logic: "or",
				            filters: [
	                            { field: "year", operator: "gt", value: 2006 },
	                            { field: "year", operator: "lt", value: 2004 },
	                        ]
				        }
				    });
	
				    myDataSourceExtended.read().then(function () {
				        //data is filtered to The Lord of the Rings and Inception
				        var data = myDataSource.view;
				    });



# Server Filtering

When bound to remote data, the Boolean __serverFiltering__ property defines how filtering is performed. If the value
					is set to __true__, the __DataSource__ sends filter expressions to the server and expects the filtered result. Note that based on
					the scenario, you may need to use the __transport.parameterMap__ property to
					modify the object sent to the remote endpoint. For more information, see the [](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)
					article.
					The default value of the __serverFiltering__ property is __false__, meaning data is filtered locally inside
					the __DataSource__.
				

# Related Topics

 * [Provide Default Filtering]({{slug:provide-default-filtering}})

 * [Implement External Filtering]({{slug:implement-external-filtering}})
