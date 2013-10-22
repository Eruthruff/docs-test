---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of RadGrid in a basic scenario, without any features
				enabled.
			

# Section1Basic HTML Output

The HTML output of a simple RadGrid control without any client features is the following (some HTML attributes have
					been removed for simplicity):
				


 __html__
    


		<div class="t-table-view" data-win-control="Telerik.UI.RadGrid">
			<div class="k-grid k-widget">
				<div class="k-grid-header">
					<div class="k-grid-header-wrap">
						<table>
							<colgroup>
								<col>
								<col>
								<col>
							</colgroup>
							<thead>
								<tr>
									<th class="k-header">Header 1</th>
									<th class="k-header">Header 2</th>
								</tr>
							</thead>
						</table>
					</div>
					<!-- .k-grid-header-wrap -->
				</div>
				<!-- .k-grid-header -->
				<div class="k-grid-content">
					<table>
						<colgroup>
							<col>
							<col>
						</colgroup>
						<tbody>
							<tr>
								<td>Column 1 Row 1</td>
								<td>Column 2 Row 1</td>
							</tr>
							<tr class="k-alt">
								<td>Column 1 Row 2</td>
								<td>Column 2 Row 2</td>
							</tr>
						</tbody>
					</table>
				</div>
				<!-- .k-grid-content -->
			</div>
			<!-- .k-grid .k-widget -->
		</div>
		<!-- .t-table-view -->



Class/selector name

Description

__.t-table-view__

The RadGrid wrapper element (the one that is passed in the control's constructor).

__.k-grid.k-widget__

The wrapper of the grid widget.

__.k-grid-header .k-grid-header-wrap__

The wrapper elements of the grid header row. It has *overflow: hidden*
								applied to prevent the header from going beyond the grid boundaries.
							

__.k-grid-header-wrap > table__

The control's header data container which holds a number of column headers according to the datasource or
								control configuration. The header contains a <thead> element with the header row, and a <colgroup>
								element with <cols>, which may define column widths and visibility.
								*table-layout* is set to *fixed*,
								which causes the non-fitting cell content to be clipped, otherwise it would overflow to the next column.
							

__.k-grid-content__

Wrapper element of the grid content. It has *overflow: hidden* applied to prevent grid
								content from going out of the grid boundaries.
							

__.k-grid-content > table__

The control's data container with a number of columns and rows, according to the datasource or control
								configuration. It contains a <tbody> element with the data rows and a <colgroup> element with
								<cols>, which may define column widths and visibility. *table-layout* is set to
								*fixed*, which causes the non-fitting cell content to be clipped, otherwise it
								would overflow to the next column.
							

__.k-grid-header .k-header__

A column header cell.

__.k-grid tr, . k-grid .k-alt__

The two most common types of data rows: the normal and alternating row.

# Related Topics
