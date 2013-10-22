---
title: Filter ListView with RadAutoCompleteBox
meta_title: Filter ListView with RadAutoCompleteBox
meta_description: description.
slug: 
tags:filter,listview,with,radautocompletebox
publish:True
---


Because of its built-in filtering capabilities, RadAutoCompleteBox is a very convenient control for external filtering of other
				controls. The main idea is to bind the "filtered" control to the set of data used by the RadAutoCompleteBox. What actually happens is 
				that the ListView takes the RadAutoCompleteBox's underlying data. Technically the ListView is not filtered at any point but the visual
				result is comparable to filtering. This article describes a step-by-step approach for achieving this scenario.
			

# Section1

Follow the steps below to create a WinJS.UI.ListView filtered by RadAutoCompleteBox:

* 

Define the control wrappers in HTML and any static properties of the ListView:


 __html__
    


				<span id="autoComplete"></span>
				<div id="listView" data-win-control="WinJS.UI.ListView" data-win-options="{
					itemTemplate: FilteringListView.getTemplate
				}">
				</div>



* 

Instantiate the RadAutoCompleteBox and assign event handlers for its open and databound events:


 __js__
    


					var filterAutoComplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("autoComplete"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Customers",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						},
						dataTextField: "CompanyName",
						onopen: open,
						ondatabound: dataBound
					});



* 

By preventing the default action in the __open__ event, you will stop the RadAutoCompleteBox from opening its dropdown. This way
							it will visually behave as a search textbox.
						


 __js__
    


		function open(args) {
			args.preventDefault();
		}



* 

Handle the __databound__ event of RadAutoCompleteBox to refresh the ListView data source once
							the data in the autocomplete control is changed. 
						


 __js__
    


		function dataBound(args) {
			var list = document.getElementById("listView").winControl;
			var listSource = new WinJS.Binding.List(args.target.dataSource.view);
			list.itemDataSource = listSource.dataSource;
		}



* 

You could use a function to dynamically generate the listview items template:


 __js__
    


		WinJS.Namespace.define("FilteringListView", {
			getTemplate: WinJS.Utilities.markSupportedForProcessing(function (itemPromise) {
				return itemPromise.then(function (item) {
					var el = document.createElement("div");
					el.classList.add("companyItem");
					el.innerHTML = [
					"<h3>" + item.data.CompanyName + "</h3>",
					"<p>Contact Name: " + item.data.ContactName + "</p>",
					"<p>Phone: " + item.data.Phone + "</p>"].join("");
					return el;
				})
			})
		});



The result will be a dynamically changed ListView, based on the value input in the RadAutoCompleteBox:![autocompletebox-howto-filter-listview](../Media/Controls\AutoCompleteBox\autocompletebox-howto-filter-listview.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *AutoCompleteBox/FilteringExternalList*.
        

# Related Topics[WinJS.UI.ListView object](http://msdn.microsoft.com/en-us/library/windows/apps/br211837.aspx)

 * [Getting Started]({{slug:getting-started}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Events]({{slug:events}})

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})

 * [Filtering]({{slug:filtering}})
