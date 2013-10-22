---
title: Using Templates in RadControls
meta_title: Using Templates in RadControls
meta_description: description.
slug: 
tags:using,templates,in,radcontrols
publish:True
---


Most RadControls support templating parts of their output, allowing you to customize the way information is shown to the user. In this article, you will see
				a list of the controls that support templates, the types of templates they support and examples of the different templating options.
			

# Templates Support in RadControls

The controls which support templates are:

Control Name

String template support

WinJS.Binding.Template support

Function returning a string support

Function returning a DOM element support

__RadAutoCompleteBox__

Yes

Yes

Yes

Yes

__RadCalendar__

Yes

No

No

No
							

__RadChart__

Yes

No

Yes

No, except for __tooltip__ property of series
							

__RadComboBox__

Yes

Yes

Yes

Yes

__RadDatePicker and RadTimePicker__

Yes

Yes

Yes

Yes

__RadDropDownList__

Yes

Yes

Yes

Yes

__RadGauge controls__

Yes

No

Yes

No

__RadGrid__

Yes

No

Yes

No

__RadHubTile controls__

Yes

Yes

Yes

No

__RadPagination__

Yes

Yes

Yes

Yes

__RadTokenInput__

Yes

No

Yes

No
							

The template limitations of some controls are due to their output (for example charts and gauges render SVG, where you cannot
					insert other HTML elements), or by the way their rendering logic is implemented (mostly due to optimizations).
				

# Template Types Examples

For a better understanding of the types of templates and how and when you can use them, see the following examples of their usage.

# String Template

As simple as this may look, you do have control over the logic of displaying content to the user, when using a string template. You can use
							the #= .... # code expression which allows you to input JavaScript logic which should evaluate to a string result. This expression opens a
							JavaScript window during template building that can be used to execute arbitrary JavaScript.
						

In most cases you would use
							the ternary operator (*expression ? result1 : result2*) to get a return value or in case of having a data context,
							you could evaluate the provided variables and append them to your custom strings. Note that you will always have a data context when the
							element you are templating would usually show a dynamic value (the chart's labels, the pickers' items, etc.) even without your template.
						

Following is an example of templating the RadChart series tooltips to display text only when the series value is different than 0.


 __js__
    


					var stringTemplateChart = new Telerik.UI.RadChart(document.getElementById("chart"), {
						dataSource: {
							data: [
								{ Value: 12, Change: 1 },
								{ Value: 22, Change: 3 },
								{ Value: 20, Change: -2 },
								{ Value: 18, Change: 0 },
								{ Value: 14, Change: -5 }
							]
						},
						series: [
						{
							field: 'Value',
							type: 'column',
							labels: {
								visible: true,
								template: "#=dataItem.Change != 0 ? 'Change: ' + dataItem.Change : ''#"
							}
						}
						],
						width: 500,
						height: 350
					});



# WinJS.Binding.Template

Used the same way as with native WinJS controls - provides a reusable declarative binding element, which you can share between different parts
							of the same control or between different controls instances. Of course, you could also just assign a regular DOM element as template to controls
							that support the WinJS Template.
						

In the example below, you can see how the native FlipView and the Telerik RadPagination controls work along with WinJS.Binding.Template
							instances.
						


 __html__
    


				<div id="flipViewItemTemplate" data-win-control="WinJS.Binding.Template" style="display: none">
					<img src="#" data-win-bind="src: picture; alt: title " style="margin-right: 30px" />
					<h2 data-win-bind="innerText: title"></h2>
				</div>
	
				<div id="paginationTemplate" data-win-control="WinJS.Binding.Template" style="display: none">
					<img class="thumbitem" src="#" data-win-bind="src:thumb;" />
				</div>
	
				<div id="flipView1" style="height: 260px"></div>
				<div id="pagination1"></div>




 __js__
    


					var flipView = new WinJS.UI.FlipView(document.getElementById("flipView1"), {
						itemDataSource: DefaultData.bindingList.dataSource,
						itemTemplate: document.getElementById("flipViewItemTemplate")
					});
					var pagination = new Telerik.UI.RadPagination(document.getElementById("pagination1"), {
						pageProvider: document.getElementById("flipView1").winControl,
						itemTemplate: document.getElementById("paginationTemplate").winControl
					});



# Function Returning a String

When the JavaScript logic that you need to process is more complex and writing a string template with this logic would be hard to
							maintain, you could instead use a function that returns a string as a template. You just need to assign the function name as a template and the
							code inside it will be executed when the template is created.
						

The following sample, adds up text to the value axis label in case its value is over a given limit.


 __html__
    


			<div id="lineChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
				series: [
					{ type: 'line', name: 'World', data: [16.7, 20, 15.7, 26.6, 23.5] }
				],
				valueAxis: {
					labels: {
						template: Sample.getLabelTemplate
					}
				},
				height: 300
			}">
			</div>




 __js__
    


		getLabelTemplate: WinJS.Utilities.markSupportedForProcessing(function (item) {
			if (item.value > 20) {
				return item.value + " !!!";
			}
			else {
				return item.value;
			}
		})



# Function Returning a DOM Element

If the content of a DOM element template should depend on different conditions or would change dynamically, you may prefer using a JavaScript function
							which returns a DOM element. This approach is also a good one if you prefer to keep most of your logic, especially related to binding in the .js file.
						


 __js__
    


					var functionAutoComplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("autoComplete"), {
						dataTextField: "CompanyName",
						dataValueField: "CustomerID",
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
						template: Sample.getTemplate,
						height: 230
					});




 __js__
    


		getTemplate: function (item) {
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
	



# Related Topics[WinJS.Binding.Template object](http://msdn.microsoft.com/en-us/library/windows/apps/br229723.aspx)

 * [Templates]({{slug:templates}})

 * [Day Template]({{slug:day-template}})

 * [Tooltip]({{slug:tooltip}})

 * [Templates]({{slug:templates}})

 * [Templates]({{slug:templates}})

 * [Overview]({{slug:overview}})

 * [Templates]({{slug:templates}})

 * [Templates]({{slug:templates}})

 * [Tooltip]({{slug:tooltip}})

 * [Tooltips]({{slug:tooltips}})

 * [Item Template]({{slug:item-template}})

 * [Tag Template]({{slug:tag-template}})
