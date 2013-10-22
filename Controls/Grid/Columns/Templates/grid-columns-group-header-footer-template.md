---
title: Group Header and Footer Cell Template
meta_title: Group Header and Footer Cell Template
meta_description: description.
slug: 
tags:group,header,and,footer,cell,template
publish:True
---


This help article will show you how to use the __groupHeaderTemplate__ and __groupFooterTemplate__ properties of
				RadGrid columns to display customized content in the group header and footer cells.
			

# headerGroup Header Template

To provide a more custom look of the group headers, you can use the __groupHeaderTemplate__ property. You could assign it either a string
					or a function returning a string (which can contain HTML). In both cases, you have access to the current group info.
				

If you use a string template, you can use binding expressions to get the *field* and *value*
					fields, e.g. "#=field#: #=value#".
				

In case you assign a function to the property, make sure you allow it to accept one argument, which will provide these values, so you can use it in
					the returned template. A group header template definition is shown in the example at the end of this article.
				

# footerGroup Footer Template

To be able to show aggregates for each group, you need to set the __groupFooterTemplate__ property to evaluate one of the pre-defined
					aggregates' values. For more information on grouping and specifying aggregates for groups, see the
					[Group Aggregates](7df5d01f-3ece-4715-a910-90fa2cbc6965) help article. As far as the template itself is concerned, it can again be a string or a
					function returning a string, where the binding context provides the aggregates specified for the current group. Make sure that your template does not try to
					output unconditionally aggregate values that are not available for all grouping scenarios of the grid.
				

In the example below you can see that only a static group is defined and the aggregate needed for it is specified in the group definition in the dataSource.
					In this scenario the value used in the group footer template is always available since the grid is always grouped by this field. The article about grouping,
					linked above, elaborates on the other options of providing aggregates and in what scenarios they would be available.
				


 __js__
    


					var gridGroupHeaderTemplate = new Telerik.UI.RadGrid(document.getElementById("grid3"), {
						dataSource: {
							data: [
								{ Name: "Peter", Group: 1, Points: 22.6 },
								{ Name: "Mary", Group: 2, Points: 24 },
								{ Name: "Sarah", Group: 2, Points: 28.8 },
								{ Name: "Nancy", Group: 1, Points: 25.2 },
								{ Name: "Andrew", Group: 2, Points: 18.4 }
							],
							group: {
								field: "Group", aggregates: [
										{ field: "Name", aggregate: "count" }
								]
							}
						},
						filterable: true,
						sortable: 'multiple, allowUnsort',
						columns: [
							{ field: "Name", groupFooterTemplate: "Total number of people in group: #=count#" },
							{ field: "Group", groupHeaderTemplate: getGroupHeaderTemplate },
							{ field: "Points" }
						]
					});




 __js__
    


		function getGroupHeaderTemplate(args) {
			var groupNameHtml = "Grouped by: <span style='color: #FF72FA'>" + args.field + "&nbsp;</span>";
			var groupValueHtml = "Current value: <span style='color: #33ccff'>" + args.value + "</span>";
			return groupNameHtml + groupValueHtml;
		}



These templates will result in the following look:![grid-columns-group-header-footer-templates](../Media/Controls\Grid\grid-columns-group-header-footer-templates.png)

# Related Topics
