---
title: Provide Default Grouping
meta_title: Provide Default Grouping
meta_description: description.
slug: 
tags:provide,default,grouping
publish:True
---


In some cases, you may want to display RadGrid grouped by default. Furthermore, this may be the only grouping that you want to allow in the control. This article
				describes how to achieve this kind of scenario.
			

# Section1Providing Default Group Expressions

You can provide default grouping in RadGrid by listing the groups in the __dataSource__ definition. Even if the
					__groupable__ property is set to *"none"*, these groupings will be applied to the grid, so you have an option to provide only pre-defined
					grouping without allowing the user to ungroup the grid or add more groups:
				


 __js__
    


					var groupedGrid = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						dataSource: {
							data: People.generatePeople(20),
							group: { field: "City" }
						},
						columns: [
	                        { field: "FirstName", title: "First Name" },
	                        { field: "LastName", title: "Last Name" },
							{ field: "Title", title: "Position" },
							{ field: "City" }
						],
						height: 320
					});



If you want to enable static headers in this scenario, set the __groupable__ property to *"staticHeaders"*.
				

To allow the user to ungroup RadGrid or add more groups, set the __groupable__ property to either *"enabled"*
					or *"enabled, staticHeaders"*.
				

For more information on defining groups in the DataSource, check [this article](f5db7e1e-a78f-4f08-9ecc-ba6abe96d770).
				

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/ProvidingDefaultGrouping*.
        

# Related Topics

 * [Binding RadGrid to Remote Data]({{slug:binding-radgrid-to-remote-data}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Grouping]({{slug:grouping}})
