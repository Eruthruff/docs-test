---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


This help article will introduce you to __RadRadialMenu's__ menu item objects and their properties. The items are highly customizable in terms
				of content and styling and allow you to build a menu for a number of different scenarios.
			

# centerSetting the Center Item

The center item is the small circle at the center of the radial menu. It is visible when the menu is collapsed and serves as a
					button to expand it. By default, the center item has a white background and a sprocket-wheel as an icon. When the user navigates to an inner view of the
					menu, the center item acts as a back button.
					To modify its appearance use the following properties:
				

* 

__icon__: Specifies the item's icon. The icon can be any character from the Segoe UI Symbol font. For
							reference follow this link:
							[Segoe UI Symbol icon list](http://msdn.microsoft.com/en-us/library/windows/apps/jj841126.aspx)

* 

__style__: This property holds multiple options for modifying the center item's appearance:
						

* 

__background__: Use this property to change the background color of the item. Accepts any valid CSS color as value.
								

* 

__border__: Use this property to change the center item's border color. Accepts any valid CSS color as value.
								

* 

__iconColor__: Get or sets the icon's color. Accepts any valid CSS color as value.
								

* 

__iconFont__: Use this property to change the font of the icon. In order to use the Segoe UI Symbol glyphs, you must not
									change the font type of the icon. However, to modify the icon size, you need to explicitly list both the font size and family. Therefore,
									you need to set this property in the following form: "XXpt Segoe UI Symbol" or "XXpx Segoe UI Symbol".
								

* 

__hoverColor__: Changes the center item color to the specified value when the user hovers over the item.
									Accepts any valid CSS color as value.
								

In __Code Listing 1__ below you can see a center item configuration and in __Figure 1__—the result.
				


 __html__
    


				<textarea id="target3"></textarea>
				<div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target3',
	                    center: {
	                        icon: '\uE109',
	                        style: {
	                            background: '#93ffa9',
	                            border: '#4e8759',
	                            iconColor: '#4e8759',
	                            iconFont: '14pt Segoe UI Symbol',
	                            hoverColor: '#f3ff89'
	                        }
	                    }
	                }">
				</div>

Figure 1: Customized Center Item![radialmenu-center-item](../Media/Controls\RadialMenu\radialmenu-center-item.png)

# menu-itemMenu Item Properties

To add an item in __RadRadialMenu__ you need to assign the __items__ property an array of
					menu item objects. This section lists the properties you can set to create a menu item that suits your needs.
				

# mainMain Settings

Following is a list of the base properties that can be set for a menu item.

* 

__id__: Specifies a string id for the current item. It is advisable to have unique ids for all the items in your
									radial menu. The menu item object can be easily retrieved by its id through the __getItem(id)__ method.
								

* 

__text__: Specifies the menu item text that will be shown to the user.
								

* 

__icon__: Specifies the icon shown in the item. The icon can be any character from the Segoe UI Symbol font. For
									reference follow this link:
									[Segoe UI Symbol icon list](http://msdn.microsoft.com/en-us/library/windows/apps/jj841126.aspx).
								

* 

__index__: Use this property if you wish to specify the position of the menu item in the circle. The
									position indexes are from 0 to 7 with the 0 item starting from the specified __startAngle__ of the
									__RadRadialMenu__.
								

* 

__enabled__: Gets or sets a Boolean value indicating whether the item is active and can be tapped by the user.
									The default property value is *true*.
								

* 

__autoCollapse__: A Boolean property indicating whether the menu will automatically collapse when
									the user taps the current item. Default property value is *false*.
								

* 

__items__: An array of child items. Each menu item can have a maximum of 8 child items. The child items are
									again menu items and can have child items of their own. There is no limit for the menu level depth. You can set the
									__items__ property of an item when you want to nest commands.
									For example, you have a menu item *Font Style* and when expanded, it can list items
									that allow the user to make their text bold, italic, underlined, etc.
								

# selectionSelection Settings

The following set of properties controls the selection behavior of menu items:

* 

__selectable__: A boolean property indicating whether the menu item can be selected. Default property
									value is *false*.
								

* 

__deselectable__: A boolean property indicating whether the menu item can be deselected. Default property
									value is *true*.
								

* 

__group__: Specifies the group name this item belongs to. Items that are in the same group are
									exclusively selectable. This property requires the __selectable__ property value to be
									*true*.
								

* 

__selected__: Gets or sets a boolean value indicating whether item is selected. The default property
									value is *false*.
								

For more information about item selection in __RadRadialMenu__, see the additional resources linked at the bottom
							of this help article.
						

# styleStyle Settings

The list below describes all styling settings that you can apply to a menu item and its expand sector.

* 

__style__: This property holds multiple options that can be used to modify each menu item's
									appearance:
								

* 

__background__: Use this option to change the menu item's background color.
										

* 

__border__: Use this option to change the menu item's border color.
										

* 

__color__: Use this option to change the menu item's text color.
										

* 

__disabledColor__: The color of the expand sector, the text and the icon when the menu item is disabled.
										

* 

__font__: Use this option to change the menu item's text font.
										

* 

__hoverColor__: The color of the hover indicator.
										

* 

__iconColor__: Use this option to change the menu item's icon color.
										

* 

__iconFont__: Use this option to change the menu item's icon font.
										

* 

__selectedColor__: The color of the selected indicator.
										

* 

__expandSectorStyle__: This property holds the following options to modify the appearance of the
									expand sector.
								

* 

__arrow__: The color of the arrow in the expand sector.
										

* 

__background__: The background color of the expand sector.
										

* 

__border__: The border color of the expand sector. This border is only between expand sectors.
											This property does not change the outer menu border color.
										

* 

__hoverArrow__: The color of the arrow in the expand sector when the user hovers over it.
										

* 

__hoverColor__: The background color of the expand sector when the user hovers over it.
										

# exampleExample

In __Code Listing 1__ below you can see a __RadRadialMenu__ definition that uses many of the options listed above. The first
					four items define icon and text while the next four are used for color picking, so they only display a color. The Bold and Italic items are selectable and
					deselectable, meaning that you can apply a bold style, italic style, bold and italic style or no style. The color items are put in a group and are not
					deselectable, meaning that you can apply only one color at a time and a color must always be selected.The Cyan item is by default selected.
				


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



The following image shows the menu defined in __Code Listing 1__.
				Figure 2: RadRadialMenu Items![radialmenu-menu-item](../Media/Controls\RadialMenu\radialmenu-menu-item.png)

# Related Topics

 * [Overview]({{slug:overview}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Selecting Items]({{slug:selecting-items}})
