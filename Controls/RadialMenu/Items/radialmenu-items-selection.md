---
title: Selecting Items
meta_title: Selecting Items
meta_description: description.
slug: 
tags:selecting,items
publish:True
---


__RadRadialMenu__ offers flexible selection feature for its items. They can be individually toggled or grouped together.
				This article describes the possible behaviors of items, related to selection, and how they are achieved using the __RadRadialMenu__
				API. Check the __Other Resources__ section at the bottom for a code example link.
			

# Non-selectable Items

By default, __RadRadialMenu__ items are not selectable. When the user taps an item, its __onselect__
					event will be fired and no change will occur in the item's selected state.
				

# Toggle Items (Multiple Selection)

To enable toggle selection for an item, set its __selectable__ property to *true*. This way, the
					item will be selected if tapped and deselected if the user taps it again. You can enable selection for any item in the menu and without further settings
					allow the user to select multiple items at a time and then deselect some or all of them. This is useful for settings that can be individually turned on or
					off, e.g. applying font style.
				

# Selection Groups (Exclusive Selection)

You can also group items together in a selection group. This means that only a single item can be selected at a time in the group.
					To group items together, make them all selectable and set their __group__ property to one and the same value. Now, when you select an
					item and then try to select another, the first item will be deselected.
				

If you want to make the group such that a selection is always present, set all items' __deselectable__ property to
					*false*. Now, once an item in the group is selected, it won't be possible to revert the selection. In this case, you may want
					to set the __selected__ property of one of the grouped items to *true*, so that initial selection is present.
					For example, if you want to switch between font size settings for text. There is a current font size and the user can change it but they cannot altogether
					remove the font size setting.
				

# Example

In __Code Listing 1__ below, you can see all three selection options implemented. __Figure 1__ shows
					the result from the code definition.
				Figure 1: RadRadialMenu Selection![radialmenu-menu-item](../Media/Controls\RadialMenu\radialmenu-menu-item.png)

* 

*Non-selectable items*: The *Increase* and *Decrease* items. They 
							have no selection-related properties set.

* 

*Toggle items*: The *Bold* and *Italic* items. They have selection 
							enabled and are not placed in one and the same group, so that they can be selected independently from one another.
					

* 

*Selection group*: The color items. They are in one and the same group. Additionally, deselection is not allowed, meaning 
							that there must always be a color selected once initial selection is performed. To make the colors behavior more consistent, the 
							*Cyan* item is preselected.
						


 __html__
    


				<textarea id="target4"></textarea>
				<div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target4',
						startAngle: 0,
	                    items: [
	                        {
								id: 'Increase',
								text: 'Increase',
								icon: '\uE1C7'
	                        },
							 {
								id: 'Decrease',
								text: 'Decrease',
								icon: '\uE1C6'
	                        },
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
								id: 'Key',
								style: {
									background: 'key'
								},
								group: 'colors',
								selectable: true,
								deselectable: false
							},
							{
								id: 'Yellow',
								style: {
									background: 'yellow'
								},
								group: 'colors',
								selectable: true,
								deselectable: false
							},
							{
								id: 'Magenta',
								style: {
									background: 'magenta'
								},
								group: 'colors',
								selectable: true,
								deselectable: false
							},
							{
								id: 'Cyan',
								style: {
									background: 'cyan'
								},
								group: 'colors',
								selectable: true,
								deselectable: false,
								selected: true
							}
	                    ]
	                }">
				</div>



# Related Topics

 * [Overview]({{slug:overview}})

 * [Overview]({{slug:overview}})T:Telerik.UI.RadRadialMenu
