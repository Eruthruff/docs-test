---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


In this help article, you will learn how RadAutoCompleteBox can be populated with suggestions, how the search process can be configured and what options you have
				for defining the way the suggestions are shown to the user.
			

* 

[Providing Suggestions](#providing-suggestions)

* 

[Local Sources](#local-sources)

* 

[Remote Sources](#remote-sources)

* 

[Configuring the Search](#configuring-search)

* 

[Enabling Multiselection](#enabling-multiselection)

* 

[Presenting the Suggestions](#presenting-suggestions)

# providing-suggestionsProviding Suggestions

To provide suggestions for RadAutoCompleteBox you can use data:

* 

from a local array

* 

from a remote data service

Locally defined values are best for small, fixed sets of suggestions. Remote suggestions should be used for larger data sets. When used with the
					__DataSource__ component, filtering large remote data services can be pushed to the server as well, maximizing client-side performance.
				

The properties used to bind the autocomplete box are:

* 

__dataSource__: Specifies the object from which RadAutoCompleteBox will fetch its results.
						

* 

__dataTextField__: Gets or sets the field from the dataSource which will be used to provide text for the autocomplete suggestions.
						

Below you can see examples of providing suggestions from local and remote sources.

# local-sourcesLocal Sources

To configure and provide RadAutoCompleteBox suggestions locally, you can set the dataSource property to a local array.


 __js__
    


					var dataSource = ["Item1", "Item2", "Item3"];
					var autocomplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("localSourcesAutoComplete"), {
						dataSource: dataSource
					});



# remote-sourcesRemote Sources

__Binding to DataSource__

The easiest way to bind a RadAutoCompleteBox to remote suggestions is to use the DataSource component 
							(__Telerik.Data.DataSource__) - an abstraction for local and remote data. The DataSource component can be used to serve data 
							from XML and JSON data services.
						


 __js__
    


					var dataSourceAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById('dataSourceAutoComplete'), {
						minLength: 3,
						dataTextField: "ProductName",
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

Another option is to request the data manually through the __WinJS.xhr__ function and populate the results in a __WinJS.Binding.List__ object. An example is
							shown below:
						


 __js__
    


					var customersSource = new WinJS.Binding.List();
					WinJS.xhr({
						url: "http://services.odata.org/Northwind/Northwind.svc/Customers?$format=json",
					}).then(function (result) {
						var customers = JSON.parse(result.response).value;
						customers.forEach(function (customer) {
							customersSource.push({
								name: customer.CompanyName
							});
						});
					}
					);
	
					var listAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById('listAutoComplete'), {
						minLength: 2,
						dataSource: customersSource,
						dataTextField: "name"
					});



Note that in the first scenario, the DataSource control is dynamically requesting the data, which is filtered remotely, based on the value of the
							autocomplete box. In the second scenario, the entire data is queried and populated into the List object and is then filtered by the autocomplete box.
						

# configuring-searchConfiguring the Search

You can control when and how RadAutoCompleteBox will perform a search for suggestions. The following properties help you achieve this:

* 

__delay__: The delay in milliseconds after which the control will start filtering the dataSource. Using this property, you
							can postpone the filtering, allowing the user to type in more text before the autocomplete starts searching for suggestions.
						

* 

__filter__: Sets the filter function used when filtering the data. The meaningful values that you can use are
							"eq" (equals), "contains" (contains) and "startswith" (starts with).
						

* 

__ignoreCase__: A Boolean type property indicating whether or not search for suggestions should be case-sensitive.
						

* 

__minLength__: The minimum number of characters that should be typed before RadAutoCompleteBox queries its data source.
							This way you can search on more specific criteria.
						


 __js__
    


					var filteredAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("filteredAutoComplete"), {
						dataSource: dataSource,
						filter: "endsWith",
						minLength: 1,
						ignoreCase: true,
						delay: 1000
					});



# enabling-multiselectionEnabling Multiselection

You can allow the user to select multiple values. This is achieved through setting the __separator__ property. By default, its
					value is empty and single selection is allowed. If you set it to a value different than empty string, on selecting an item, the specified separator will be
					appended to the text in the autocomplete box and the user can continue typing new search text.
				

The declaration below will result in the autocomplete adding a comma and a space after each selected suggestion:


 __js__
    


					var multiSelectionAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("multiSelectionAutoComplete"), {
						dataSource: dataSource,
						filter: "endsWith",
						minLength: 1,
						ignoreCase: false,
						separator: ", "
					});



# presenting-suggestionsPresenting the Suggestions

Based on your requirements, you can provide different settings for facilitating the user's selection of text. They include:
				

* 

__autoSuggest__: Autocompletes the rest of the text in the text input area while the user is typing. The value used to complete
							the entry is the first one matching the current criteria.
						![Auto suggest](../Media/Controls\AutoCompleteBox\autocompletebox-auto-suggest.png)

* 

__height__: Use this property to set the RadAutoCompleteBox's dropdown list height in pixels.
						

* 

__highlightFirst__: A Boolean value indicating whether the first item should automatically be marked for selection. Pressing
							Enter while typing in this case will select the item.
						![Highlight the first match](../Media/Controls\AutoCompleteBox\autocompletebox-highlight-first.png)

* 

__enabled__: Gets or sets the enabled state of the control. You can use it when you want to prevent selecting a value in 
							RadAutoCompleteBox, for example, if the user has to perform another action before being able to interact with the control.
						

* 

__placeholder__: Allows you to specify text to display in the input area before the user starts typing.
						![Showing empty text](../Media/Controls\AutoCompleteBox\autocompletebox-placeholder.png)

* 

__readonly__: Gets or sets whether the RadAutoCompleteBox is read-only.
						

* 

__text__: You can use this property to get or set the text content of the control.
						

For example:


 __js__
    


					var customPresentingAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("customPresentingAutoComplete"), {
						dataSource: dataSource,
						minLength: 1,
						autoSuggest: true,
						highlightFirst: true,
						placeholder: "Type text to search for..."
					});



# Focusing the control

Since Q2 2013, RadAutoCompleteBox exposes a __focus()__ method. You can use it to programatically focus a control and allow the user
					to directly start typing in it.
				

# Related Topics[Working with RadAutoCompleteBox in JavaScript-based Application for Windows Store (Telerik Helper blog)](http://telerikhelper.net/2012/11/20/working-with-radautocompletebox-in-javascript-based-application-for-windows-store/)
