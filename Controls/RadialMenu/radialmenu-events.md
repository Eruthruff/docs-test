---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of __RadRadialMenu__ and its most notable event arguments.
			

# Section1Events

Event Name

Description

Arguments

__action__

Fires when a menu item is tapped.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.item__ - The tapped menu item instance.
							

__e.menu__ - The RadRadialMenu control instance.
							

__collapse__

Fires when RadRadialMenu is collapsed.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.menu__ - The RadRadialMenu control instance.
							

__deselect__

Fires when a menu item is deselected.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.item__ - The deselected menu item instance.
							

__e.menu__ - The RadRadialMenu control instance.
							

__expand__

Fires when RadRadialMenu is expanded.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.menu__ - The RadRadialMenu control instance.
							

__hide__

Fires when RadRadialMenu is hidden.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.menu__ - The RadRadialMenu control instance.
							

__navigate__

Fires when the user navigates to another menu view.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.item__ - The instance of the menu item that was tapped to trigger navigation.
							

__e.menu__ - The RadRadialMenu control instance.
							

__select__

Fires when a menu item is selected.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.item__ - The selected menu item instance.
							

__e.menu__ - The RadRadialMenu control instance.
							

__show__

Fires when RadRadialMenu is shown.
							

__e.actionTarget__ - The target element of the current RadRadialMenu.
							

__e.menu__ - The RadRadialMenu control instance.
							

# Example

The following example shows how to handle the __action__ and __expand__ events of
					__RadRadialMenu__ to apply text style to an editable div element. __Code Listing1__ defines a
					__RadRadialMenu__ with three items - Bold, Italic, and Underline. It is attached to a div element with
					__contenteditable__ attribute set to *"true"*.
				


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
	
		<link href="events.css" rel="stylesheet" />
		<script src="events.js"></script>
	</head>
	<body>
		<h1>RadialMenu Events</h1>
		<div class="samplesContainer">
	
			<!-- #region  markup-->
			<div id="target1" contenteditable="true" style="color: black; width: 500px; height: 200px; border: 2px solid black">
				Radial menus are an innovative and space-saving toolbars providing the end-user with variety of options to choose 
			from. Radial menus are especially useful on touch devices as they enable the developer to place many commands and options in a flexible and dynamic UI 
			container.
			</div>
			<div id="radialMenu1" data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target1',
						visible: false,
	                    items: [
							 {
								id: 'Bold',
								text: 'Bold',
								icon: '\uE19B',
								selectable: true
	                        },
							 {
								id: 'Italic',
								text: 'Italic',
								icon: '\uE199',
								selectable: true
	                        },
							 {
								id: 'Underline',
								text: 'Underline',
								icon: '\uE19A'
	                        }
	                    ],
						onaction: Events.action,
						onexpand: Events.expand
	                }">
			</div>
			<!--#endregion-->
	
		</div>
	</body>
	</html>



__Code Listing 2__ handles the two events inside a namespace definition. The expand event handler takes care of displaying the correct
					selected state of the items, based on the currently selected text formatting. The action event handler applies the text style corresponding to the tapped
					menu item.
				


 __js__
    


		WinJS.Namespace.define("Events", {
			action: WinJS.Utilities.markSupportedForProcessing(function (e) {
				var action = e.item.id;
				switch (action) {
					case "Bold":
						document.execCommand("bold", false);
						break;
					case "Italic":
						document.execCommand("italic", false);
						break;
					case "Underline":
						document.execCommand("underline", false);
						break;
				}
			}),
			expand: WinJS.Utilities.markSupportedForProcessing(function (e) {
				var menu = e.menu;
				menu.getItem("Bold").selected = document.queryCommandState("bold");
				menu.getItem("Italic").selected = document.queryCommandState("italic");
				menu.getItem("Underline").selected = document.queryCommandState("underline");
			})
		});



In __Figure 1__ below you can see the result of the above definition. The figure shows an editable text area where upon selecting text and
					expanding the menu, the user can apply a style to the selected piece of the text.
				Figure 1: Text Editing Using RadRadialMenu![radialmenu-events](../Media/Controls\RadialMenu\radialmenu-events.png)

To learn more about the used attributes and APIs, check the __See Also__ section at the bottom.
				

# Related Topics

 * [Overview]({{slug:overview}})

 * [Selecting Items]({{slug:selecting-items}})[contenteditable Attribute](http://msdn.microsoft.com/en-us/library/ie/ms533690(v=vs.85).aspx)[execCommand Method](http://msdn.microsoft.com/en-us/library/ms536419(v=vs.85).aspx)[queryCommandState Method](http://msdn.microsoft.com/en-us/library/ie/ms536679(v=vs.85).aspx)
