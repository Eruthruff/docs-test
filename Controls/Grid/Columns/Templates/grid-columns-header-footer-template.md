---
title: Header and Footer Cell Template
meta_title: Header and Footer Cell Template
meta_description: description.
slug: 
tags:header,and,footer,cell,template
publish:True
---


This help article will show you how to use the __headerTemplate__ and __footerTemplate__ properties of
				RadGrid columns to display customized content in the header and footer cells.
			

# headerHeader Template

If you want to customize the way column titles are displayed or you want to replace them with an icon, a control, etc., you can use the
					__headerTemplate__ property.
				

Note that, when sorting is enabled for RadGrid, whatever content you put in the header cell, a sort action will be triggered upon clicking it. The reason
					behind this is to not break the sort behavior of RadGrid, when using custom column headers.
				

An example of using the header template to customize the title look is shown in the
					*Using a Template for the Header/Footer Cells* example below.
				

# footerFooter Template

You can display aggregated values, based on the entire data source, in the grid footer. To get the aggregated values to show, you need to perform two
					steps:
				

* 

Specify the aggregates in the dataSource. For more information on the syntax, follow [this link](81da975d-5587-4628-aff2-35a77e154a5a).
						

* 

Specify a __footerTemplate__ for the column, for which you have an aggregate calculated. It can be a string or a function
							returning a string. In the binding context you will have the aggregate in a variable named after the aggregate function that you have specified,
							e.g. "average". To better understand this, see the following code snippet where the data source declares aggregates for the "Points" and "Age" fields.
							The first one calculates the sum of all "Points" values. The second will produce the average age of all people listed.
						


 __js__
    


					var gridHeaderTemplate = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						dataSource: {
							data: [
								{ Name: "Peter", Age: 23, Points: 22.6 },
								{ Name: "Mary", Age: 30, Points: 24 },
								{ Name: "Mark", Age: 27, Points: 28.8 }
							],
							aggregate: [
								{ field: "Points", aggregate: "sum" },
								{ field: "Age", aggregate: "average" }
							]
						},
						filterable: true,
						sortable: "multiple, allowUnsort",
						columns: [
							{ field: "Name" },
							{ field: "Age", footerTemplate: "Average participant age: #=Math.floor(average)# " },
							{ field: "Points", headerTemplate: "<span style='color:#336699; font-style: italic'>Points</span>", footerTemplate: "Total sum: #=sum#" }
						]
					});



The result looks like this:![grid-columns-header-footer-template](../Media/Controls\Grid\grid-columns-header-footer-template.png)

# Related Topics
