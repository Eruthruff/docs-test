---
title: Templates
meta_title: Templates
meta_description: description.
slug: 
tags:templates
publish:True
---


You can provide a template for customizing the appearance of the RadAutoCompleteBox suggestions. This is achieved by assigning the __template__
				property one of the following values:
			

* 

a __WinJS.Binding.Template__ reference
					

* 

a string template
					

* 

a function returning a DOM element
					

In this help article, you will see examples of all three approaches. If you run their code, they will all produce the autocomplete box shown below:![autocompletebox-templates](../Media/Controls\AutoCompleteBox\autocompletebox-templates.png)

# Using WinJS.Binding.Template

You can use the native template as you would with any other control that uses templates. It is easiest to declare the template in HTML, add bindings to it 
					and then, in JavaScript, assign a reference to the control as a template for RadAutoCompleteBox:
				


 __html__
    


				<div id="autoCompleteBoxTemplate" data-win-control="WinJS.Binding.Template">
					<div id="container">
						<h3 style="color: #33ccff" data-win-bind="innerText: CompanyName"></h3>
						<span data-win-bind="innerText:Address"></span>, <span data-win-bind="innerText:City"></span>
					</div>
				</div>
				<span id="winTemplateAutoComplete"></span>




 __js__
    


					var winTemplateAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("winTemplateAutoComplete"), {
						dataTextField: "CompanyName",
						filter: "contains",
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
						template: document.getElementById("autoCompleteBoxTemplate").winControl,
						height: 230
					});



# Using a String Template with Binding Expressions

Another option is to utilize a string template with binding expressions to provide more flexibility to the content. You can evaluate JavaScript expressions 
					and based on the result, return different content.
					You can provide identical results as those of the WinJS template by using binding expressions. The following declaration will provide
					a result equivalent to the one from the previous section example:
				


 __js__
    


					var stringTemplateAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("stringTemplateAutoComplete"), {
						dataTextField: "CompanyName",
						filter: "contains",
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
						template: "<div id='container'><h3 style='color: \\#33ccff;'>#=CompanyName#</h3><span>#=Address#, #=City#</span></div>",
						height: 230
					});



# 
				Using a Function Returning a DOM Element
			

Another possible approach is to set the __template__ property value to point to a function that returns a DOM element for each item.
					This function can receive the data item for the current entry as an argument, so that you can populate the template accordingly:
				


 __js__
    


					var functionAutoCompleteCtrl = new Telerik.UI.RadAutoCompleteBox(document.getElementById("functionAutoComplete"), {
						dataTextField: "CompanyName",
						filter: "contains",
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
						template: getTemplate,
						height: 230
					});




 __js__
    


		function getTemplate(item) {
			var container = document.createElement("div");
			container.id = "container";
	
			var title = document.createElement("h3");
			title.innerText = item.CompanyName;
			title.style.color = "#33ccff";
			container.appendChild(title);
	
			var address = document.createElement("span");
			address.innerText = item.Address + ", " + item.City;
			container.appendChild(address);
	
			return container;
		}



# Related Topics[WinJS.Binding.Template object](http://msdn.microsoft.com/en-us/library/windows/apps/br229723.aspx)

 * [Using Templates in RadControls]({{slug:using-templates-in-radcontrols}})
