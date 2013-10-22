---
title: Grouping
meta_title: Grouping
meta_description: description.
slug: 
tags:grouping
publish:True
---


Grouping is a feature that requires a number of additions to the grid layout - a service column, a popup, groups of rows, etc.
				This
				article explains the RadGrid HTML output and the additional CSS classes used.
			

# Section1Grid Layout in Groupable View

When grouping is enabled and no other features are enabled in RadGrid, the output is a bit different from the default
					one. A new service column is rendered on the right of the grid over which you can drag and drop column headers to group RadGrid
					by their data field. The service column has a default text instructing the user to drop column headers to group by these columns.
					When groups are added to this area, its styling is changed and by clicking it you can open the group popup.
				


 __html__
    


		<div class="t-table-view t-service-view" data-win-control="Telerik.UI.RadGrid">
			<div class="t-service-column">
				<div class="t-group-panel">
					<div class="t-group-caption">
						<span>Drag a column header here to group</span>
					</div>
				</div>
			</div>
			<!-- .t-service-column -->
			<div class="k-grid k-widget">
				... the same structure as the default grid
			<table class="t-fixedGroupHeader"></table>
			</div>
			<!-- .k-grid .k-widget -->
		</div>
		<!-- .t-table-view .t-service-view -->



Class name

Description

__.t-service-view __

The __.t-service-view__ class is added to the grid wrapper element. It is used to change the *display* property of
								the wrapper container to *–ms-grid*.
							

__.t-service-column__

The wrapper *div* element which holds the content of the service column. The height of the
								service column is set to 100% so it stretches to the grid height.
							>
									Three additional classes are added to the service column wrapper element, which indicate the three different
									states in which the service column may be:
								

* 

__.t-highlight__: This class indicates that dragging the column header has
											started and highlights the service column so the user is prompted to drop the header over it. The list
											icon is made of symbols from Segoe UI Symbol, applied using the __:before__
											and __:after__ pseudo-elements.
										

* 

__.t-over__: This class indicates that the column header is dragged over the
											service column.
										

* 

__.t-open__: This class is set to the service column when it has groups and
											the group panel is opened.
										

__.t-group-panel__

A wrapper element for the content of the service column.>
									One additional class is added to the group panel. When the grid is grouped by a column it receives the
									<legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.t-has-groups</legacyBold>	class. Once again, the icon which indicates that there are groups is made of glyphs
									from Segoe UI Symbol, using the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">:before</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">:after</legacyBold> pseudo elements. Its
									state is changed by the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.t-open</legacyBold> class.
								

__.t-group-caption__

The wrapper of the text in the service column. When the grid is grouped by a column the *display*
								style of this div is set to *none*.
							

__.t-group-caption span__

A holder for the default text in the service column.

# HTML Output of the Group Popup

The group popup is rendered as a direct child of the groupable view. Following is its HTML output with one grouped column.
					Every new group level is added as a *li* element in the unordered list.
				


 __html__
    


		<div class="t-group-popup">
			<div>
				<ul class="k-reset">
					<li>
						<div>
							<span>
								<span class="k-icon"></span>
								<span>Header 1</span>
								<span class="k-icon k-i-arrow-n"></span>
							</span>
							<button class="k-icon"></button>
						</div>
					</li>
				</ul>
			</div>
		</div>



Same as with sorting UI, __.k-i-arrow-n__ and __.k-i-arrow-s__ are used to show in what
					direction the grid groups are sorted.
				

# Content of RadGrid with Grouping Enabled

When RadGrid is grouped, there are some new cells and rows in the output of the grid table. Group headers are rendered to indicate
					the start of each group.
					Starting with that there are grouping rows which indicate the start of each group and contain information about the group-by value and
					at the end of each group there is a group footer which is displayed when there are aggregates calculated for the groups.
				


 __html__
    


		<table>
			<colgroup>
				<col class="k-group-col">
				<col>
				<col>
			</colgroup>
			<tbody>
				<tr class="k-grouping-row">
					<td colspan="3">
						<p class="k-reset">
							<a tabindex="-1" class="k-icon k-i-collapse"></a>
							Group Name: Column 1
						</p>
					</td>
				</tr>
				<tr>
					<td class="k-group-cell">&nbsp;</td>
					<td>Column 1 Row 1</td>
					<td>Column 2 Row 1</td>
				</tr>
				<tr class="k-alt">
					<td class="k-group-cell">&nbsp;</td>
					<td>Column 1 Row 2</td>
					<td>Column 2 Row 2</td>
				</tr>
				<tr class="k-group-footer">
					<td class="k-group-cell"></td>
					<td>Total employees in group: 3</td>
					<td></td>
				</tr>
	
			</tbody>
		</table>



Class/selector name

Description

__.k-group-col__

This class is used to set the width of the new group cells (see below).

__.k-group-cell__

Cells that are used to indicates how nested the group is. For example, if the current group is a child of another group,
								these cells will be two.
							

__.k-grouping-row__

The rows containing group header cells. The content of these cells can be customized by the groupHeaderTemplate
								property of the grid columns.
							

__.k-grouping-row .k-icon__

Icon that indicates the expanded state of the group.>
									The icon state is controlled by two additional classes: <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-i-collapse</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-i-expand</legacyBold>.
								

__k-group-footer__

The rows containing group footer cells. They are populated with group aggregate values and the cells content is controlled
								by the groupFooterTemplate property of the grid columns.
							

# HTML Output of the Fixed Group Headers

When grouping and scrolling are enabled in RadGrid, there is an option to enable static group headers. If you do so, the HTML of the
					fixed group header is placed right after the grid widget element (the one with __.k-grid__ class applied. This
					is a *table* with a *tbody* in it that contains the current group header row(s)
					(the ones having __.k-grouping-row__ class assigned). The HTML is the same as in the regular group headers.
				


 __html__
    


		<table class="t-fixedGroupHeader">
			<tbody>
				<tr class="k-grouping-row">
					<td colspan="3">
						<p class="k-reset">
							<a class="k-icon k-i-collapse"></a>Group Name: Column 1
						</p>
					</td>
				</tr>
			</tbody>
		</table>



# Related Topics
