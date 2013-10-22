---
title: Templates
meta_title: Templates
meta_description: description.
slug: 
tags:templates
publish:True
---


By default, RadPagination displays simple thumbnails giving a quick visual indication of the current page among all pages.
				The content of the thumbnails can be customized through the use of templates. Similar to the __WinJS.UI.FlipView__
				control, RadPagination provides the __itemTemplate__ property that can be used to specify the custom
				thumbnail template.
			

During data binding, the template in RadPagination is data-bound to the paged control's own data source. Any data properties from
				the __FlipView.itemDataSource__ are available inside the Pagination templates. This enables a wide range
				of visualization scenarios, where the FlipView data determines what the thumbnails of the Pagination show.
			

# Section1Defining an Item Template

A template can be specified in a variety of ways in RadPagination. The __itemTemplate__ property accepts the following
					different types of values:
				

* 

An instance of __WinJS.Binding.Template__.
						

* 

An HTML element hosting an instance of __WinJS.Binding.Template__ (identical to Microsoft native controls).
						

* 

A string value representing HTML to be generated along with data-binding expressions (e.g. "<span>#= title #</span>").

* 

A function that returns an HTML element.

* 

A function that returns an HTML string.

Below you can find samples for the main templating scenarios. They all result in the following combination of flipview and
					pagination controls:
				![Providing an item template](../Media/Controls\Pagination\pagination-templates.png)

# Using the WinJS.BindingTemplate

You can use a WinJS binding template for the RadPagination control just like with any other control:


 __html__
    


	<!DOCTYPE html>
	<html>
	<head>
		<meta charset="utf-8" />
		<title>templates</title>
	
		<!-- WinJS references -->
		<link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
		<script src="//Microsoft.WinJS.1.0/js/base.js"></script>
		<script src="//Microsoft.WinJS.1.0/js/ui.js"></script>
	
		<!-- Telerik references -->
		<link href="///Telerik.UI/css/common.css" rel="stylesheet" />
		<link href="///Telerik.UI/css/dark.css" rel="stylesheet" />
		<script src="///Telerik.UI/js/jquery.js"></script>
		<script src="///Telerik.UI/js/ui.js"></script>
	
		<link href="templates.css" rel="stylesheet" />
		<script src="templates.js"></script>
		<script src="../../js/defaultData.js"></script>
	</head>
	<body>
		<h1>Templates</h1>
		<div class="samplesContainer">
	
			<div class="example">
				<h2>Using WinJS.BindingTemplate</h2>
	
				<!-- #region wintemplate -->
				<div id="flipViewItemTemplate" data-win-control="WinJS.Binding.Template" style="display: none">
					<img src="#" data-win-bind="src: picture; alt: title " style="margin-right: 30px" />
					<h2 data-win-bind="innerText: title"></h2>
				</div>
	
				<div id="paginationTemplate" data-win-control="WinJS.Binding.Template" style="display: none">
					<img class="thumbitem" src="#" data-win-bind="src:thumb;" />
				</div>
	
				<div id="flipView1" style="height: 250px" data-win-control="WinJS.UI.FlipView" data-win-options="{ 
					itemDataSource: DefaultData.bindingList.dataSource, 
					itemTemplate: select('#flipViewItemTemplate') 
				}">
				</div>
				<div id="pagination1" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView1'),
					itemTemplate: select('#paginationTemplate')
				}">
				</div>
				<!-- #endregion -->
			</div>
			<div class="example">
				<h2>Returning template from a javascript function</h2>
				<div id="flipView2" style="height: 250px"></div>
				<div id="pagination2"></div>
			</div>
		</div>
		<div>
			<div class="singleContainer">
				<h2>Specifying string template</h2>
	
				<!-- #region string -->
				<div id="flipView3" style="height: 250px" data-win-control="WinJS.UI.FlipView" data-win-options="{ 
					itemDataSource: DefaultData.bindingList.dataSource, 
					itemTemplate: select('#flipViewItemTemplate') 
				}">
				</div>
				<div id="pagination" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView3'),
					itemTemplate: '&lt;div&gt; &lt;img src=&quot;#=thumb#&quot; alt=&quot;#=title#&quot; /&gt; &lt;/div&gt;'
				}">
				</div>
				<!-- #endregion -->
			</div>
	
	
		</div>
	</body>
	</html>



# Returning a Template from a JavaScript Function

The sample below shows how to dynamically create a FlipView and a RadPagination control, along with their templates. Note
							the difference in the objects that the controls pass to the templating function. __FlipView__ passes a WinJS.Promise object
							for the item that is about to render (read more
							[here](http://msdn.microsoft.com/en-us/library/windows/apps/hh700622.aspx) ).
							RadPagination sends the actual item with its binding context.
						


 __js__
    


					var flipView = new WinJS.UI.FlipView(document.getElementById("flipView2"), {
						itemDataSource: DefaultData.bindingList.dataSource,
						itemTemplate: PaginationTemplatesSample.getFlipViewTemplate
					});
	
					var pagination = new Telerik.UI.RadPagination(document.getElementById("pagination2"), {
						pageProvider: document.getElementById("flipView2").winControl,
						itemTemplate: PaginationTemplatesSample.getPaginationTemplate
					});




 __js__
    


		getFlipViewTemplate: WinJS.Utilities.markSupportedForProcessing(function (itemPromise) {
			return itemPromise.then(function (item) {
				var element = document.createElement("div");
				element.innerHTML =
				"<img  src='" + item.data.picture + "' alt='" + item.data.title + "' style='margin-right: 30px' /> " +
				"<h2>" + item.data.title + "</h2>";
				element.style.display = "-ms-flexbox";
				element.style.msFlexAlign = "center";
				return element;
			});
		}),
	
		getPaginationTemplate: WinJS.Utilities.markSupportedForProcessing(function (item) {
			var templateHolder = document.createElement("div");
			templateHolder.innerHTML = "<img  src='" + item.thumb + "' alt='" + item.title + "' />";
			return templateHolder;
		})



# Using a String with Binding Expressions

You can set a simple string as an item template for the pagination. It can use binding expressions to
							populate the rendered HTML with values from the item's binding context.
						>
								If you specify the template in HTML, you
								may need to use HTML-encoded characters to get matching quotation marks. In this case you will need to replace the quotations
								in the template value shown below with a matching
								<externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>HTML entity</linkText><linkUri>http://www.ascii.cl/</linkUri></externalLink>.
							


 __html__
    


				<div id="flipView3" style="height: 250px" data-win-control="WinJS.UI.FlipView" data-win-options="{ 
					itemDataSource: DefaultData.bindingList.dataSource, 
					itemTemplate: select('#flipViewItemTemplate') 
				}">
				</div>
				<div id="pagination" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView3'),
					itemTemplate: '&lt;div&gt; &lt;img src=&quot;#=thumb#&quot; alt=&quot;#=title#&quot; /&gt; &lt;/div&gt;'
				}">
				</div>



In all above samples, *DefaultData.bindingList* is of type WinJS.Data.List and is defined like this for the purpose of the example:
						


 __js__
    


	WinJS.Namespace.define("DefaultData", {
		bindingList: new WinJS.Binding.List([
		{
			type: "item",
			title: "Soft Drink",
			picture: "/images/food/1.jpg",
			thumb: "/images/thumbs/1.jpg"
		},
		//...



# Related Topics
