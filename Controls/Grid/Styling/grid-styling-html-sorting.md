---
title: Sorting
meta_title: Sorting
meta_description: description.
slug: 
tags:sorting
publish:True
---


This article explains the changes in the HTML output and additional CSS classes of RadGrid in a scenario with sorting
				enabled.
			

# HTML Output with Sorting Enabled

When sorting is enabled in RadGrid, the content in header cells is wrapped in an anchor (*a*)
					element. When a column is sorted in RadGrid, a *span* element is inserted in the anchor element.
				


 __html__
    


		<thead>
			<tr>
				<th class="k-header">
					<a class="k-link">Header 1</a>
				</th>
				<th class="k-header">
					<a class="k-link">Header 2
						<span class="k-icon k-i-arrow-n"></span>
					</a>
				</th>
				<th class="k-header">
					<a class="k-link">Header 3
						<span class="k-icon k-i-arrow-s"></span>
					</a>
				</th>
			</tr>
		</thead>



# CSS Classes/Selectors

Class/selector name

Description

__.k-header .k-link__

The wrapper, which holds the content of the sortable column header.

__.k-header .k-link .k-i-arrow-n__

The icon indicator, which shows that the column is sorted in ascending order.

__.k-header .k-link .k-i-arrow-s__

The icon indicator, which shows that the column is sorted in descending order.

# Related Topics

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
