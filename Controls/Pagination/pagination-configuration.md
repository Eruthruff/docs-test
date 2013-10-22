---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article, describes the configuration options of the RadPagination control.

# Section1Assigning a Pageable Control

To start using a RadPagination control, you should assign it a control to page, for example a FlipView. To do so, set the
					__pageProvider__ property value to point to the paged control instance:
				


 __html__
    


				<div id="flipView1" data-win-control="WinJS.UI.FlipView" style="width: 500px; height: 250px" data-win-options="{ 
					itemDataSource: DefaultData.bindingList.dataSource, 
					itemTemplate: select('#flipViewItemTemplate') 
				}">
				</div>
				<div id="pagination1" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView1')
				}">
				</div>



Here, *DefaultData.bindingList* is of type __WinJS.Binding.List__ and is defined like this for the purpose 
					of the example.
				


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



Once RadPagination is associated with a pageable control, it can perform the following actions:
				

* 

Receive notifications when the current page changes and update its own UI—thumbnails and index label

* 

Navigate the pageable control in response to user action—clicking prev/next buttons and thumbnail items.

# Providing a Template for the Thumbnails

You can define a template that will be used for rendering the thumbnail items. This is done through the
					__itemTemplate__ property, which accepts:
				

* 

A WinJS.BindingTemplate instance or an HTML element hosting a template.

* 

A function returning an HTML string or a DOM element.

* 

An HTML string with binding expressions defining the template.
						

The code sample that follows uses a WinJS.BindingTemplate instance:


 __html__
    


			<div id="paginationTemplate" data-win-control="WinJS.Binding.Template" style="display: none">
				<img class="thumbitem" src="#" data-win-bind="src:thumb;" />
			</div>




 __html__
    


				<div id="pagination2" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView2'),
					itemTemplate: select('#paginationTemplate')
				}">
				</div>

![Providing item template](../Media/Controls\Pagination\pagination-item-template.png)

For more information and code samples, click to view the
					[Templates help article](59c4c80d-dd61-4578-961c-25eb198a207c).
				

# Controlling Visibility of Elements

It is up to you to decide which parts of the pagination controls should be visible. To hide its page buttons, label or thumbnails, set
					the __showButtons__, __showLabel__ and __showThumbnails__ properties,
					respectively, to false. They are all set to true by default.
				


 __html__
    


				<div id="pagination3" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView3'),
					itemTemplate: select('#paginationTemplate'),
					showButtons: false
				}">
				</div>



The code sample above hides page navigation buttons and will leave only the thumbnails as the means for flipping the views.![Hide buttons](../Media/Controls\Pagination\pagination-hide-buttons.png)

# Customizing the Page Index Label

You could customize the content of the label saying "X/Y" next to the RadPagination control. To do so, use the
					__label.template__ property. The available values are __page__, __count__ and
					__separator__.
				


 __html__
    


				<div id="pagination4" data-win-control="Telerik.UI.RadPagination" data-win-options="{
					pageProvider: select('#flipView4'),
					label: {
						template: 'Item #=page# of #=count#'
					}
				}">
				</div>

![Providing label template](../Media/Controls\Pagination\pagination-label-template.png)

# Disabling the Control

To prevent user-defined paging for the RadPagination control, set its __enabled__ property to
					__false__. Once you do so, only programmatic navigation of the control is possible. This can be done using the
					__prev()__ and __next()__ methods, which navigate to the previous and next item respectively;
					or by changing the __currentIndex__ property value.
				


 __html__
    


				<div id="pagination5" data-win-control="Telerik.UI.RadPagination" data-win-options="{
						pageProvider: select('#flipView5'),
						itemTemplate: select('#paginationTemplate'),
						enabled: false
					}">
				</div>



# Related Topics
