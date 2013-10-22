---
title: Binding RadGrid to Local Data
meta_title: Binding RadGrid to Local Data
meta_description: description.
slug: 
tags:binding,radgrid,to,local,data
publish:True
---


In terms of settings, binding RadGrid to local data is the simplest scenario. You just need to set the __dataSource.data__ property to
				an array containing your data and you are good to go. Of course, you can also assign a __WinJS.Binding.List__ as a dataSource as you can see
				below. However, in most scenarios you would not need it, as you can process your data in the DataSource instance itself.
			

# Section1Binding RadGrid to an Array of Objects

The examples below show how you could bind a grid to a local array of data.

Here you can see that if your data is simple enough, you do not even need to define columns, the grid will automatically generate them:


 __js__
    


					var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							data: [
								{ Name: "Peter", Age: 23, Points: 22.6 },
								{ Name: "Mary", Age: 30, Points: 24 },
								{ Name: "Mark", Age: 27, Points: 28.8 }
							]
						}
					});



Following is a sample that demonstrates how nested objects' values can be displayed. You just need to define the columns explicitly and in the
					__field__ property of the column, point to the object value using [childObject].[propertyName].
				


 __js__
    


					var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
						dataSource: {
							data: [
								{
									Name: "Peter",
									Age: 23,
									Results: {
										Module: "Running",
										Points: 22.6
									}
								},
								{
									Name: "Mary",
									Age: 30,
									Results: {
										Module: "Swimming",
										Points: 24
									}
								},
								{
									Name: "Mark",
									Age: 27,
									Results: {
										Module: "Running",
										Points: 28.8
									}
								}
							]
						},
						columns: [
							{ field: "Name" },
							{ field: "Age" },
							{ field: "Results.Module", title: "Module" },
							{ field: "Results.Points", title: "Points" }
						]
					});



# 
				Binding RadGrid Using a WinJS.Binding.List
			

The following example binds RadGrid to the same data, but processed through the native List component. If you already have logic that provides
					data to your app through it, you can just assign it as a value of the dataSource property.
				


 __js__
    


					var list = new WinJS.Binding.List([
								{
									Name: "Peter",
									Age: 23,
									Results: {
										Module: "Running",
										Points: 22.6
									}
								},
								{
									Name: "Mary",
									Age: 30,
									Results: {
										Module: "Swimming",
										Points: 24
									}
								},
								{
									Name: "Mark",
									Age: 27,
									Results: {
										Module: "Running",
										Points: 28.8
									}
								}
					]);
					var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid3"), {
						dataSource: list,
						columns: [
							{ field: "Name" },
							{ field: "Age" },
							{ field: "Results.Module", title: "Module" },
							{ field: "Results.Points", title: "Points" }
						]
					});



# Related Topics
