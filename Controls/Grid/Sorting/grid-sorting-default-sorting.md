---
title: Provide Default Sorting
meta_title: Provide Default Sorting
meta_description: description.
slug: 
tags:provide,default,sorting
publish:True
---


In some cases, you may want to display RadGrid sorted by default. Furthermore, you may want to only apply your initial sorting and not allow the user to
				change it. This help article describes how to achieve such scenario.
			

# Providing Default Sort Expressions

Specifying default sort expressions in RadGrid is done through the __dataSource.sort__ property.
				


 __js__
    


					var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						sortable: "multiple, allowUnsort",
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
							sort: [
								{ field: "Price", dir: "asc" }
							]
	
						},
						columns: [
							{ field: "Product" },
							{ field: "Price", format: "{0:C}" }
						]
					});



If you allow sorting in RadGrid and apply one or more expressions this way, you will again see indications in the UI that the contorl is sorted.
					If you do not want the user to be able to alter the sorting, you can set the __sortable__ property to
					*"none"*. In this case the sorting is interpreted only at the data source level and RadGrid does not display any visual indication
					of being sorted.
				

For more information on manual sorting, check the [Sorting](d55b84e4-bc0f-45d6-827a-0e41d4533a74) article of the
					DataSource control.
				

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/ProvidingDefaultSortExpression*.
        

# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Sorting]({{slug:sorting}})
