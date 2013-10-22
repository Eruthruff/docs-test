---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The __RadChart__ control for Windows 8 is a HTML/JavaScript component that uses SVG to render high-quality data visualizations. 
        It provides a rich set of APIs for visualizing data in different types of data series. This article describes how to get started with using RadChart.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to a HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a Chart

To create a __RadChart__ in the HTML markup, add an empty __div__ element with a 
              __data-win-control__ attribute with value of __Telerik.UI.RadChart__:
						

	
							<div data-win-control="Telerik.UI.RadChart">
							</div>
						



Alternatively, you can create __RadChart__ programmatically through JavaScript by first defining a __div__ element
							with an id and then passing it as a first argument to the __Telerik.UI.RadChart__ constructor:
						

	
							<div id="myChart">
							</div>
						



	
							var chart = new Telerik.UI.RadChart(document.getElementById("myChart"));
						



Defining __RadChart__ without any properties set will not render a usable control. Without data __RadChart__ 
              cannot serve its purpose to show it. Therefore, you need to at least specify a __dataSource__. The rest of 
              __RadChart__'s properties will be set to their default values. You can see a basic example of defining a usable 
              __RadChart__ in the next step.
            

# optionsSetting Chart Options

Just like any other Windows Runtime JavaScript control, __RadChart__ options can be defined through the 
              __data-win-options__ attribute:
						


 __html__
    


				<div id="markupChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: [
								{ year: '2000', sales: 200 },
								{ year: '2001', sales: 450 },
								{ year: '2003', sales: 125 }]
							},
							series: [
								{ type: 'line', field: 'sales', name: 'Sales' }
							],
							categoryAxis: {
								field: 'year'
							},
	                        theme: 'light'
						}">
				</div>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						


 __html__
    


				<div id="codeChart"></div>




 __js__
    


				    var chart = new Telerik.UI.RadChart(document.getElementById("codeChart"), {
				        dataSource: {
				            data: [
	                        { year: '2000', sales: 200 },
	                        { year: '2001', sales: 450 },
	                        { year: '2003', sales: 125 }]
				        },
				        series: [
	                        { type: 'line', field: 'sales', name: 'Sales' }
				        ],
				        categoryAxis: {
				            field: 'year'
				        },
	                    theme: "light"
				    });



For detailed information regarding __RadChart__'s properties refer to the related articles at the bottom of the article.
            

Both the examples produce the same output. You can see the chart below.
            ![chart-gettingstarted](../Media/Controls\Chart\chart-gettingstarted.png)

# referencingReferencing the RadChart Control Instance

As described in
							[this MSDN article about adding controls to a Windows Store app](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493.aspx),
							any control in a Windows Runtime JavaScript application requires a call to __WinJS.UI.processAll()__ for proper
							initialization. The same holds true for any of the Telerik UI controls. Once, the WinJS framework has initialized all the controls
							on the page, the __RadChart__ control instance associated with a host HTML element can be retrieved using the 
              __winControl__ expando property of the host HTML element.
						

	
							<!--Define your chart control in the HTML-->
							<div id="myChart" data-win-control="Telerik.UI.RadChart">
							</div>
						



	
							WinJS.Utilities.ready(function () {
								WinJS.UI.processAll().then(function () {
									//wait for the processAll() method to finish, then find the
									//chart control from the host element's winControl property
									var chartElement = document.getElementById("myChart");
									var myChartControl = chartElement.winControl;
									console.log(myChartControl instanceof Telerik.UI.RadChart); //true
								});
							});
						



# propertiesModifying Chart Properties

All __RadChart__ properties are configurable either through the __data-win-options__ attribute, 
              or programmatically through the JavaScript control instance. For example, you can enable chart tooltips with the following definition in the mark-up:
						

	
							<div id="myChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
								tooltip: {
									visible: true
								}
								...
							}">
							</div>
						



Once __RadChart__ is loaded and the control is referenced in JavaScript, the control exposes an extensive set of 
              properties methods and events. After a chart property is modified, for the changes to take effect, the __refresh()__ 
              method of the control needs to be called. This re-initializes and rebinds the chart with the modified properties.
						

	
							var chart = document.getElementById("myChart").winControl; //myChart is the host HTML element
							chart.tooltip.visible = true;   //modify properties
							chart.refresh();                //call refresh() to update
						



To see all available configuration options, look at the members, constructors, methods, properties and events available for the 
							T:Telerik.UI.RadChart class.
						

# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var chart = new Telerik.UI.RadChart(document.getElementById("myChart"), {
								onserieshover: changeHandlerFnName });
							// OR
							var chart = new Telerik.UI.RadChart(document.getElementById("myChart"), {
								onserieshover: function(e) {//...}
							});
						

>
								If you attach the event handler as shown above, in HTML mark-up, you need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							chart.addEventListener("serieshover", serieshoverHandlerFnName);
						



# Related Topics

 * [Data Binding]({{slug:data-binding}})

 * [Common Configuration]({{slug:common-configuration}})

 * [Common Configuration]({{slug:common-configuration}})

 * [Chart Legend]({{slug:chart-legend}})

 * [Tooltip]({{slug:tooltip}})

 * [Events]({{slug:events}})[How to Work with RadChart in a JavaScript-based Application for Windows 8 (Telerik Helper blog)](http://telerikhelper.net/2012/12/19/how-to-work-with-radchart-in-javascript-based-application-for-windows-8/)
