---
title: Nesting Items
meta_title: Nesting Items
meta_description: description.
slug: 
tags:nesting,items
publish:True
---


Each menu item in __RadRadialMenu__ can have child items. This feature makes it easier for the end-user to navigate through multiple related
				options in a small area. This article explains how to define hierarchical menu items, what is their behavior and how to customize them.
			

# Section1Adding Child Menu Items

To add child items to a __RadRadialMenu__ item, set its __items__ property to an array of item definitions.
					__Code Listing 1__ below shows a __RadRadialMenu__ with an item that has three child items. The last child
					item defines its own children.
				


 __html__
    


	<!DOCTYPE html>
	<html>
	<head>
		<meta charset="utf-8" />
		<title>configuration</title>
	
		<!-- WinJS references -->
		<link href="//Microsoft.WinJS.1.0/css/ui-light.css" rel="stylesheet" />
		<script src="//Microsoft.WinJS.1.0/js/base.js"></script>
		<script src="//Microsoft.WinJS.1.0/js/ui.js"></script>
	
		<!-- Telerik.UI references -->
		<link href="///Telerik.UI/css/common.css" rel="stylesheet" />
		<link href="///Telerik.UI/css/light.css" rel="stylesheet" />
		<script src="///Telerik.UI/js/jquery.js"></script>
		<script src="///Telerik.UI/js/ui.js"></script>
	
		<link href="nesteditems.css" rel="stylesheet" />
		<script src="nesteditems.js"></script>
	</head>
	<body>
		<h1>RadialMenu Getting Started</h1>
		<div class="samplesContainer">
	
			<!--#region markup-options-->
			<textarea id="target1"></textarea>
			<!-- #region  nesting-->
			<div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target1',
	                    items: [
	                        {
	                            text: 'Font Color',
	                            icon: '\uE186',
								index: 4,
								items: [
									{
										id: 'Red',
										style: {
											background: 'red'
										},
										group: 'colors',
										selectable: true,
										deselectable: false,
										selected: true,
										index: 3
									},
									{
										id: 'Green',
										style: {
											background: 'green'
										},
										group: 'colors',
										selectable: true,
										deselectable: false,
										index: 4
									},
									{
										id: 'Blue',
										style: {
											background: 'blue'
										},
										group: 'colors',
										selectable: true,
										deselectable: false,
										index: 5,
										items: [
											{
												id: '1',
												style: {
													background: '#edf7ff'
												},
												group: 'colors',
												selectable: true,
												deselectable: false,
												index: 3
											},
											{
												id: '2',
												style: {
													background: '#d9fbfc'
												},
												group: 'colors',
												selectable: true,
												deselectable: false,
												index: 4
											},
											{
												id: '3',
												style: {
													background: '#52d1f7'
												},
												group: 'colors',
												selectable: true,
												deselectable: false,
												index: 5
											},
											{
												id: '4',
												style: {
													background: '#0000ff'
												},
												group: 'colors',
												selectable: true,
												deselectable: false,
												index: 6
											},
											{
												id: '5',
												style: {
													background: '#091e95'
												},
												group: 'colors',
												selectable: true,
												deselectable: false,
												index: 7
											}
										]
									}
								]
	                        }
	                    ]
	                }">
			</div>
			<!--#endregion-->
	
		</div>
	</body>
	</html>



As a result of the above definition, the item that has children defined will display an arrow in its sector of the outer ring.
				

When the arrow is tapped, the menu will navigate to the inner view containing the child items of the current item. Now you can either make a selection again
					or tap the center item which is now a back button. The third child items has child items of its own and the navigation procedure is the same.
				Figure 1: Navigating Through RadRadialMenu![radialmenu-nesting-items](../Media/Controls\RadialMenu\radialmenu-nesting-items.png)

# Related Topics

 * [Overview]({{slug:overview}})

 * [Overview]({{slug:overview}})T:Telerik.UI.RadRadialMenu
