---
title: Reordering
meta_title: Reordering
meta_description: description.
slug: 
tags:reordering
publish:True
---


If you would want the user to be able to arrange the order of columns in the grid to better fit their preference of viewing data, you can easily do this,by enabling the
				columns reordering feature of the control. This is done by setting the __reorderable__ property of RadGrid to *true* (it
				is false by default).
			

# Column Reordering

When reordering is enabled by setting __reorderable__ to true, the user can perform the following actions:
				

* 

Press and hold or tap and hold on a column header, so it is highlighted.

* 

Start dragging the header. It will replace other columns' headers to indicate where the selected column is about to be moved.

* 

Once the header is at its desired position, release it, so that the columns are reordered.


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							data: People.generatePeople(15)
						},
						columns: [
							{ field: "Id" },
							{ title: "Name", template: "#=FirstName+ ' ' +LastName#" },
							{ field: "Title" },
							{ field: "City" }
						],
						reorderable: true
					});



# Related Topics
