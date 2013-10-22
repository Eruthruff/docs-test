---
title: Tag Template
meta_title: Tag Template
meta_description: description.
slug: 
tags:tag,template
publish:True
---


You can assign a template not only for RadTokenInput items but for its tags as well. For this purpose, use the __tagTemplate__ property.
				This template will be used for all tags rendered in the control's textbox. It could be:
			

* 

A string template with binding expressions

* 

A function returning a DOM element

In this help article, you can see how these two approaches are used to achieve the following result:![tokeninput-tag-template](../Media/Controls\TokenInput\tokeninput-tag-template.png)

# Section1Using a String Template with Binding Expressions

You can use a string template with binding expressions as a simple way to customize the look of tags in RadTokenInput. The string template has a binding
					context where all fields from the corresponding data item are available.
				

You can see the __itemTemplate__ example, extended to also feature a __tagTemplate__, below:
				


 __js__
    


					var tagStringTemplateTokenInput = new Telerik.UI.RadTokenInput(document.getElementById("tagTemplateTokenInput2"), {
						dataSource: {
							data: cities
						},
						dataTextField: "City",
						dataValueField: "City",
						itemTemplate: "<div class='tItem'><img height=60 src='/images/Cities/#=City#.jpg'/><h3>#=City#</h3></div>",
						tagTemplate: "<img style='vertical-align: middle' height='25' src='/images/Cities/#=City#.jpg'/><span>&nbsp;#=City#</span>"
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

Another possible approach is to set the __tagTemplate__ property value to point to a function that returns a string for each
					item. This function can receive the data item for the current item as an argument so that you can populate the template.
				


 __js__
    


					var tagFunctionTemplateTokenInput = new Telerik.UI.RadTokenInput(document.getElementById("tagTemplateTokenInput1"), {
						dataSource: {
							data: cities
						},
						dataTextField: "City",
						dataValueField: "City",
						itemTemplate: getTemplate,
						tagTemplate: getTagTemplate
					});



And the templating function:


 __js__
    


		function getTagTemplate(item) {
			var template = ["<img style='vertical-align: middle' height='25' src='/images/Cities/" + item.City + ".jpg'/>",
			"<span>&nbsp;" + item.City + "</span>"].join("");
			return template;
		}



Same as before, the *item* object, passed to the templating function, contains all fields of the current data item, even the ones
					that are not assigned as __dataTextField/dataValueField__.
				

For clarity, the template function used for the items is the following:


 __js__
    


		function getTemplate(item) {
			var template = ["<div class='tItem'><img height='60' src='/images/Cities/" + item.City + ".jpg'/>",
			"<h3>" + item.City + "</h3></div>"].join("");
			return template;
		}



# Related Topics

 * [Using Templates in RadControls]({{slug:using-templates-in-radcontrols}})
