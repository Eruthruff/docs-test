---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


__RadPagination__ for Windows 8 is an HTML/JavaScript component that uses lightweight HTML rendering that maximizes
				loading performance, yet keeps the control flexible when changing styles and layout is required.
			

# HTML Output

__RadPagination__ renders four main parts - the __"previous" button__, __the "next" button__,
					__the thumbnails list__ and the __label__. Here is the HTML output of a sample
					__RadPagination__ instance showing four available pages, with the first one selected:
				


 __html__
    


	        <div class="t-pagination" data-win-control="Telerik.UI.RadPagination">
	            <button class="t-button t-prev"></button>
	            <button class="t-button t-next"></button>
	            <div class="t-thumbnails t-default">
	                <ul>
	                    <li class="t-selected">
	                        <div class="t-item"></div>
	                    </li>
	                    <li class="t-after-selected">
	                        <div class="t-item"></div>
	                    </li>
	                    <li>
	                        <div class="t-item"></div>
	                    </li>
	                    <li>
	                        <div class="t-item"></div>
	                    </li>
	                </ul>
	            </div>
	            <span class="t-label">
	                <span>1</span>
	                <span>/</span>
	                <span>4</span>
	            </span>
	        </div>



# CSS Classes

RadPagination uses the following CSS classes on its HTML elements:
				

CSS class/selector

Target HTML element / Description

__.t-pagination__

The HTML host element that defines the __data-win-control__ attribute.
							

__.t-pagination .t-button__

The prev/next button.
							

__.t-pagination .t-button.t-prev__

The previous page button.
							

__.t-pagination .t-button.t-next__

The next page button.
							

__.t-pagination .t-thumbnails__

The thumbnails list.
							

__.t-pagination .t-thumbnails.t-default__

The thumnbails list with default rendering (no user-defined template).
							

__.t-pagination .t-thumbnails.t-custom__

The thumnbails list with a custom user-defined template.
							

__.t-pagination .t-thumbnails .t-item__

A thumbnail item with default (no template) rendering.
							

__.t-pagination .t-thumbnails .t-item.t-selected__

The selected list item.
							

__.t-pagination .t-thumbnails .t-item.t-after-selected__

The item immediately to the right of the selected item.
							

__.t-pagination .t-label__

The page index label.
							

__.t-pagination.t-disabled, .t-pagination .t-thumbnails.t-disabled__

Applied to the host HTML element (__.t-pagination__) and the thumbnails
								list element (__.t-thumbnails__) when the control is disabled.
							

# Related Topics

 * [Customizing Layout with CSS]({{slug:customizing-layout-with-css}})
