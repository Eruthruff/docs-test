---
title: Filtering
meta_title: Filtering
meta_description: description.
slug: 
tags:filtering
publish:True
---


This article explains the changes in the HTML output and additional CSS classes of RadGrid in a scenario with filtering
				enabled.
			

# HTML Output with Filtering Enabled

When filtering is enabled in RadGrid, an anchor (*a*)
					element, which shows the filter icon, is added to the header cell. When a column is sorted, a *span*
					element is inserted in the anchor element.
				


 __html__
    


		<thead>
			<tr>
				<th class="k-header k-filterable">
					<a class="k-grid-filter"></a>
					Header 1
				</th>
				<th class="k-header k-filterable">
					<a class="k-grid-filter"></a>
					Header 2
				</th>
			</tr>
		</thead>



Class/selector name

Description

__.k-header .k-grid-filter__

Grid filter icon whose style is changed for hover and active states.>
									One additional class is applied to the anchor element in some cases. When the filter popup is opened down
									the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-state-border-down</legacyBold> class is added . If the popup is opened up the class added
									to the filter icon is <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-state-border-up</legacyBold>.
								

__k-grid-filter:before__

The actual filter icon. RadGrid uses Segoe UI Symbol as content of the *before* pseudo
								element.
							

# Related Topics

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
