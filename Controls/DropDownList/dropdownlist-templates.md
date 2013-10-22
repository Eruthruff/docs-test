---
title: Templates
meta_title: Templates
meta_description: description.
slug: 
tags:templates
publish:True
---


You can assign a template to __RadDropDownList__ using its __template__ property. This template will be used for all items
				rendered in the dropdown. It could be:
			

* 

a __WinJS.Binding.Template__ reference
					

* 

a string template with binding expressions
					

* 

a function returning a DOM element
					

In this article you can find examples of the three possible scenarios.
			

# Using WinJS.Binding.Template

You can use the native template as you would with any other control that uses templates. Declare the template in HTML, add bindings to it and then, in 
					JavaScript, assign a reference to the control as a template for __RadDropDownList__:
				


 __html__
    


				<div id="dropDownListTemplate" data-win-control="WinJS.Binding.Template">
					<div id="container">
						<img src="#" style="width: 50px;"
							data-win-bind="alt: Title; src: SmallPictureUrl" />
						<h6 data-win-bind="innerText: Title"></h6>
					</div>
				</div>




 __js__
    


					var winTemplateDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById("winTemplateDropDown"), {
						dataTextField: "Title",
						dataValueField: "Id",
						dataSource: {
							transport: {
								read: {
									url: "/js/movies.json",
									dataType: "json"
								}
							},
							schema: {
								data: "movies"
							}
						},
						template: document.getElementById("dropDownListTemplate").winControl,
						height: 330
					});



# Using String Template with Binding Expressions

Another option is to use a string template with binding expressions to provide more flexibility to the content. You can evaluate JavaScript expressions 
					and based on the result, return different content.
					You can provide an identical template to the one shown in the previous section by using binding expressions.
				


 __js__
    


					var stringTemplateDropDownCtrl = new Telerik.UI.RadDropDownList(document.getElementById("stringTemplateDropDown"), {
						dataTextField: "Title",
						dataValueField: "Id",
						dataSource: {
							transport: {
								read: {
								    url: "/js/movies.json",
									dataType: "json"
								}
							},
							schema: {
								data: "movies"
							}
						},
						template: "<div id='container'><img src='#=SmallPictureUrl#' style='width:50px' alt='ProductName'/><h6>#=Title#</h6></div>",
						height: 330
					});



# 
				Using a Function Returning a DOM Element
			

The third possible approach is to set the __template__ property value to point to a function which returns a DOM element for each item. 
          This function can receive the data item for the current entry as an argument so that you can populate the template.
				


 __js__
    


					var functionDropDown = new Telerik.UI.RadDropDownList(document.getElementById("functionDropDown"), {
						dataTextField: "Title",
						dataValueField: "Id",
						dataSource: {
							transport: {
								read: {
								    url: "/js/movies.json",
									dataType: "json"
								}
							},
							schema: {
								data: "movies"
							}
						},
						template: getTemplate,
						height: 330
					});




 __js__
    


	function getTemplate(item) {
		var container = document.createElement("div");
		container.id = "container";
	
		var img = document.createElement("img");
		img.src = item.SmallPictureUrl;
		img.alt = "Product picture";
		img.style.width = "50px";
		container.appendChild(img);
	
		var title = document.createElement("h6");
		title.innerText = item.Title;
		container.appendChild(title);
	
		return container;
	}



The result from all three examples of displaying templated items containing an image and a heading is one and the same, shown in the image below.![Templated RadDropDownList](../Media/Controls\DropDownList\dropdownlist-templates.png)

# Related Topics[WinJS.Binding.Template object](http://msdn.microsoft.com/en-us/library/windows/apps/br229723.aspx)
