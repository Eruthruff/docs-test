---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadGrid control for Windows 8 is a powerful HTML/JavaScript component for visualizing tabular data. It provides a rich set of features - paging, sorting,
				filtering, grouping, virtual scrolling, etc. Enabling these requires minimum effort and saves you loads of time for achieving the same result from scratch.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadGrid

To create a RadGrid in the HTML markup, add an empty div element with a data-win-control attribute with value of Telerik.UI.RadGrid.
							Since RadGrid is a control that depends on data to create its structure, you should also assign it a data source in order to get a
							visible representation of the control.
						

	
							<div id="myGrid" data-win-control="Telerik.UI.RadGrid"></div>
						



You can achieve the same result in JavaScript—just define the host div element on the page and then instantiate a new RadGrid
							by passing a reference to the div DOM object in the control constructor:
						

	
							var grid = new Telerik.UI.RadGrid(document.getElementById("myGrid"));
						



The examples above will not render a usable __RadGrid__ control. All data-bound controls need at least a basic 
              set of data that they have to display. You can see a basic setup of __RadGrid__ in the section below.
            

# optionsSetting RadGrid Options

Same as with the rest of the Windows Runtime JavaScript controls, RadGrid's properties can be set through the data-win-options attribute of
							the host element:
						


 __html__
    


				<div id="markupGrid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
						dataSource: {
							data: [
								{ OrderID: 1, ShipCity: 'Sofia' },
								{ OrderID: 2, ShipCity: 'London' },
								{ OrderID: 3, ShipCity: 'Madrid' }
							]
						},
						selectable: 'row'
						}"></div>



In JavaScript, you can pass an options object as a second argument to the RadGrid constructor:


 __html__
    


				<div id="codeGrid"></div>




 __js__
    


				    var grid = new Telerik.UI.RadGrid(document.getElementById("codeGrid"), {
				        dataSource: {
				            data: [
	                            { OrderID: 1, ShipCity: 'Sofia' },
	                            { OrderID: 2, ShipCity: 'London' },
	                            { OrderID: 3, ShipCity: 'Madrid' }
				            ]
				        },
				        selectable: 'row'
				    });



Both of the examples produce the same output. Here is an image of the resulting __RadGrid__.
            ![grid-gettingstarted](../Media/Controls\Grid\grid-gettingstarted.png)

# reference
						Referencing the RadGrid Control Instance
					

As described in
							[this MSDN article about adding controls to a Windows Store app](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493.aspx), any control in a Windows Runtime JavaScript application requires a call to
							__WinJS.UI.processAll()__ for proper initialization. The same holds true for any of the Telerik UI controls. Once
							the WinJS framework has initialized all the controls on the page, the RadGrid control instance associated with a host HTML element can be
							retrieved using the winControl expando property of the host HTML element.
						

	Define your grid control in the HTML



	
							WinJS.Utilities.ready(function () {
								WinJS.UI.processAll().then(function () {
									//wait for the processAll() method to finish, then find the
									//grid control from the host element's winControl property
									var gridElement = document.getElementById("myGrid");
									var myGridControl = gridElement.winControl;
									console.log(myGridControl instanceof Telerik.UI.RadGrid); //true
								});
							});
						



# propertiesModifying RadGrid Properties

Once RadGrid is loaded and the control is referenced in JavaScript, the control exposes an extensive set of properties methods and events.
							When a RadGrid property is modified, for the changes to take effect, the refresh() method of the control needs to be called. This re-initializes
							and rebinds RadGrid with the modified properties.
						

	
							args.setPromise(WinJS.UI.processAll().then(function () {
								var grid = document.getElementById("myGrid").winControl;
								grid.selectable = "row";
								grid.refresh();
							}));
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches.
						

	
							var grid = new Telerik.UI.RadGrid(document.getElementById("myGrid"), {
								ondatabound: dataBoundHandlerFnName 
							});
							// OR
							var grid = new Telerik.UI.RadGrid(document.getElementById("myGrid"), {
							ondatabound: function(e) {//...}
							});
						

>
								If you attach the event handler as shown above, but in HTML mark-up, you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							grid.addEventListener("databound", dataBoundHandlerFnName);
						



# Related Topics

 * [Data Binding Overview]({{slug:data-binding-overview}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Rows]({{slug:rows}})

 * [Overview]({{slug:overview}})

 * [Overview]({{slug:overview}})

 * [Overview]({{slug:overview}})

 * [Declarative Hierarchy]({{slug:declarative-hierarchy}})

 * [Overview]({{slug:overview}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Events]({{slug:events}})

 * [Best Practices]({{slug:best-practices}})
