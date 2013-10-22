---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


In this help article, you will learn how RadTokenInput can be populated with data, how the filter process can be configured and what options you have for defining
				the way the matches are shown to the user.
			

* 

[Data Binding](#data-binding)

* 

[Local Sources](#local)

* 

[Remote Sources](#remote)

* 

[Configuring Filtering](#filtering)

* 

[Configuring Selection](#selection)

* 

[Configuring Presentation](#presenting)

# data-bindingData-binding

RadTokenInput can be bound to both local arrays and remote data via the underlying
					[Telerik.Data.DataSource](d27deb0c-aa3f-4549-8308-6c2e0f99d2df) component; an abstraction for local and remote data.
				

The properties used to bind the dropdownlist are:

* 

__autoBind__: A boolean property indicating whether the control should be bound to the data on initialization. Its default
							value is *true*.
						

* 

__dataSource__: Specifies the object from which RadTokenInput will fetch its items.
						

* 

__dataTextField__: Gets or sets the field from the dataSource which will be used to provide text for the RadTokenInput list items.
						

* 

__dataValueField__: Gets or sets the field from the dataSource which will be used to populate the items value.
						

Below you can see examples of binding RadTokenInput to local and remote sources.

# localLocal Sources

To bind RadDropDownList locally, you can set the __dataSource__ property to a local array.
						


 __js__
    


					var dataSource = ["Item1", "Item2", "Item3"];
					var tokenInput = new Telerik.UI.RadTokenInput(document.getElementById("localSourcesTokenInput"), {
						dataSource: {
							data: dataSource
						}
					});



# remoteRemote Sources

You can bind RadTokenInput to both the __Telerik.Data.DataSource__ component and a __WinJS.Binding.List__.
							You can see examples below.
						

__Binding to Telerik.Data.DataSource__

The easiest way to bind a RadTokenInput to remote suggestions is to use the DataSource component (Telerik.Data.DataSource)—an abstraction for local
							and remote data. The DataSource component can be used to serve data from XML and JSON data services or from local files containing data in XML or JSON format.
						


 __js__
    


					var dataSourceTokenInputCtrl = new Telerik.UI.RadTokenInput(document.getElementById('dataSourceTokenInput'), {
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
							sort: { field: "ProductName", dir: "asc" },
							onerror: function (e) { debugger; }
						}
					});



__Binding to WinJS.Binding.List__

Another option is to request the data manually through the WinJS.xhr function and populate the results in a
							__WinJS.Binding.List__ object. An example is shown below:
						


 __js__
    


					var employeesSource = new WinJS.Binding.List();
					WinJS.xhr({
						url: "http://services.odata.org/Northwind/Northwind.svc/Employees?$format=json",
					}).then(function (result) {
						var employees = JSON.parse(result.response).value;
						employees.forEach(function (employee) {
							employeesSource.push({
								name: employee.FirstName + " " + employee.LastName,
								id: employee.EmployeeID
							});
						});
					}
					);
					var listTokenInputCtrl = new Telerik.UI.RadTokenInput(document.getElementById('listTokenInput'), {
						dataSource: employeesSource,
						dataTextField: "name",
						dataValueField: "id"
					});



# filteringConfiguring Filtering

You can control when and how RadTokenInput will filter its suggestions. The following properties help you achieve this:

* 

__delay__: The delay in milliseconds after which the control will start filtering the dataSource. Using this property, you
							can postpone the filtering, allowing the user to type in more text before RadTokenInput starts searching for suggestions.
						

* 

__filter__: Sets the filter function used when filtering the data. The meaningful values that you can use are
							*"eq"* (equals), *"contains"* (contains) and
							*"startswith"* (starts with). The default value of the property is "none".
						

* 

__ignoreCase__: A Boolean type property indicating whether or not search for suggestions should be case-sensitive. The default
							filtering is case-insensitive.
						

* 

__minLength__: The minimum number of characters that should be typed before RadTokenInput queries its data source.
							By setting a number, greater than 0 (default value), you can search on more specific criteria.
						

Note that if you do not specify filter options, RadTokenInput will display all its available suggestions on focus. If you set
					__minLength__ or __filter__ to values different than their defaults, the user would first need to type in text,
					before the RadTokenInput fetches suggestions.
				


 __js__
    


					var filteredTokenInputCtrl = new Telerik.UI.RadTokenInput(document.getElementById("filteredTokenInput"), {
						dataSource: {
							data: dataSource
						},
						filter: "contains",
						minLength: 2,
						ignoreCase: true,
						delay: 1000
					});



# selectionConfiguring Selection

You can easily limit the number of items that can be selected in RadTokenInput. Just set the __maxSelectedItems__ property to
					an integer value. This way, once the maximum number of selected values is reached, the dropdown list with the suggestions will not be displayed anymore.
				


 __js__
    


					var selectionLimitTokenInputCtrl = new Telerik.UI.RadTokenInput(document.getElementById("selectionLimitTokenInput"), {
						dataSource: {
							data: dataSource
						},
						maxSelectedItems: 2
					});



# presentingConfiguring Presentation

You can use the properties below to modify the way the user interacts with the RadTokenInput control:
				

* 

__enabled__: Gets or sets the enabled state of the control. You can use it when you want to prevent selecting a value in
							RadTokenInput, for example, if the user has to perform another action before being able to interact with the RadTokenInput control.
						

* 

__height__: Use this property to set the RadTokenInput's dropdown list height in pixels.
						

* 

__highlightFirst__: A Boolean value indicating whether the first item should automatically be marked for selection. Pressing
							Enter while typing in this case will select the item. The default value of the property is *true*.
						![tokeninput-configuration-highlight-first](../Media/Controls\TokenInput\tokeninput-configuration-highlight-first.png)

* 

__placeholder__: Allows you to specify text to display in the input area before the user starts typing.

						

* 

__readonly__: A Boolean value that determines whether RadTokenInput is read-only.
						

# Customizing Tags and Items

RadTokenInput exposes two properties that allow you to provide templates for its tags and items—__tagTemplate__ and
					__itemTemplate__. For more information and examples of their usage, go to:
					[Item Template](4c5db45e-de1f-401e-a79e-aceae48f54e5) and
					[Tag Template](17f87026-ae80-46e2-b792-8a35ccdfdf29).
				

# Related Topics
