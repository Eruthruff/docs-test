---
title: Visual Structure
meta_title: Visual Structure
meta_description: description.
slug: 
tags:visual,structure
publish:True
---


This article explains the visual elements of the RadCalendar control.

# Visual Structure![calendar-visual-structure](../Media/Controls\Calendar\calendar-visual-structure.png)

# Description of elements

Name

Description

Header

The header is the top element of the calendar, containing the "Prev" and "Next" buttons and the fast navigation.
							

Table

This is the element containing the week names (if in month view) and day cells. It is the visual representation of a view  (month, year, decade,
								century).
							

Footer

The footer is an optionally visible element, which holds a link which allows you to navigate from anywhere to today's date.
							

Navigation buttons

The navigation buttons are used to go to the previous or next view (month, year, etc.) of the calendar.
							

Fast navigation

This is a link, having as text a string representation of the current date. Clicking/tapping it allows the user to navigate between the different
								view levels - from month to year, from year to decade, etc.
							

Column headers

In month view, the column headers display an abbreviated version of the week names.
							

Cells

They correspond to dates in the calendar. They display dates from previous, current and next month and have different states - selected, focused,
								hovered, disabled.
							

# Calendar views / Fast navigation

RadCalendar has four views - month, year, decade and century. They are used to easily navigate through different periods of time. You can see how they
					look in the image below. Switching from a view showing smaller period of time to one showing a larger time period, is done by clicking/tapping the fast
					navigation link button. Navigating to a smaller time period display is done by selecting one of the available periods in the current view.
				![calendar-views](../Media/Controls\Calendar\calendar-views.png)

# Related Topics
