---
title: Cell Template
meta_title: Cell Template
meta_description: description.
slug: 
tags:cell,template
publish:True
---


In this help article, you will learn about the __template__ property, which is used to specify the content rendered in all data cells of a given
		  RadGrid column.
	  

# Using a Template for the Data Cells

The property accepts either a string template or a function as values. The function must return a string containing HTML. As you will
				  see below, you can use such functions to even display another RadControl in the column cell.
			  

Since you have a data context available, you can easily use multiple fields from the current data item and display multiple values arranged together
				  in a single cell. The example below shows how to use two values to display a full name and build an image source. Also, in the last column, a WinJS Rating
				  control is declared in the template. Note that in order for the control to be initialized, you need to call processAll for the RadGrid element after it
				  is entirely loaded. An appropriate event for this would be __dataBound__.
			  


 __js__
    


					var gridHtmlTemplate = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport: {
								read: {
									url: 'http://services.odata.org/Northwind/Northwind.svc/Employees',
									dataType: 'json'
								}
							},
							schema: {
								data: 'value'
							}
						},
						columns: [
							{ field: 'EmployeeID', title: 'ID', width: 40 },
							{
								field: 'LastName',
								title: 'Employee',
								template: '<div class="bcard"><img src="http://demos.telerik.com/aspnet-ajax/salesdashboard/Images/#= FirstName #_#=LastName#.png" /><h3>#= FirstName # #= LastName #</h3><h4>#= Title #</h4></div>'
							},
							{ field: 'Title' },
							{ template: '<div data-win-control="WinJS.UI.Rating"></div>' }
						],
						height: 350
					});
	
					gridHtmlTemplate.addEventListener("databound", initializeControls);




 __js__
    


		function initializeControls(e) {
			if (e.target.element.offsetHeight) {
				WinJS.UI.processAll(e.target.element);
			}
			else {
				setTimeout(initializeControls, 500);
			}
		}



This definition will result in the following control:![grid-columns-cell-template](../Media/Controls\Grid\grid-columns-cell-template.png)

# Related Topics
