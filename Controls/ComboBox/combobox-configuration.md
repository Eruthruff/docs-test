---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article will introduce you to the specifics of binding RadComboBox, filtering its results and presenting them to the user. We will cover:

* 

[Data-binding](#data-binding)

* 

[Local sources](#local-sources)

* 

[Remote sources](#remote-sources)

* 

[Filtering the results](#filtering-results)

* 

[Presenting the suggestions](#presenting-suggestions)

# data-bindingData-binding

The RadComboBox can be bound to both local arrays and remote data via the DataSource component; an abstraction for local and remote data. Local arrays are appropriate for
					limited value options, while remote data binding is better for larger data sets. With remote data-binding, items will be loaded on-demand; when they are displayed.
				

The properties used to bind the RadComboBox are:

* 

__autoBind__: A Boolean property indicating whether the control should be bound to the dataSource on initialization. Its
							default value is *true*.
						

* 

__dataSource__: Specifies the object from which RadComboBox will fetch its data items.
						

* 

__dataTextField__: Gets or sets the field from the dataSource which will be used to provide text for the combobox items.
						

* 

__dataValueField__: Gets or sets the field from the dataSource which will be used to populate the items value.
						

Below you can see examples of binding RadComboBox to local and remote sources.

# local-sourcesLocal Sources

To bind RadComboBox locally, you can set the dataSource property to a local array.


 __js__
    


					var localSourcesComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById("localSourcesComboBox"), {
						dataTextField: "text",
						dataValueField: "value",
						dataSource: [
							{ text: "Item1", value: "1" },
							{ text: "Item2", value: "2" }
						]
					});



# remote-sourcesRemote Sources

__Binding to DataSource__

The easiest way to bind a RadComboBox to remote suggestions is to use the DataSource component (__Telerik.Data.DataSource__) 
							- an abstraction for local and remote data. Your application can use the DataSource component to serve data from online data services, 
							such as XML and JSON.
						


 __js__
    


					var dataSourceComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById("dataSourceComboBox"), {
						index: 0,
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
    


					var customersSource = new WinJS.Binding.List();
					WinJS.xhr({
						url: "http://services.odata.org/Northwind/Northwind.svc/Customers?$format=json",
					}).then(function (result) {
						var customers = JSON.parse(result.response).value;
						customers.forEach(function (customer) {
							customersSource.push({
								name: customer.CompanyName,
								id: customer.CustomerID
							});
						});
					}
					);
	
					var listComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById('listComboBox'), {
						dataSource: customersSource,
						dataTextField: "name",
						dataValueField: "id"
					});



Note that using this approach, you will load all data entries locally, once you populate the list.

# filtering-resultsFiltering the Results

You can control when and how RadComboBox will perform a filtering for the items displayed in it. The following properties help you achieve this:

* 

__delay__: The delay in milliseconds after which the control will start filtering the dataSource. Using this property, you
							can postpone the filtering, allowing the user to type in more text before RadComboBox starts filtering its source.
						

* 

__filter__: Sets the filter function used when filtering the data. The meaningful values that you can use are
							*"eq"* (equals), *"contains"* (contains) and 
							*"startswith"* (starts with).
						

* 

__ignoreCase__: A Boolean type property indicating whether or not search should be case-sensitive.
						

* 

__minLength__: The minimum amount of characters that should be typed before RadComboBox filters its data source.
							This way you can perform search on more specific criteria.
						


 __js__
    


					var filteredComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById('filteredComboBox'), {
						dataSource: customersSource,
						dataTextField: "name",
						dataValueField: "id",
						delay: 1500,
						filter: "startsWith",
						ignoreCase: false,
						minLength: 2
					});



# presenting-suggestionsPresenting the Suggestions

Based on your requirements, you can provide different settings for fascilitating the user's interaction with the control. They include:
				

* 

__autoSuggest__: Auto-completes the rest of the text in the text input area while the user is typing. The value used to complete
							the entry is the first one matching the current criteria.
						![AutoSuggest feature](../Media/Controls\ComboBox\combobox-auto-suggest.png)

* 

__enabled__: Gets or sets the enabled state of the control. You can use it when you want to prevent selecting an item in RadComboBox,
							for example if the user has to perform another action before being able to write and choose a suggestion.
						

* 

__height__: Use this property to set the RadComboBox's dropdown list height in pixels.
						

* 

__highlightFirst__: A Boolean value indicating whether the first item should automatically be marked for selection. Pressing
							Enter while typing in this case will select the item.
						![Highlight first item feature](../Media/Controls\ComboBox\combobox-highlight-first.png)

* 

__index__: By setting this property to a numeric value , you can specify which item in the RadComboBox will be selected. 
							The index is zero-based.
						

* 

__readonly__: Gets or sets whether the RadComboBox is read-only.
						

* 

__text__: Use this property to define the text of the control, when its __autoBind__ property 
							is set to false.
						

* 

__value__: Use this property to define the value of the control.
						


 __js__
    


					var customPresentingComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById('customPresentingComboBox'), {
						dataSource: customersSource,
						dataTextField: "name",
						dataValueField: "id",
						highlightFirst: true,
						autoSuggest: true
					});



# Focusing the control

Since Q2 2013, RadComboBox exposes a __focus()__ method. You can use it to programatically focus a control and allow the user
					to directly start typing in it.
				

# Related Topics
