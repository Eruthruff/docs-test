---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


RadGrid offers rich grouping functionality, supporting drag-to-group, predefined groups, aggregates, plus group header and footer templates. This help article
				will introduce you to the main scenarios of grouping in RadGrid.
			

# Enabling Grouping

To allow/disallow the user the ability to perform grouping in RadGrid, you just need to set the __groupable__ property to a string
					value enabling the behavior that best fits your scenario. The values recognized by RadGrid are:
				

Value

Meaning

__none__

Grouping is disabled. This is the default value.

__enabled__

The end user can drag column headers to a specifically designed grouping panel (see below) to perform grouping by the column field. Pre-defining
								groups in the data source is also allowed. Group headers are scrolled together with the grid rows.
							

__staticHeaders__

User-defined grouping is disabled, but you can add groups in the data source. If you do so, the group header of the currently visible top group
								will stay static under the grid header while this group is scrolled vertically. If the currently scrolled rows belong to a group, having parent groups,
								their headers will also stay visible on top.
							

__enabled, staticHeaders__

User-defined grouping is allowed as well as adding groups manually in the data source. The group header of the currently visible top group
								will stay static under the grid header, while this group is scrolled vertically. If the currently scrolled rows belong to a group, having parent groups,
								their headers will also stay visible on top.
							

# Grouping Specifics

When __groupable__ is set to *enabled*, a new area will be exposed on the left side of the grid table view. You can drag a column header cell and drop it over
					this area (the grouping panel) to group by that column.
				![grid-grouping 1](../Media/Controls\Grid\grid-grouping_1.png)![grid-grouping 2](../Media/Controls\Grid\grid-grouping_2.png)

It is possible to group by multiple fields simply by dragging more columns onto the grouping panel. Then, you can click the panel to view all grouped fields.
					You can reorder them or remove any of them to modify the grouped view of the grid. This next image shows grouping by job position and then by last name.
				![grid-grouping 3](../Media/Controls\Grid\grid-grouping_3.png)

You have control over the content of the group headers and footers through the __groupHeaderTemplate__ and
					__groupFooterTemplate__ properties. For more information, see the [Templates article](e3c17ab8-400d-48d9-ae60-8bfcd5d87030).
				

The code sample below shows a grid with grouping enabled.


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							data: People.generatePeople(50),
						},
						groupable: "enabled",
						columns: [
	                        { field: "FirstName", title: "First Name" },
	                        { field: "LastName", title: "Last Name" },
							{ field: "Title", title: "Position" },
							{ field: "City" }
						],
						height: 320
					});



*generatePeople* is a simple function for generating a given number of records. To be able to run the above code sample, you can copy
					the code below as well.
				


 __js__
    


	WinJS.Namespace.define("People", {
		generatePeople: WinJS.Utilities.markSupportedForProcessing(function (itemCount) {
			var firstNames = ["Nancy", "Andrew", "Janet", "Margaret", "Steven", "Michael", "Robert", "Laura", "Anne", "Nige"],
			lastNames = ["Davolio", "Fuller", "Leverling", "Peacock", "Buchanan", "Suyama", "King", "Callahan", "Dodsworth", "White"],
			cities = ["Seattle", "Tacoma", "Kirkland", "Redmond", "London", "Philadelphia", "New York", "Seattle", "London", "Boston"],
			titles = ["Accountant", "Vice President, Sales", "Sales Representative", "Technical Support", "Sales Manager", "Web Designer",
			"Software Developer", "Inside Sales Coordinator", "Chief Techical Officer"];
			
			var data = [];
	
			do {
				var firstName = firstNames[Math.floor(Math.random() * firstNames.length)],
					lastName = lastNames[Math.floor(Math.random() * lastNames.length)],
					city = cities[Math.floor(Math.random() * cities.length)],
					title = titles[Math.floor(Math.random() * titles.length)];
	
				data.push({
					Id: data.length + 1,
					FirstName: firstName,
					LastName: lastName,
					City: city,
					Title: title
				});
			} while (data.length < itemCount);
			return data;
		})
	});



# Related Topics
