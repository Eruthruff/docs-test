---
title: Visual Structure
meta_title: Visual Structure
meta_description: description.
slug: 
tags:visual,structure
publish:True
---


This article describes the visual elements of the RadGrid control.

# Common Structure

Below you can find a description of the common elements, visible in every RadGrid control.

# Visual Structure![grid-visual-structure 1](../Media/Controls\Grid\grid-visual-structure_1.png)

# Description of Elements

Name     

Description

[Column](fbb96399-dfbe-4826-ac0f-c5d6e698f244)

Columns are the vertical entity of data from a single data field. In the simplest scenario they consist of a header cell and column
										cells (or just cells).
									

[Row](749c4be4-e3f7-4912-a248-c984dcb5e2c6)

Could also be referred to as *"items"*. Rows are a horizontal entity of data representing a single
										data item from the grid data source. A row contains one cell of data from each column as you move horizontally across all of the columns.
									

Cell
									

Cells are the intersection between a column and a row. A cell by default displays a single value from a single data field.
									

Column Header
									

The column header is a cell, shown on top of each column of data. It is not bound to a data field and is usually used to
										display the title of the field the current column is bound to. Column headers together form the
										__grid header__.
									

# Grid with Aggregates Defined

# Visual Structure![grid-visual-structure 2](../Media/Controls\Grid\grid-visual-structure_2.png)

# Description of Elements

Name     

Description

Column Footer
									

The column footer is a cell at the bottom of columns, used to display summary data about columns (for example the count of
										data records, or the sum of their values in the current column, etc.). The column footers together form the grid footer and
										are only shown when there are aggregates defined in the grid data source.
									

# Grid with Filtering Enabled

# Visual Structure![grid-visual-structure 3](../Media/Controls\Grid\grid-visual-structure_3.png)

# Description of Elements

Name     

Description

Filter Icon
									

The filter icon appears in each filterable column's header when filtering is enabled. Clicking/tapping the filter icon results in the
										column filter menu being shown.
									

[Filter Menu](2c36b378-519b-4ee6-96d6-6cf99e4f6fe8)

The filter menu is used to visually construct filter expressions for each grid column. You can follow the link on the
										left to learn about its detailed structure.
									

# Grid with Grouping Enabled

# Visual Structure![grid-visual-structure 4](../Media/Controls\Grid\grid-visual-structure_4.png)

# Description of Elements

Name     

Description

Group Header
									

The group header displays information about the group it belongs to. By default, this information is the name of the group-by
										field and the current group value.
									

Group Footer Cell
									

The group footer cell is shown in columns at the bottom of each group, used to display summary data about the values of a
										field in the current group (for example, the count of data records belonging to the group, or the sum of their values in the
										current column, etc.). The column group footer cells together form the grid group footer and
										are only shown when there are aggregates defined in the grid data source and a group footer template defined in the column.
									

Grouping Panel
									

The grouping panel is used to display and allow interaction with the group-by fields. They can be sorted, reordered and
										removed, using their visual representations in the panel.
									

# Grid with Hierarchical Structure

# Visual Structure![grid-visual-structure 5](../Media/Controls\Grid\grid-visual-structure_5.png)

# Description of Elements

Name     

Description

Parent Table
									

In a hierarchy scenario, the parent table (or *master table*) is the actual grid table, which
										contains all top-level grid rows.
									

Detail Table
									

Could also be referred to as *"child table"*. It contains all the rows that are hierarchically
										related to a row in the parent table (details). It has its own filtering, sorting, selection, etc., independently from the
										parent table.
									

Parent Row
									

This is the row from the parent table, that is expanded to display the detail one.
									

Expand Button
									

A button shown in each row in the parent table, used to expand this row in order to display its detail tables, and then to
										collapse it on a second click (toggles the expanded and collapsed state of parent rows).
									

# Related Topics
