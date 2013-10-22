---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article will introduce you to the specifics of binding RadDropDownList and presenting its options to the user.
			

* 

[Data-binding](#data-binding)

* 

[Local sources](#local-sources)

* 

[Remote sources](#remote-sources)

* 

[Presenting the options](#presenting-options)

# data-bindingData-binding

The RadDropDownList can be bound to both local arrays and remote data via the DataSource component; an abstraction for local and remote data. Local arrays are
					appropriate for limited value options, while remote data binding is better for larger data sets. With remote data-binding, items will be loaded on-demand; when
					they are displayed.
				

The properties used to bind the RadDropDownList are:

* 

__autoBind__: A Boolean property indicating whether the control should be bound to the dataSource on initialization.
						

* 

__dataSource__: Specifies the object from which RadDropDownList will fetch its items.
						

* 

__dataTextField__: Gets or sets the field from the dataSource which will be used to provide text for the dropdown list items.
						

* 

__dataValueField__: Gets or sets the field from the dataSource which will be used to populate the items value.
						

Below you can see examples of binding RadDropDownList to local and remote sources.

# local-sourcesLocal Source

To bind RadDropDownList locally, you can set the dataSource property to a local array.


 __js__
    


					var localSourcesDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById("localSourcesDropDown"), {
						dataTextField: "text",
						dataValueField: "value",
						dataSource: [
							{ text: "Item1", value: "1" },
							{ text: "Item2", value: "2" }
						]
					});



# remote-sourcesRemote Sources

__Binding to DataSource__

The easiest way to bind a RadDropDownList to remote suggestions is to use the DataSource component 
							(__Telerik.Data.DataSource__)—an abstraction for local and remote data. The DataSource component can be used to serve data 
							from data services, such as XML and JSON.
						


 __js__
    


					var dataSourceDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById("dataSourceDropDown"), {
						dataTextField: "ProductName",
						dataValueField: "ProductID",
						filter: "contains",
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Products",
									dataType: "json"
	
								}
							},
							schema: {
								data: "value"
							},
							sort: { field: "ProductName", dir: "asc" }
						}
					});



__Binding to List__

Another option is to request the data manually through the __WinJS.xhr__ function and populate the results in a
							__WinJS.Binding.List__ object.
							An example is shown below:
						


 __js__
    


					var categoriesList = new WinJS.Binding.List();
					WinJS.xhr({
						url: "http://services.odata.org/Northwind/Northwind.svc/Categories?$format=json",
					}).then(function (result) {
						var categories = JSON.parse(result.response).value;
						categories.forEach(function (category) {
							categoriesList.push({
								categoryId: category.CategoryId,
								categoryName: category.CategoryName
							});
						});
					}
					);
	
					var listDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById('listDropDown'), {
						dataSource: categoriesList,
						dataTextField: "categoryName",
						dataValueField: "categoryId"
					});
	



# presenting-optionsPresenting the Options

You can use the properties below to modify the way the user interacts with the dropdown list control:

* 

__enabled__: Gets or sets the enabled state of the control. You can use it when you want to prevent selecting an item in 
							RadDropDownList. For example, if the user has to perform another action before being able to write and choose a suggestion.
						

* 

__height__: Use this property to set the dropdown list height in pixels.
						

* 

__index__: By setting this property to a numeric value , you can specify which item in the dropdown list will be selected. The index is
							zero-based.
						

* 

__optionLabel__: Set this property value to some string and it will be displayed in a default empty item in the dropdown list.
						![Options Label](../Media/Controls\DropDownList\dropdownlist-option-label.png)

* 

__readonly__: Gets or sets whether the RadDropDownList is read-only.
						

* 

__text__: Use this property to define the text of the control, when its __autoBind__ property
							is set to false.
						

* 

__value__: Use this property to define the value of the control.
						


 __js__
    


					var customPresentingDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById("customPresentingDropDown"), {
						dataSource: categoriesList,
						dataTextField: "categoryName",
						dataValueField: "categoryId",
						optionLabel: "Pick a category..."
					});



# Focusing the control

Since Q2 2013, RadDropDownList exposes a __focus()__ method. You can use it to programatically focus a control and allow the user
					to directly navigate through its options.
				

# Related Topics[Working with RadDropDownList in JavaScript based Windows Store Application (Telerik Helper blog)](http://telerikhelper.net/2012/11/19/working-with-raddropdownlist-in-javascript-based-windows-store-application/)
