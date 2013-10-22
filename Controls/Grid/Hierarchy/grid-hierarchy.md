---
title: Declarative Hierarchy
meta_title: Declarative Hierarchy
meta_description: description.
slug: 
tags:declarative,hierarchy
publish:True
---


RadGrid allows you to present hierarchical data through a convenient visual structure. You can take advantage of the automatic hierarchy feature of the grid
				that will generate detail tables based on declarative relations that you specify.
			

# Using Declarative Relations

In this case, you need to have two tables of data containing a field that could be used to match one row from the first table to one or more rows from the
					second. The implementation is quite easy and intuitive. You need to follow these simple steps:
				

* 

Declare the parent grid, as normal—dataSource, columns, etc.

* 

In the parent grid constructor, define a __detailTable__ option, which on its turn receives an object as value.
						

* 

This object should contain a __dataSource__ definition, and a __parentRelation__. The parent
							relation is used to link a parent record to its children and populate a detail table with them. This relation contains two properties:
						

* 

__masterField__: The field in the parent grid's data source which is used to connect it with the child records.
								

* 

__detailField__: The name of the field in the child table's data source.
								

If needed, you can provide additional settings for columns, sorting, selection, child tables, etc. Note that any features enabled in the master
							table will not be transferred to the detail ones, so you should set them separately in the detailTable definition.
						

Following is a sample implementation following these steps.


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: Sample.categories,
						columns: [
	                        { field: "ID", width: 40 },
	                        { field: "Name", title: "Category" }
						],
						detailTable: {
							dataSource: Sample.data,
							parentRelation: {
								masterField: "ID",
								detailField: "CategoryID"
							},
							columns: [
	                            { field: "ID", width: 40 },
	                            { field: "Name" },
	                            { field: "Price" }
							]
						}
					});



For a better image of the scenario, the data used in the example is defined, as shown below:


 __js__
    


		var data = [
	        { "ID": 0, "Name": "Bread", "Price": "2.5", "CategoryID": 0 },
	        { "ID": 1, "Name": "Milk", "Price": "3.5", "CategoryID": 1 },
	        { "ID": 2, "Name": "Vint soda", "Price": "20.9", "CategoryID": 1 },
	        { "ID": 3, "Name": "Havina Cola", "Price": "19.9", "CategoryID": 1 },
	        { "ID": 4, "Name": "Fruit Punch", "Price": "22.99", "CategoryID": 1 },
	        { "ID": 5, "Name": "Cranberry Juice", "Price": "22.8", "CategoryID": 1 },
	        { "ID": 6, "Name": "Pink Lemonade", "Price": "18.8", "CategoryID": 1 },
	        { "ID": 7, "Name": "DVD Player", "Price": "35.88", "CategoryID": 2 },
	        { "ID": 8, "Name": "LCD HDTV", "Price": "1088.8", "CategoryID": 2 },
			{ "ID": 9, "Name": "Soup", "Price": "10.5", "CategoryID": 0 },
			{ "ID": 10, "Name": "Cake", "Price": "7.5", "CategoryID": 0 },
			{ "ID": 11, "Name": "Surface Tablet", "Price": "499 ", "CategoryID": 2 }
		];
	
		var categories = [
	        { ID: 0, Name: "Food" },
	        { ID: 1, Name: "Beverages" },
	        { ID: 2, Name: "Electronics" }
		];
	
		WinJS.Namespace.define("Sample", {
			data: data,
			categories: categories
		});



This is how the grid will look like when a parent item is expanded:![grid-declarative-hierarchy](../Media/Controls\Grid\grid-declarative-hierarchy.png)

# Related Topics
