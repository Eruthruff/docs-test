---
title: Templates
meta_title: Templates
meta_description: description.
slug: 
tags:templates
publish:True
---


All tile components support content templates for their back side. Some components, like the RadSlideHubTile or RadCustomHubTile, also support
				templates for the front side.
			

Since Q1 2013, RadHubTile supports all template options, listed in the common [Templates article](a27cfadb-2990-4c07-be2a-8557b9cf722e);
				namely an HTML string, a WinJS.Binding.Template (or a static DOM element), and a function returning a string or a DOM element.
			

# Using String as a Template

Here is an example of how to set templates for the RadCustomHubTile using an HTML string and an element:
				


 __html__
    


				<div id="customTile2" data-win-control="Telerik.UI.RadCustomHubTile" data-win-options="{
						frontContentTemplate: '&lt;h2 style=&quot;padding: 10px &quot;&gt;Front Title&lt;/h2&gt; &lt;h4 style=&quot;padding: 10px &quot;&gt;Some content inside the front side of the custom hub tile&lt;/h4&gt;',
						backContentTemplate: '&lt;h2 style=&quot;padding: 10px &quot;&gt;Back Title&lt;/h2&gt; &lt;h4 style=&quot;padding: 10px &quot;&gt;Some content inside the back side of the custom hub tile&lt;/h4&gt;'
					}">
				</div>

![Templated tile](../Media/Controls\HubTile\hubtile-templates-2.png)>
						If you specify the string template in HTML, you
						may need to use HTML-encoded characters to get matching quotation marks. In this case you will need to replace the quotations
						in the template value shown below with a matching
						<externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>HTML entity</linkText><linkUri>http://www.ascii.cl/htmlcodes.htm</linkUri></externalLink>.
					

# 
				Using an Element as a Template
			

If the template declaration is too complex for encoding into a string, you can simply declare it inside a hidden element in your HTML and assign a
					reference to this element to the respective template property:
				


 __html__
    


				<div id="customTile1" style="background-color: white; color: black" data-win-control="Telerik.UI.RadCustomHubTile" data-win-options="{
					frontContentTemplate:select('#frontCustomTemplate1'), 
					backContentTemplate:select('#backCustomTemplate1')
					}">
				</div>
				<div id="frontCustomTemplate1" style="display: none;">
					<div style="display: -ms-grid; -ms-grid-columns: 1fr 2fr; -ms-grid-column-align: end; padding-right: 10px">
						<div style="-ms-grid-column: 2; text-align: right">
							<h2>Red Wine</h2>
							<img src="/images/food/5.jpg" alt="Red Wine" height="85" />
						</div>
					</div>
				</div>
				<div id="backCustomTemplate1" style="display: none;">
					<div style="display: -ms-grid; -ms-grid-columns: 3fr 1fr; -ms-grid-column-align: end; padding-left: 10px">
						<div style="-ms-grid-column: 1; text-align: left">
							<h2>Gummy bears</h2>
							<img src="/images/food/4.jpg" alt="Gummy bears" height="85" />
						</div>
					</div>
				</div>

![Templated tile](../Media/Controls\HubTile\hubtile-templates-1.png)>
						If you update the element you use for template after the tile is rendered, the changes will not be
						reflected in the tile. In this case you will need to set the template property again which will cause the control to refresh.
					

# Using a WinJS.Binding.Template Instance

If you have a WinJS template already declared that you want to reuse in RadHubTile, assign a reference to it and the control will pick it. Note, however,
					that the hub tile controls do not have a binding context, so in most cases the usage of this control's instance is not necessary.
				


 __html__
    


				<div id="customTile3" style="background-color: white; color: black">
				</div>
				<div id="frontTemplate" data-win-control="WinJS.Binding.Template">
					<div style="display: -ms-grid; -ms-grid-columns: 1fr 2fr; -ms-grid-column-align: end; padding-right: 10px">
						<div style="-ms-grid-column: 2; text-align: right">
							<h2>Red Wine</h2>
							<img src="/images/food/5.jpg" alt="Red Wine" height="85" />
						</div>
					</div>
				</div>
				<div id="backTemplate" data-win-control="WinJS.Binding.Template">
					<div style="display: -ms-grid; -ms-grid-columns: 3fr 1fr; -ms-grid-column-align: end; padding-left: 10px">
						<div style="-ms-grid-column: 1; text-align: left">
							<h2>Gummy bears</h2>
							<img src="/images/food/4.jpg" alt="Gummy bears" height="85" />
						</div>
					</div>
				</div>




 __js__
    


					var bindingTemplateTile = new Telerik.UI.RadCustomHubTile(document.getElementById("customTile3"), {
						frontContentTemplate: document.getElementById("frontTemplate").winControl,
						backContentTemplate: document.getElementById("backTemplate").winControl
					});

![Templated tile](../Media/Controls\HubTile\hubtile-templates-1.png)

# Using a Function Returning a String

If the displayed content depends on some conditions or is generated using live data, you can use a JavaScript function to set it. A simple example is shown
					below:
				


 __js__
    


					var functionTemplateTile = new Telerik.UI.RadHubTile(document.getElementById("customTile4"), {
						message: '<h2>The weather today</h2>',
						backContentTemplate: HubTileTemplates.backTemplate
					});




 __js__
    


	WinJS.Namespace.define("HubTileTemplates", {
		backTemplate: WinJS.Utilities.markSupportedForProcessing(function () {
			//here the content of the wrapper DIV can be determined by some live data
			//for simplicity, the template below is hard-coded
			var template = "<div style='margin-left: 90px'><h2>Sunny</h2><img src='/images/sun.png'/></div>";
			return template;
		})
	});

![hubtile-templates-3](../Media/Controls\HubTile\hubtile-templates-3.png)

# Related Topics

 * [Using Templates in RadControls]({{slug:using-templates-in-radcontrols}})
