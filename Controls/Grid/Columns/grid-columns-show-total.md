---
title: Create a Calculated Column
meta_title: Create a Calculated Column
meta_description: description.
slug: 
tags:create,a,calculated,column
publish:True
---


The combination of the rich template support of __RadGrid__ and the public API of the __DataSource__ control allows
				you to implement scenarios with dynamic value calculation in columns. A calculated column is such that is not bound to a field in
				the grid datasource but is populated based on a formula calculation using multiple fields. This is useful in many scenarios, for example, creating a
				shopping list where, based on the price and count of items included, a total sum is calculated. Another example is calculating the net profit of a company,
				based on revenue and expenses. This article will show you how to implement a calculated column in RadGrid with group and total aggregates.
			

# Section1Implementation

Follow these steps to implement a calculated column in RadGrid:

* 

*Define RadGrid.* The declaration can include groups with aggregates and total aggregates. They are used to
							populate the group footers and the grid footer.
						

Following is an example of a single predefined group with listed aggregates. For multiple groups and dynamic grouping, you will need to implement
							more complex calculation logic.
						


 __js__
    


				//defined inside the dataSource options
				group: [{field: 'CategoryID', aggregates:[
					{field: 'ProductName', aggregate: 'count'},
					{field: 'UnitPrice', aggregate: 'sum'},
					{field: 'UnitsInStock', aggregate: 'sum'}
				]}]



The column aggregates are defined as shown below. You just need to define an aggregate object with the name of the field and the aggregate
							function that needs to be used. Such aggregate object must be defined for each field which will be used in the
							__footerTemplate__ property assignment.
						


 __js__
    


				//defined inside the dataSource options
				aggregate: [
					{field: 'ProductName', aggregate: 'count'}
				]



The __footerTemplate__ can then use these aggregates as shown in the following code snippet:
						


 __js__
    


				//defined inside the columns array
				{
					field: 'ProductName', 
					title: 'Product',
					groupFooterTemplate: 'Products in category: #=count#',
					footerTemplate: 'Total Products: #=count#'
				}



Each column can use values from all fields from the current data item to calculate its value. In this case, the calculated column will use the
							UnitPrice and UnitsInStock fields to calculate a total price for all available units. For its cells, this is easily done through the
							__template__ property:
						


 __js__
    


				//defined inside the columns array
				{
					title: 'Total Price', 
					template: '#=Telerik.Utilities.toString(data.UnitPrice*data.UnitsInStock, &quot;c2&quot;)#',
					groupFooterTemplate: '#=TotalColumnExample.getGroupTemplateForTotal(data)#',
					footerTemplate: '#=TotalColumnExample.getTemplateForTotal(data)#',
				}



Since this column is not bound to a field in the __DataSource__, its group and column aggregates cannot be calculated through
							the __DataSource__ directly. Therefore, you need to manually get these aggregates. For this purpose, you can define template functions in
							code for the __footerTemplate__ and __groupFooterTemplate__ properties and implement them in JavaScript. 
							You can see the implementation of these functions in the next steps.
						

Following is the full __RadGrid__ definition that you can use as an example.
						


 __js__
    


				<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: {
				            transport: {
				                read: {
				                    url: 'http://services.odata.org/Northwind/Northwind.svc/Products',
				                    dataType: 'json'
				                }
				            },
				            schema: {
				                data: 'value',
								model: {
									fields: {
										CategoryID: {type: 'number'},
										ProductName: {type: 'string'},
										UnitPrice: {type: 'number'},
										UnitsInStock: {type: 'number'}
									}
								}
				            },
							group: [{field: 'CategoryID', aggregates:[
									{field: 'ProductName', aggregate: 'count'},
									{field: 'UnitPrice', aggregate: 'sum'},
									{field: 'UnitsInStock', aggregate: 'sum'}
							]}],
							aggregate: [
								{field: 'ProductName', aggregate: 'count'}
							]
				        },
						columns: [
							{
								field: 'ProductName', 
								title: 'Product',
								groupFooterTemplate: 'Products in category: #=count#',
								footerTemplate: 'Total Products: #=count#'
							},
							{
								field: 'UnitPrice', 
								title: 'Unit Price', 
								format: '{0:c2}'
							},
							{
								field: 'UnitsInStock',
								title: 'Units in Stock'
							},
							{
								title: 'Total Price', 
								template: '#=Telerik.Utilities.toString(data.UnitPrice * data.UnitsInStock, &quot;c2&quot;)#',
								groupFooterTemplate: '#=TotalColumnExample.getGroupTemplateForTotal()#',
								footerTemplate: '#=TotalColumnExample.getTemplateForTotal()#',
							}
						],
						height: 373
				}">
				</div>



* 

*Calculate the group and column totals.* You can manually calculate the aggregates in the 
							__databinding__ event of __RadGrid__ where the __DataSource__ groups are already 
							created and easy to access. The following logic loops through each group's data items and gets the calculated value. All calculated values are summed 
							in a __sum__ variable which is then added to a __total__ array. The __total__ array 
							is defined globally for the page. Then, aggregates for all groups are summed in the __totalSum__ variable that is also global 
							for the current page.
						


 __js__
    


		var total = []; //used for the group totals
		var totalSum = 0; //used for the grand total of the calculated column
		var groupIndex = 0; //used to manually track the current group




 __js__
    


					var grid = Telerik.UI.to.Grid(document.getElementById("grid1").winControl);
					//the grid datasource is ready
					grid.ondatabinding = function (e) {
						//reset aggregates
						total = [];
						totalSum = 0;
						//get the current data view (with any data operations applied - filtering, sorting, grouping)
						var data = grid.dataSource.view;
						data.forEach(function (item, index) {
							var group = item.field; //we know there is grouping; if grouping is dynamic in your project, first make sure that item.field exists
							var sum = 0;
							//items is an array of the items belonging to the current group (when grouping is applied)
							//if there are multiple levels of grouping, each item in the items collection will have its own items collection
							item.items.forEach(function (product) {
								//calculate the sum for the current group by looping all data items that form it and summing their calculated values
								sum += (product.UnitPrice * product.UnitsInStock);
							});
							total.push(sum);
							//add the current group sum to the grand total for the whole grid
							totalSum += sum;
						});
					};



* 

*Define the template functions*. The function that returns the group footer template needs to be aware of the group it
							is being called for. Therefore, you can manually track the group index by incrementing a __groupIndex__ variable by 1
							each time the template function is called.
						


 __js__
    


		WinJS.Namespace.define("TotalColumnExample", {
			getGroupTemplateForTotal: WinJS.Utilities.markSupportedForProcessing(function () {
				//groups are rendered in the same order that they are ordered in the dataSource.view object
				var sum = total[groupIndex];
				//increase the group index to be in sync when the template function is called for the next group footer
				groupIndex++; 
				return "Total: " + Telerik.Utilities.toString(sum, "c2")
			}),
			getTemplateForTotal: WinJS.Utilities.markSupportedForProcessing(function () {
				return "Grand Total: " + Telerik.Utilities.toString(totalSum, "c2")
			})
		});



If you are going to use the __getGroupTemplateForTotal__ function for more than one column, make sure you add logic that checks if
							the __groupIndex__ variable should be incremented or not. This is needed because in the current implementation the template
							function is called once for each group but if you use the template function for more columns it will be called as many times per group as the number
							of columns that use it is.
						

* 

*(Optionally) Define styles for the footers.* By styling the footers you can highlight the aggregated results. This is easily
							achievable using CSS:
						


 __none__
    


	.k-grid-content .k-group-footer {
		background-color: #e8e0ff;
	}
	
	div.k-grid-footer tr.k-footer-template {
		background-color: #9085c6;
	}
	
	div.k-grid-content .k-alt {
		background-color: #fff;
	}



The image below shows the calculated column and its group and grand totals.![grid-columns-show-total](../Media/Controls\Grid\grid-columns-show-total.png)

# Related Topics

 * [Header and Footer Cell Template]({{slug:header-and-footer-cell-template}})

 * [Group Header and Footer Cell Template]({{slug:group-header-and-footer-cell-template}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Events]({{slug:events}})

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})

 * [Aggregates]({{slug:aggregates}})

 * [Grouping]({{slug:grouping}})
