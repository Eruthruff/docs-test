---
title: Scrolling
meta_title: Scrolling
meta_description: description.
slug: 
tags:scrolling
publish:True
---


In most scenarios, the space you will have available for displaying __RadGrid__ records will not be enough to 
				accommodate all of them at the same time. In order to view __RadGrid's__ entire data without the need of an app 
				scrollbar, you can enable vertical scrolling in the grid itself.
			

# Scrolling Modes

Vertical scrolling is enabled by default in RadGrid. Disabling it, or changing the scrolling mode is done using a single property—
					__scrollable__. It accepts the following values:
				

* 

__enabled__: The default value. When set, all grid rows are loaded and a scrollbar appears to navigate 
							through them. Note that, to be scrollable, RadGrid needs to have a __height__ set.
						

* 

__none__: Scrolling is disabled and RadGrid is as high as the total sum of its rows height plus the header height (plus
							group headers/footers height if available).
						

* 

__virtual__: Enables UI virtualization of data. Loads only the items needed for the currently visible position of the 
							scrollable area.
							Perfect for scenarios where you need to visualize large sets of data in tabular form.
						

In the example below, you can see a definition of a RadGrid with scrolling enabled and specific width set.


 __html__
    


				<div id="scrollableGrid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: {
						data: Sample.data,
						group: {field: 'CategoryID'}
					},
					groupable: 'enabled',
					columns: [
	                    { field: 'ID', title: 'First Name' },
	                    { field: 'Name', title: 'Last Name' },
						{ field: 'Price', title: 'Position' }
					],
					scrollable: 'enabled',
					height: 320
				}">
				</div>

![grid-scrolling](../Media/Controls\Grid\grid-scrolling.png)

# Related Topics
