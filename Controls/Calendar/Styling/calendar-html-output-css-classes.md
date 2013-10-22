---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of RadCalendar in a basic scenario. You can use this information when providing custom styles for
				the control or when trying to access a specific element from the control output.
			

# Section1Basic output of RadCalendar

The HTML output of a simple RadCalendar control is the following (some HTML attributes have been removed for simplicity):


 __html__
    


	<div class="t-calendar" data-win-control="Telerik.UI.RadCalendar">
		<div class="k-widget k-calendar">
			<div class="k-header">
				<a class="k-link k-nav-prev">
					<span class="k-icon k-i-arrow-w"></span>
				</a>
				<a class="k-link k-nav-fast">April 2013</a>
				<a class="k-link k-nav-next">
					<span class="k-icon k-i-arrow-e"></span>
				</a>
			</div>
			<!-- .k-header -->
			<table class="k-content">
				<thead>
					<tr>
						<th>Su</th>
						<th>Mo</th>
						<th>Tu</th>
						<th>We</th>
						<th>Th</th>
						<th>Fr</th>
						<th>Sa</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td class="k-other-month k-weekend">
							<a class="k-link">31</a>
						</td>
						<td>
							<a class="k-link">1</a>
						</td>
						<td>
							<a class="k-link">2</a>
						</td>
						<td>
							<a class="k-link">3</a>
						</td>
						<td>
							<a class="k-link">4</a>
						</td>
						<td>
							<a class="k-link">5</a>
						</td>
						<td class="k-weekend">
							<a class="k-link">6</a>
						</td>
					</tr>
					<!--rest of the days from this month-->
					...
					<tr>
						<td class="k-weekend">
							<a class="k-link">28</a>
						</td>
						<td>
							<a class="k-link">29</a>
						</td>
						<td>
							<a class="k-link">30</a>
						</td>
						<td class="k-other-month">
							<a class="k-link">1</a>
						</td>
						<td class="k-other-month">
							<a class="k-link">2</a>
						</td>
						<td class="k-other-month">
							<a class="k-link">3</a>
						</td>
						<td class="k-other-month k-weekend">
							<a class="k-link">4</a>
						</td>
					</tr>
					<!--rest of other month days -->
				</tbody>
			</table>
			<!-- .k-content -->
			<div class="k-footer">
				<a title="Tuesday, April 16, 2013" class="k-link k-nav-today" href="#">Tuesday, April 16, 2013</a>
			</div>
			<!-- .k-footer -->
		</div>
		<!--.k-calendar.k-widget -->
	</div>
	<!-- .t-calendar -->



The following sections list the classes and their usage, grouped by the part of RadCalendar they belong to.

# Main structure

Class/selector name

Description

__.t-calendar__

The RadCalendar wrapper element (the one that is passed in the control’s constructor).

__.k-calendar.k-widget__

The wrapper of the calendar widget.

__.t-calendar .k-header__

The wrapper element of RadCalendar’s fast navigation.

__.t-calendar .k-footer__

The wrapper element of RadCalendar’s footer.

__.t-calendar .k-content__

The table element holding RadCalendar’s current view (content).

# Header structure

Class/selector name

Description

__.t-calendar .k-header .k-nav-prev __

The RadCalendar wrapper element (the one that is passed in the control’s constructor).

__.t-calendar .k-header .k-nav-fast __

Fast navigation button.

__.t-calendar .k-header .k-nav-next__

Next button of the fast navigation.

These buttons are link (<a>) elements, which acquire two more class names, based on their state:

Class/selector name

Description

__.k-state-hover__

This class is added when the mouse is over one of the links.

__.k-state-disabled __

This class is added when the max or min date in the view is visible and there are visible cells after it, which cannot be selected.

# Footer structure

Class/selector name

Description

__.t-calendar .k-footer .k-nav-today__

Today button in RadCalendar's footer.

# Content structure

# Month view

In month view there are a table header (<thead>) with short days names and a table body (<tbody>) with 6 rows, 7 cells on a row, which
							represent all days in the month and some additional days before and after the month.
							Each cell has a link (<a>) with __.k-link__ class assigned, which is the actual element that represents the content
							of the cell.
						

There are a few other class names applied to the cells, based on their state or usage:

Class/selector name

Description

__.k-other-month__

Cells with dates from another month (previous or next to the current month).

__.k-weekend__

Cells which represent the weekend days.

__.k-today__

Today’s day cell.

__.k-state-selected__

Selected cell in the calendar

__.k-state-hover__

Hovered cells in the calendar.

__.k-state-focused__

Focused cells in the calendar.

# Meta view

Meta views are all other view in RadCalendar -year view, decade view and century view. In these views, the table (the one having
							__.k-content__ class name) does not have a header. It only holds 6 rows with 2 cells in each that represent
							months,  years or decades, depending on the current view.
						

Again, each cell has a link (<a>) which is the actual element that represents the content of the cell and has a
							__.k-link__ class assigned.
						

Each cell can have the selected, hovered and focused states (classes) listed in the previous section.

# Related Topics
