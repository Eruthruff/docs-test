---
title: Templates
meta_title: Templates
meta_description: description.
slug: 
tags:templates
publish:True
---


You can assign a template to __RadComboBox__ using its __template__ property. This template will be used for all 
        items rendered in the control's dropdown. It could be:
			

* 

A __WinJS.Binding.Template__ reference
					

* 

A string template with binding expressions
					

* 

A function returning a DOM element
					

In this article, you can see how the three approaches are used to create the following __RadComboBox__:![RadComboBox templates](../Media/Controls\ComboBox\combobox-templates.png)

# Using WinJS.Binding.Template

You can use the native template as you would with any other control that uses templates. It is easiest to declare the template in HTML, add bindings to 
					it and then, in JavaScript, assign a reference to the control as a template for RadComboBox:
				


 __html__
    


				<span id="winTemplateComboBox"></span>
				<div id="comboBoxTemplate" data-win-control="WinJS.Binding.Template">
					<div id="container">
						<img src="#" style="width: 50px;"
							data-win-bind="alt: Title; src: SmallPictureUrl" />
						<h6 data-win-bind="innerText: Title"></h6>
	                    <span style='color: #33ccff'>New Price: </span>
	                    <span style='color: #33ccff' data-win-bind="innerText: ConvertedCurrentPrice"></span>
					</div>
				</div>




 __js__
    


					var winTemplateComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById("winTemplateComboBox"), {
						dataTextField: "Title",
						dataValueField: "Id",
						filter: "contains",
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
						template: document.getElementById("comboBoxTemplate").winControl,
						height: 265
					});



# Using String Template with Binding Expressions

Another option is to utilize a string template with binding expressions to provide more flexibility to the content. You can evaluate JavaScript expressions 
					and based on the result, return different content. You can provide identical results as those of the WinJS template by using binding expressions. This next example
					shows a declaration that will provide a result equivalent to the one from the previous section:
				


 __js__
    


					var stringTemplateComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById("stringTemplateComboBox"), {
						dataTextField: "Title",
						dataValueField: "Id",
						filter: "contains",
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
						template: ["<div id='container'>",
						"<img src='#=SmallPictureUrl#' style='width:50px; margin-top:7px' alt='ProductName'/>",
						"<h5>#=Title#</h5><span style='color: \\#33ccff'>New Price: #=ConvertedCurrentPrice#</span></div>"].join(""),
						height: 265
					});



# 
				Using a Function Returning a DOM Element
			

Another possible approach is to set the __template__ property value to point to a function that returns a DOM element for each item. This function 
					can receive the data item for the current entry as an argument, so that you can populate the template:
				


 __js__
    


					var functionComboBoxCtrl = new Telerik.UI.RadComboBox(document.getElementById("functionComboBox"), {
						dataTextField: "Title",
						dataValueField: "Id",
						filter: "contains",
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
						height: 265
					});




 __js__
    


		function getTemplate(item) {
			var container = document.createElement("div");
			container.id = "container";
	
			var img = document.createElement("img");
			img.src = item.SmallPictureUrl;
			img.alt = "Product picture";
			img.style.width = "50px";
			img.style.marginTop = "7px";
			container.appendChild(img);
	
			var title = document.createElement("h5");
			title.innerText = item.Title;
			container.appendChild(title);
	
			var price = document.createElement("span");
			price.style.color = "#33ccff";
			price.innerText = "New Price: " + item.ConvertedCurrentPrice;
			container.appendChild(price);
	
			return container;
		}



# Related Topics[WinJS.Binding.Template object](http://msdn.microsoft.com/en-us/library/windows/apps/br229723.aspx)
