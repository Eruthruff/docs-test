---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


RadPagination for Windows 8 is a HTML/JavaScript component that attaches to pageable content presenter controls on your page. Currently, only __WinJS.UI.FlipView__ is
				supported out-of-the box.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a Pagination

To add a RadPagination control in the HTML markup, add an empty __div__ element with a __data-win-control__
							attribute and a value of __Telerik.UI.RadPagination__:
						

	
							<div data-win-control="Telerik.UI.RadPagination">
							</div>
						



Alternatively, you can instantiate RadPagination programmatically by defining an empty __div__ element with an __id__
							attribute and using the __Telerik.UI.RadPagination__ control constructor in JavaScript:
						

	
							<div id="myPagination">
							</div>
						



	
							var pagination = new Telerik.UI.RadPagination(document.getElementById("myPagination"));
						



Defining a __RadPagination__ without setting any properties will not result in a usable control. Moreover, 
              __RadPagination__ needs to be associated with a pageable control like __WinJS.UI.FlipView__ to 
              function properly. You can find more information regarding how this is done in this article: 
              [RadPagination configuration options](af98f628-de56-42cd-bd48-186df9b07a77)

# optionsSetting Pagination Options

Just like any other Windows Runtime JavaScript control, RadPagination control options can be defined through the __data-win-options__
							attribute:
						

	
							<div data-win-control="Telerik.UI.RadPagination" data-win-options="{showButtons:'false'}">
							</div>
						



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						

	
							var pagination = new Telerik.UI.RadPagination(document.getElementById("myGauge"), { showButtons: false });
						



To see all available configuration options in the API, click to go to T:Telerik.UI.RadPagination

# accessAccessing and Modifying RadPagination

You can get ahold of the RadPagination object the same way as the native WinJS components—find its DOM element and access its
							__winControl__ property.
						

	
							var pagination = document.getElementById("myPagination").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							pagination.decimals = 3;
							pagination.showButtons = false;
						



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Templates]({{slug:templates}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
