---
title: Rows
meta_title: Rows
meta_description: description.
slug: 
tags:rows
publish:True
---


RadGrid rows represent a single record in the control's data source. By default, rows consist of cells, each holding a single value from the associated record.
			

In terms of styling, there are two types of rows in RadGrid - *rows* and *alternating rows*.
				Alternating rows are those placed at an odd index in the control table (0-based indexing). For better visualization of data, alternating rows have a background color
				that contrasts with the main grid background.
			

Rows in RadGrid are highly customizable—you can provide them with templated content in two ways:

* 

by providing cell templates through the column definitions ( since
						cells are the intersection between a column and a row in tabular component like RadGrid). For more information, read the
						[Column Templates](e3c17ab8-400d-48d9-ae60-8bfcd5d87030) help article.
					

* 

by providing a template for the entire row. To learn how to do this, read until the end of this article.

# Using Templates in Grid Rows

Providing a template for a grid row is similar to providing the different templates in columns—you can assign either a string or a function
					returning a string as a template. A data context, containing the whole data item, corresponds to the current row.
				

You can use two templates for grid rows—__rowTemplate__ and __altRowTemplate__. When you do not need a
					different look for rows and alternating rows, you can assign a value only to the __rowTemplate__ property. The
					__altRowTemplate__ should be used only in scenarios where the alternating rows need to be distinguished.
				

The following example demonstrates how to use row templates.


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Employees",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						},
						columns: [{ title: 'Person Info' }, { title: 'Job Info' }],
						rowTemplate: Rows.rowTemplate,
						altRowTemplate: Rows.altRowTemplate,
						height: 700
					});




 __js__
    


	WinJS.Namespace.define("Rows", {
		rowTemplate: function (item) {
			var firstCell = ["<td><div class='pItem'>",
			"<img src='http://demos.telerik.com/aspnet-ajax/salesdashboard/Images/" + item.FirstName + "_" + item.LastName + ".png' />",
			 item.FirstName + " " + item.LastName,
			 "</div><div class='notes'>" + item.Notes + "</div></td>"].join("");
	
			var secondCell = ["<td><p>Position: " + item.Title + "</p>",
			"<p>Works in: " + item.City + ", " + item.Country + "</p>",
			"<p>Extension: " + item.Extension + "</p></td>"].join("");
	
			var template = "<tr>" + firstCell + secondCell + "</tr>";
			return template;
		},
	
		altRowTemplate: function (item) {
			//get the regular template content
			var template = Rows.rowTemplate(item);
			//set the different class name for alt rows
			template = template.replace("<tr", "<tr class='altRow'");
			return template;
		}
	});




 __none__
    


	.pItem {
		color: #ccfa00;
	}
	
	.notes {
		font-style: italic;
	}
	
	.altRow {
		background-color: #303030;
	}



The resulting grid layout is shown here:![grid-row-template](../Media/Controls\Grid\grid-row-template.png)>
						The content of the template should be defined inside a TR element because RadGrid renders its data in a TABLE element and
						each row should be represented by a TR element with at least one cell (TD) defined inside it.
					

# Related Topics
