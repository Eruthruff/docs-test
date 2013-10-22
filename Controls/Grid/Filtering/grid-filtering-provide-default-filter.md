---
title: Provide Default Filtering
meta_title: Provide Default Filtering
meta_description: description.
slug: 
tags:provide,default,filtering
publish:True
---


If your __RadGrid__ is bound to a large set of data and the user would be interested only in a subset of it, at a time, you may provide default 
        filtering to the control on initial load. Furthermore, you can disable the filtering feature and prevent the user from unfiltering.
			

# Providing Default Filter Expressions

You can predefine filter expressions for __RadGrid__ in its dataSource declaration, as shown below.


 __js__
    


					var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						filterable: true,
						dataSource: {
							data: [
								{ Product: "Southwestern Twisted Chips", Price: 6.99 },
								{ Product: "Top Shelf Combo Appetizer", Price: 9.49 },
								{ Product: "Blue Cheese and Hazelnut Shortbread", Price: 10.69 },
								{ Product: "Avocado Feta Salsa", Price: 6.99 },
								{ Product: "Red Cherry Boost", Price: 6.99 },
							],
							schema: {
								model: {
									fields: {
										Product: { type: "string" },
										Price: { type: "number" }
									}
								}
							},
							filter: {
							    logic: "or",
							    filters: [
	                                { field: "Price", operator: "gt", value: 7 },
								    { field: "Product", operator: "contains", value: "Appetizer" }
							    ]
							}
	
						}
					});



If filtering is enabled, the filter values and functions provided in the data source will be shown in the filter items, so the user can modify the already
					defined expressions. If you disable filtering (set __filterable__ to *false*), it will be interpreted
					only at data source level and there will be no visual indication in __RadGrid__.
				

For more information on manual filtering, check this article: [DataSource Filtering](69ac0343-692f-402f-a04d-0d00498f34da).
				

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/ProvidingDefaultFilterExpression*.
        

# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Filtering]({{slug:filtering}})
