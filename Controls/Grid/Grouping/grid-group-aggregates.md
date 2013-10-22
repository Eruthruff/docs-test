---
title: Group Aggregates
meta_title: Group Aggregates
meta_description: description.
slug: 
tags:group,aggregates
publish:True
---


To present summaries about the data in each group, you can take advantage of the group aggregates feature, which allows you to specify aggregate fields and
				functions and then display the results in the group footer of each column.
			

There are two main scenarios for setting aggregates—when you have pre-defined grouping and when you allow the drag-to-group feature (setting
				__groupable__ to *true*). The steps for each scenario are listed below.
			

# Showing Aggregates with Predefined Groups

* 

Set the group(s) in the dataSource as shown in the first section of this article.

* 

Expand the object(s) inside the __group__ array to also list aggregates in the following form:
						

	
							group: {
								field: "UnitsInStock", aggregates: [
									{ field: "ProductName", aggregate: "count" },
									{ field: "UnitPrice", aggregate: "sum"},
									//.....
								]
							}
						



where the __aggregates__ object contains aggregate definitions for all fields that you want to show summarized data for.
						

* 

In the __columns__ definition of the grid, add a __groupFooterTemplate__ to each column, where you can
							evaluate the result of the already defined function, e.g. "Total number: "#=count#".
						


 __js__
    


					var aggregateGrid1 = new Telerik.UI.RadGrid(document.getElementById("grid3"), {
						dataSource: {
							data: People.generatePeople(20),
							group: {
								field: "City", aggregates: [
									{ field: "FirstName", aggregate: "count" }
								]
							}
						},
						columns: [
	                        { field: "FirstName", title: "First Name", groupFooterTemplate: "Total employees in group: #=count#" },
	                        { field: "LastName", title: "Last Name" },
							{ field: "Title", title: "Position" },
							{ field: "City" }
						],
						height: 320
					});

![grid-grouping 4](../Media/Controls\Grid\grid-grouping_4.png)

# Showing Aggregates with Enabled Drag-to-group Feature

When the groups in RadGrid can change dynamically, you need to make sure that you define the aggregates you will need in all grouping scenarios. Follow these
					steps:
				

* 

In the __dataSource__, set the __aggregate__ property to an array of objects defining all needed aggregates.
						

* 

In the __columns__ definition of the grid, add an __aggregates__ property and set it to
							an array of all needed aggregate functions for the current column. Make sure that you have consistency between the aggregates listed in the
							dataSource and those listed in each column.
						

* 

Again in the __columns__ definition of the grid, add a __groupFooterTemplate__ to each column, where you can
							evaluate the result of the already defined function(s), e.g. "Total number: "#=count#, total price: #=sum#".
						


 __js__
    


					var aggregateGrid2 = new Telerik.UI.RadGrid(document.getElementById("grid4"), {
						dataSource: {
							data: People.generatePeople(20),
							//can be a single object, without the square brackets
							aggregate: [
								{ field: "FirstName", aggregate: "count" }
							]
						},
						groupable: "enabled",
						columns: [
	                        { field: "FirstName", title: "First Name", aggregates: ["count"], groupFooterTemplate: "Total employees in group: #=count#" },
	                        { field: "LastName", title: "Last Name" },
							{ field: "Title", title: "Position" },
							{ field: "City" }
						],
						height: 320
					});



# Related Topics
