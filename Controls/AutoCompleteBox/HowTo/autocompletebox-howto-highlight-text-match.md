---
title: Highlight Matching Text in Suggestions
meta_title: Highlight Matching Text in Suggestions
meta_description: description.
slug: 
tags:highlight,matching,text,in,suggestions
publish:True
---


When the user types text into a RadAutoCompleteBox, its suggestions are filtered only to matching items. In scenarios where the filtering uses a "contains"
				function and the search string cannot be immediately spotted in a match, you may want to highlight the matching part of the text. To achieve this, you can
				follow the instructions below.
			

# Section1

To highlight parts of the text in the matching results, you can use a template for items and wrap the matched piece of text in a
					styled inline HTML element, for example <span>. To do this, perform the following steps:
				

* 

Define the RadAutoCompleteBox wrapper:


 __html__
    


				<span id="autoComplete"></span>



* 

Instantiate the RadAutoCompleteBox and assign it a template function:


 __js__
    


					var matchAutoComplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("autoComplete"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Products",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						},
						dataTextField: "ProductName",
						filter: "contains",
						template: itemTemplate
					});



* 

Declare a template function that triggers the matching logic:


 __js__
    


		function itemTemplate(item) {
			return matchQuery(item.ProductName);
		}



* 

The logic of the matching function is: Find the start and end index of the matching string in the current item. Then replace the substring between 
							them with the same string wrapped in an inline HTML element, which has a class name assigned.
						


 __js__
    


		function matchQuery(name) {
			var autoCompleteBox = document.getElementById("autoComplete").winControl;
			var query = autoCompleteBox.text.toLowerCase();
			var index = name.toLowerCase().indexOf(query);
			var match = name.substring(index, index + query.length);
			return name.replace(match, "<span class='match'>" + match + "</span>");
		}



* 

Provide some styling for the match:


 __none__
    


	.match {
		color: #33ccff;
	}



The result of typing into the RadAutoCompleteBox now looks like this:![autocompletebox-howto-highlight-text-match](../Media/Controls\AutoCompleteBox\autocompletebox-howto-highlight-text-match.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *AutoCompleteBox/TextMatchHighlighting*.
        

# Related Topics

 * [Getting Started]({{slug:getting-started}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Templates]({{slug:templates}})
