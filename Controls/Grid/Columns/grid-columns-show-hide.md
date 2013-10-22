---
title: Show/Hide Grid Columns
meta_title: Show/Hide Grid Columns
meta_description: description.
slug: 
tags:show/hide,grid,columns
publish:True
---


You can show and hide columns in RadGrid, using the control's API. This allows you to hide a column by default and show it upon some user action, or allow the 
				end-user to show and hide columns as per their preference.
			

# Section1Hide columns by default

When you want to hide a RadGrid column in the initial view of the control, you just need to set its __hidden__ property to
					*true*. The column will be rendered but with a *display: none* style applied to it. For example,
					with the following definition, the Age column will be initially invisible:
				


 __html__
    


				<div id="showHideGrid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
							dataSource: {
								data: [
									{ Name: 'Peter', Age: 23, Points: 22.6 },
									{ Name: 'Mary', Age: 30, Points: 24 },
									{ Name: 'Mark', Age: 27, Points: 28.8 }
								]
							},
							columns: [
								{ field: 'Name', title: 'Participant'},
								{ field: 'Age', hidden: true},
								{ field: 'Points', title: 'Score'}
							]
						}">
				</div>
				<button id="btn">Click to show age column</button>



# Show/hide columns programmatically

RadGrid exposes two methods to achieve the columns show/hide functionality - __showColumn()__ and __hideColumn()__.
					Both accept a single argument, which must be the 0-based index of the column, or its bound field. In the second case, make sure that you pass the name of the
					field to which the column is bound and *not* the title of the column.
				

You can extend the above example to show the hidden column on button click with the following code:


 __js__
    


					document.getElementById("btn").addEventListener("click", function () {
						var grid = showHideGrid.winControl;
						grid.showColumn(1);
					});



# Related Topics

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})
