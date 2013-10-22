---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


The following help article will introduce you to the properties of __RadRadialMenu__ and its usage. The
				article provides property descriptions, available property values and configuration examples.
			

# showShowing RadRadialMenu

Configure the following properties to change how the control is shown:
				

* 

__visible__: A Boolean property indicating whether the menu button is visible at start.
							Note that because of the nature of the context menu, only one menu can be visible at any given moment. This means that
							only the last declared visible menu will be displayed when the page loads. The default property value is
							*true*.
						

* 

__target__: Specifies the target HTML element or CSS selector for which the radial menu will be
							shown. If the property value is *null* the menu button is positioned at the __RadRadialMenu__'s
							wrapper element location. The default property value is *null*.
						

* 

__trigger__: Specifies the action upon the target element that will show the attached menu. In order to work properly, this
							property requires a valid __target__ setting. Possible property values for the
							__trigger__ property are *"none"*, *"tap"*,
							*"hover"*, and *"focus"*.
							The default property value is *"tap"*.
						

* 

__position__: Gets or sets the position of the menu button relative to its HTML target element. This
							property requires a valid __target__ setting. Accepted property values are
							*"top"*, *"bottom"*, *"left"*,
							*"right"*, *"center"*, *"top left"*,
							*"top right"*, *"bottom left"*, and *"bottom right"*.
							The default property value is *"right"*.
						

* 

__offsetLeft__: Gets or sets the left offset of the radial menu button in pixels relative to the target
							HTML element and the specified position. This property requires a valid __target__ setting.
						

* 

__offsetTop__: Gets or sets the top offset of the radial menu button in pixels relative to the target
							HTML element and the specified position. This property requires a valid __target__ setting.
						><legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadRadialMenu</legacyBold> does not currently support viewport edge detection. This means
								the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">position</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">offsetLeft</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">offsetTop</legacyBold> property
								values can lead to the menu displaying outside of the visible area in you application. You should have this in mind when the target element is placed
								close to the edge of the visible area. Viewport edge detection will be added as a feature to the menu in future versions.
							

* 

__expanded__: A Boolean property indicating whether the radial menu will be automatically
							expanded when shown. The default property value is *false*.
						

* 

__autoCollapse__: A Boolean property indicating whether the radial menu will collapse
							automatically when the user taps outside of it. The default property value is *true*.
						

* 

__transitions__: A Boolean property indicating whether the menu animations are enabled
							or disabled. The default property value is *true*.
						

__Code Listing 1__ below shows an example configuration of __RadRadialMenu__. Check
					__Figure 1__ to see the result and a display of the control behavior.
				


 __html__
    


				<textarea id="target1" style="width: 150px; height: 80px;">Radial menus are an innovative and space-saving toolbars providing the end-user with variety of options to choose from. Radial menus are especially useful on touch devices as they enable the developer to place many commands and options in a flexible and dynamic UI container.</textarea>
				<div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    visible: false,
	                    target: '#target1',
	                    trigger: 'focus',
	                    position: 'top',
	                    offsetLeft: 250,
	                    offsetTop: 100,
						items: [
							{text: 'Copy'},
							{text: 'Cut'},
							{text: 'Select All'}
						]
	                }">
				</div>

Figure 1: Showing RadRadialMenu![radialmenu-configuration-show](../Media/Controls\RadialMenu\radialmenu-configuration-show.png)

# addAdding Menu Items

To add items to the radial menu use these two properties:

* 

__center__: Use this property to change the menu's center item. This is the item in the center of the radial
							menu and is shown when the menu is collapsed. This property accepts a single center item object. By default the center item is white
							and has a sprocket-wheel as an icon.
						

* 

__items__: Use this property to add an array of items to the radial menu. By default there are no items in the menu
							and the default property value is an empty array.
						

You can see a simple items definition in __Code Listing 1__ above.
					For information on menu item properties and configuration, refer to this article:
					[Menu Items Properties and Configuration](4032cd26-3ac6-4ec5-a3bf-62f5ebda6500).
				

# appearanceAppearance Settings

The __RadRadialMenu__ appearance can be configured by the following properties:
				

* 

__startAngle__: Specifies the start angle of the first radial sector in the menu in degrees. The items are rendered clockwise,
							where a start angle of 0 is equal to 180 degrees in the polar coordinate system. This property takes both positive and negative floating point
							numbers. The default property value is *-22.5*.
						

* 

__radius__: Gets or sets the radius of the radial menu in pixels. This property takes positive floating point
							numbers. The default property value is *132.5*.
						

* 

__background__: Use this property to change the outer circle's background color.
						

* 

__border__: Use this property to change the outer circle's border color.
						

* 

__innerBackground__: Use this property to change the inner circle's background color.
						

__Code Listing 2__ below uses the properties introduced above to customize __RadRadialMenu__. You can see the
					result in __Figure 2__.
				


 __html__
    


				<div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target2',
	                    startAngle: 90,
	                    radius: 120,
	                    background: '#93fbff',
	                    border: '#60a3a5',
	                    innerBackground: '#e8feff',
	                    items: [
	                        {
	                            text: 'Font size',
	                            icon: '\uE1C8'
	                        }, {
	                            text: 'Font',
	                            icon: '\uE185'
	                        }
	                    ]
	                }">
				</div>

Figure 2: RadRadialMenu with Customized Appearance![radialmenu-configuration-appearance](../Media/Controls\RadialMenu\radialmenu-configuration-appearance.png)

# Related Topics

 * [Overview]({{slug:overview}})
