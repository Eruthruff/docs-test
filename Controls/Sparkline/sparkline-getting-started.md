---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


__RadSparkline__ is a tailored version of the RadChart implementation that allows you to display simple, word-sized graphics that
        can be embedded in different places—text, tables, headlines, etc. This help article will help you get started with using the 
        __RadSparkline__ control.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadSparkline

To create a __RadSparkline__ in the HTML markup, add an empty __span__ element with a data-win-control
              attribute with value of __Telerik.UI.RadSparkline__.
						

	
							<span id="sparkline1" data-win-control="Telerik.UI.RadSparkline"></span>
						



You can achieve the same result in JavaScript—just define the host span element on the page and then instantiate a new __RadSparkline__
							by passing a reference to the span DOM object in the control constructor:
						

	
							var sparkline = new Telerik.UI.RadSparkline(document.getElementById("sparkline1"));
						



Creating a __RadSparkline__ without setting any options will not result in a usable control. __RadSparkline__ 
              needs at least a basic set of data that it has to visualize. You can find a basic example of how you can set property values below.
            

# optionsSetting RadSparkline Options

Same as with the rest of the Windows Runtime JavaScript controls, __RadSparkline__'s properties can be set through the 
              __data-win-options__ attribute of the host element:
						

	
              <span class="control" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
	              data: [22, 13, 37, 42, 12],
	              type: 'column',
	              height: 50,
	              width: 100
              }"></span>
						



In JavaScript, you can pass an options object as a second argument to the __RadSparkline__ constructor:

	
              var sparkline = new Telerik.UI.RadSparkline(document.getElementById("mySparkline"), {
                  data: [22, 13, 37, 42, 12],
                  type: "column",
                  height: 50,
                  width: 100
              });
            



Here is an image of the produced __RadSparkline__ control:
            ![sparkline-gettingstarted](../Media/Controls\Sparkline\sparkline-gettingstarted.png)

# reference
						Referencing the RadSparkline Control Instance
					

As described in
							[this MSDN article about adding controls to a Windows Store app](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493.aspx), any control in a Windows Runtime JavaScript application requires a call to
							__WinJS.UI.processAll()__ for proper initialization. The same holds true for any of the Telerik UI controls. Once
							the WinJS framework has initialized all the controls on the page, the __RadSparkline__ control instance associated 
              with a host HTML element can be retrieved using the winControl expando property of the host HTML element.
						

	Define your RadSparkline control in the HTML



	
							WinJS.Utilities.ready(function () {
								WinJS.UI.processAll().then(function () {
									//wait for the processAll() method to finish, then find the
									//sparkline control from the host element's winControl property
									var sparklineElement = document.getElementById("mySparkline");
									var mySparklineControl = sparklineElement.winControl;
									console.log(mySparklineControl instanceof Telerik.UI.RadSparkline); //true
								});
							});
						



# propertiesModifying RadSparkline Properties

Once __RadSparkline__ is loaded and the control is referenced in JavaScript, it exposes an extensive set of 
              properties, methods and events.
						

	
							args.setPromise(WinJS.UI.processAll().then(function () {
								var sparkline = document.getElementById("mySparkline").winControl;
								sparkline.tooltip.font = "9pt Segoe UI";
							}));
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var sparkline = new Telerik.UI.RadSparkline(document.getElementById("mySparkline"), {
								ondatabound: databoundHandlerFnName
							});
							// OR
							var sparkline = new Telerik.UI.RadSparkline(document.getElementById("mySparkline"), {
								ondatabound: function(e) {//...}
							});
						

>
								If you attach the event handler using the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">on[eventname]</legacyBold> property in HTML mark-up, you would need to mark the handler
								function as safe in your JavaScript code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							sparkline.addEventListener("databound", databoundHandlerFnName);
						



# Related Topics

 * [Data Binding]({{slug:data-binding}})

 * [Types]({{slug:types}})

 * [Axes]({{slug:axes}})

 * [Tooltips]({{slug:tooltips}})

 * [Plot Bands]({{slug:plot-bands}})
