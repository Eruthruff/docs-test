---
title: Customize Borders
meta_title: Customize Borders
meta_description: description.
slug: 
tags:customize,borders
publish:True
---


This help article lists various scenarios for customizing the RadCalendar borders.

# Section1Customize all borders

There are a few changes that you need to make in RadCalendar's in order to get all borders width. They are shown in the listing below, where RadCalendar's
					border width is decreased to 1 px:
				


 __none__
    


	.t-calendar,
	.k-calendar .k-header,
	.k-calendar .k-content th,
	.k-calendar .k-footer,
	.k-calendar .k-content td,
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		border-width: 1px;
	}
	
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		top: -1px; /* 1px - Same as the border width */
		left: -1px; /* 1px - Same as the border width */
	}

![calendar-style-borders-all](../Media/Controls\Calendar\calendar-style-borders-all.png)

If you want to also change the colors of the borders, you can split the first rule into a few parts and give them colors of your choice. The first
					four selectors, target all regular borders in the calendar. The next four target borders of cells in a specific state. The styles below provide purple
					borders for the calendar and magenta ones for today's date cell:
				


 __none__
    


	.t-calendar,
	.k-calendar .k-header,
	.k-calendar .k-content th,
	.k-calendar .k-footer,
	.k-calendar .k-content td {
		border-color: #a081d9;
	}
	
	
	.k-calendar .k-content .k-today:before {
		border-color: #d821c3;
	}

![calendar-style-borders-all-color](../Media/Controls\Calendar\calendar-style-borders-all-color.png)

# Customize state borders

Based on the user actions, the calendar cells can be in different states. If you want to customize only cells in states different than the default one,
					you can use the state classes in your selectors. For example, to change the width of cells in selected, hovered and focused states, along with the today's
					date cell, to 3px you can use the following:
				


 __none__
    


	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		border-width: 3px;
	}
	
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		top: -3px; /* 3px - Same as states (today, selected, hover, focus) border width */
		left: -3px; /* 3px - Same as states (today, selected, hover, focus) border width */
	}



As mentioned in the previos section, customizing the states border color is achieved by using the same state selectors as those used for changing the
					width. For example, the following styles provide yellow color for today's date, magenta for the selected date and green for hovered dates.
				


 __none__
    


	.k-calendar .k-content .k-today:before {
		border-color: #ffc300;
	}
	
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-focused:before {
		border-color: #d821c3;
	}
	
	.k-calendar .k-content .k-state-hover:before {
		border-color: #3eb408;
	}



When the two sets of styles from this section are combined, the calendar will look like this:
				![calendar-style-borders-states](../Media/Controls\Calendar\calendar-style-borders-states.png)

# Customize inner borders

To change only the borders of inner cells, you can use the __k-content__ CSS class in your selectors and target only
					*td* elements (without *th* ones). For example, to change the border width of only cells in the view, use:
				


 __none__
    


	.k-calendar .k-content td,
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		border-width: 1px;
	}
	
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		top: -1px; /* 1px - same as the border width */
		left: -1px; /* 1px - same as the border width */
	}



To change the color of these borders, you need only the first selector from the above snippet:


 __none__
    


	.k-calendar .k-content td {
		border-color: #33ccff;
	}



If you use the above two snippets combined, the resulting calendar will look like this:![calendar-style-borders-inner](../Media/Controls\Calendar\calendar-style-borders-inner.png)

# Remove borders

# Remove horizontal borders

To remove horizontal borders in RadCalendar, you can directly paste the following CSS in your app's styles:


 __none__
    


	.k-calendar .k-content td {
		border-bottom-width: 0;
	}
	
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before,
	.k-calendar .k-content.t-animation-grid td:before {
		height: calc(100% - 2px); /* 2px - same as the states (today, selected, hover, focus) border width */
	}
	
	.k-calendar .k-content tr:last-child > td:before {
		height: 100%;
	}



The result will look like this:![calendar-style-borders-hide-horizontal](../Media/Controls\Calendar\calendar-style-borders-hide-horizontal.png)

# Remove vertical borders

To remove vertical borders in RadCalendar, you can use these styles:


 __none__
    


	.k-calendar .k-content td {
		border-left-width: 0;
	}
	
	.k-calendar .k-content .k-today:before,
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before {
		width: calc(100% - 2px); /* 2px - same as the states (today, selected, hover, focus) border width */
	}
	
	.k-calendar .k-content td:last-child:before {
		width: 100%;
	}



The result is:![calendar-style-borders-hide-vertical](../Media/Controls\Calendar\calendar-style-borders-hide-vertical.png)

# Remove inner borders

To remove inner borders, paste the following CSS in your app's styles:


 __none__
    


	.k-calendar .k-content td {
		border-width: 0px;
	}
	
	.k-calendar .k-content .k-today:before, 
	.k-calendar .k-content .k-state-selected:before,
	.k-calendar .k-content .k-state-hover:before,
	.k-calendar .k-content .k-state-focused:before,
	.k-calendar .k-content.t-animation-grid td:before  {
		height: calc(100% - 2px); /* 2px - the width of the states (today, selected, hovered, focused) borders */
		width: calc(100% - 2px); /* 2px - the width of the states (today, selected, hovered, focused) borders */
	}
	
	.k-calendar .k-content tr:last-child > td:before {
		height: 100%;
	}
	
	.k-calendar .k-content td:last-child:before {
		width: 100%;
	}



The result will look like this:![calendar-style-borders-hide-inner](../Media/Controls\Calendar\calendar-style-borders-hide-inner.png)

# 

This implementation is part of our
        [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
        [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Calendar/CustomizeBorders*.
      

# Related Topics

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
