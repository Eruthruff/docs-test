---
title: Style Columns Individually
meta_title: Style Columns Individually
meta_description: description.
slug: 
tags:style,columns,individually
publish:True
---


This article shows how you can take advantage of the __attributes__, __headerAttributes__ and
				__footerAttributes__ properties of a column to apply custom styles to its cells only. This is an easy way to highlight or align a column
				without using templates for its cells.
			

All three attribute properties receive an object value. The object must list as keys the attribute names and as values—the attribute
				values. Below you can see a couple of examples showing usages of these properties.
			

# Aligning a Column in RadGrid

By default, __RadGrid__ left-aligns its column cells content. When you want to center or right-align all
					columns, you can easily do it with CSS, but when you want to change the alignment of a single or a few columns, you need a slightly
					different approach. This is where the attribute properties come to help.  You can use them to align only data cells, header or
					footer cells, or you can align them all together.
				

The example below shows how to right-align the columns that present numeric information, so that they are visually separated
					from the ones listing the sales persons' names. Furthermore, the footers are differently styled, according to the that information they are showing.
				


 __js__
    


				<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: {
						data: AttributesExample.salesData,
						aggregate: [
							{ field: 'name', aggregate: 'count' },
							{ field: 'salesLastYear', aggregate: 'sum' },
							{ field: 'salesYTD', aggregate: 'sum' },
							{ field: 'salesQuota', aggregate: 'average' },
							{ field: 'bonus', aggregate: 'sum' }
						]
					},
					columns: [
					{
						field: 'name',
						title: 'Name',
						footerTemplate: 'Number of employees: #=count#',
						width: 300
					},
					{
						field: 'salesYTD',
						title: 'Sales YTD',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(sum, &quot;c2&quot;)#',
						attributes: {
							style: 'text-align: right'
						},
						footerAttributes: {
							style: 'text-align: right; color: green'
						},
						headerAttributes: {
							style: 'text-align: right'
						},
						format: '{0:c2}'
					},
					{
						field: 'salesQuota',
						title: 'Sales Quota',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(average, &quot;c2&quot;)#',
						attributes: {
							style: 'text-align: right'
						},
						footerAttributes: {
							style: 'text-align: right; color: green'
						},
						headerAttributes: {
							style: 'text-align: right'
						},
						format: '{0:c2}'
					},
					{
						field: 'bonus',
						title: 'Bonus',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(sum, &quot;c2&quot;)#',
						attributes: {
							style: 'text-align: right; padding-right: 20px'
						},
						footerAttributes: {
							style: 'text-align: right; color: orange; font-style: italic'
						},
						headerAttributes: {
							style: 'text-align: right'
						},
						format: '{0:c2}'
					}
					],
					height: 330
				}"></div>



For reference, the data used in the example is of the following format:


 __js__
    


		{
			id: 275,
			name: "Michael Blythe",
			salesLastYear: 1750406.4785,
			salesYTD: 3763178.1787,
			salesQuota: 300000,
			bonus: 4100



The image below shows the resulting RadGrid, with all numeric columns right-aligned:![grid-columns-howto-right-align](../Media/Controls\Grid\grid-columns-howto-right-align.png)

# Highlight a Column in RadGrid

You can use a similar approach to highlight a specific column. In the below example, all three attribute properties are used to highlight the column
					that presents information about the sales to date for the current year. Note that this time styles are applied using CSS classes since this is also a
					possible way to apply your custom styles and its advantage is that styles will be easier to maintain.
				


 __js__
    


				<div id="grid2" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: {
						data: AttributesExample.salesData,
						aggregate: [
							{ field: 'name', aggregate: 'count' },
							{ field: 'salesLastYear', aggregate: 'sum' },
							{ field: 'salesYTD', aggregate: 'sum' },
							{ field: 'salesQuota', aggregate: 'average' },
							{ field: 'bonus', aggregate: 'sum' }
						]
					},
					columns: [
					{
						field: 'name',
						title: 'Name',
						footerTemplate: 'Number of employees: #=count#',
						width: 300
					},
					{
						field: 'salesYTD',
						title: 'Sales YTD',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(sum, &quot;c2&quot;)#',
						format: '{0:c2}',
						attributes: {
							class: 'highlightCell'
						},
						headerAttributes: {
							class: 'highlightHeader'
						},
						footerAttributes: {
							class: 'highlightFooter'
						}
					},
					{
						field: 'salesQuota',
						title: 'Sales Quota',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(average, &quot;c2&quot;)#',
						format: '{0:c2}'
					},
					{
						field: 'bonus',
						title: 'Bonus',
						footerTemplate: 'Total: #=Telerik.Utilities.toString(sum, &quot;c2&quot;)#',
						format: '{0:c2}'
					}
					],
					height: 330
				}"></div>



These are the styles used to customize the column look:


 __none__
    


	.k-grid-header .k-header.highlightHeader {
		background: #50749E;
		color: white;
		text-align:center;
	}
	
	.k-grid .k-alt .highlightCell,
	.k-grid .highlightCell {
		color: #4590E0;
		text-align: center;
	}
	
	.k-grid-footer .k-footer-template .highlightFooter {
		color: #50749E;
		text-align:center;
	}



You can see the result of this definition below. The Sales YTD column is centered, with differently colored header, cell and footer text.![grid-columns-howto-highlight](../Media/Controls\Grid\grid-columns-howto-highlight.png)

# Related Topics

 * [Conditional Formatting]({{slug:conditional-formatting}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})

 * [Aggregates]({{slug:aggregates}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})
