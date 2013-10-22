---
title: Item Template
meta_title: Item Template
meta_description: description.
slug: 
tags:item,template
publish:True
---


You can assign a template for the items in RadTokenInput if you set its __itemTemplate__ property. This template will be used for all items
				rendered in the control's dropdown. It could be:
			

* 

A string template with binding expressions

* 

A function returning a DOM element

In this help article, you can see how these two approaches are used to achieve the following result:![tokeninput-item-template](../Media/Controls\TokenInput\tokeninput-item-template.png)

# Section1Using a String Template with Binding Expressions

You can utilize a string template with binding expressions to provide more flexibility to the content of RadTokenInput items. You can evaluate JavaScript
					expressions and based on the result, return different content.
				

You can see a simple example of string template usage below:


 __js__
    


					var stringTemplateTokenInput = new Telerik.UI.RadTokenInput(document.getElementById("tokenInput2"), {
						dataSource: {
							data: cities
						},
						dataTextField: "City",
						dataValueField: "City",
						itemTemplate: "<div class='tItem'><img height=60 src='/images/Cities/#=City#.jpg'/><h3>#=City#</h3></div>"
					});



Here *cities* is an array of simple objects but if needed, you can access all fields of the current data item, even if they are not
					assigned as __dataTextField/dataValueField__.
				


 __js__
    


					var cities = [
						{ City: "Beijing" },
						{ City: "Berlin" },
						{ City: "Bombay" },
						{ City: "Bonn" },
						{ City: "Boston" },
						{ City: "Cairo" },
						{ City: "Cancun" },
						{ City: "Cannes" },
						{ City: "Frankfurt" }];



# Using a Function Returning a String

Another possible approach is to set the __itemTemplate__ property value to point to a function which returns a string for each
					item. This function can receive the data item for the current item as an argument, so that you can populate the template.
				


 __js__
    


					var functionTemplateTokenInput = new Telerik.UI.RadTokenInput(document.getElementById("tokenInput1"), {
						dataSource: {
							data: cities
						},
						dataTextField: "City",
						dataValueField: "City",
						itemTemplate: getTemplate
					});



And the templating function:


 __js__
    


		function getTemplate(item) {
			var template = ["<div class='tItem'><img height='60' src='/images/Cities/" + item.City + ".jpg'/>",
			"<h3>" + item.City + "</h3></div>"].join("");
			return template;
		}



Same as before, the *item* object passed to the templating function contains all fields of the current data item, even the ones
					that are not assigned as __dataTextField/dataValueField__.
				

# Related Topics

 * [Using Templates in RadControls]({{slug:using-templates-in-radcontrols}})
