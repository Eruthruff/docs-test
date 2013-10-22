---
title: RadHubTile
meta_title: RadHubTile
meta_description: description.
slug: 
tags:radhubtile
publish:True
---


RadHubTile is the most commonly used tile. It consists of a title, an icon, a notification count and an optional message.
				For example the store tile on the Windows start screen has a shopping bag icon. The available updates count is displayed
				on the lower right side of the tile and the title says "Store". The message can be used to display the name of the last
				app that has an update available.
			

# section1Using RadHubTile

RadHubTile exposes only three properties. These are __notification__, __imageSource__
					and __message__.
				

__notification__ is an integer that gets or sets the notification count shown at the bottom right corner of the tile.
					When it is not set (null), no notification is displayed.
				

__imageSource__ can be used to provide the location of the image to display in the tile.
				

__message__ is a string that is displayed in the top left corner of the tile. It can contain HTML which will be
					interpreted accordingly.
					Below is an example of RadHubTile with all its properties set:
				


 __html__
    


				<div id="hubTile" style="color: grey; background-color: white" data-win-control="Telerik.UI.RadHubTile" data-win-options="{
							notification: 3,
							imageSource: '/images/telerik_logo.png',
							message: '&lt;h4&gt;Welcome!&lt;/h4&gt;'
							}">
				</div>

![Hub tile](../Media/Controls\HubTile\hubtile-sample.png)

RadHubTile also inherits the following properties from the base tile component: __title__,
					__updateInterval__, __isFrozen__, and __backContentTemplate__.
				

__title__ is used to provide a title for the tile, identical to the name of the applications shown in the
					Windows 8 home screen tiles.
				

__updateInterval__
					is a number and determines the time interval of the periodic tile flips. It is important to note that these updates are only
					updates of the tile's visual states, if the tile displays some data from a remote location, for example a web service,
					the tile will not request new information, it will simply update its visuals.
				

For RadHubTile, no visual updates are going to happen by default because there is nothing dynamic on the front side.
					However, if the __backContentTemplate__ property is set, RadHubTile will start to update itself,
					by flipping to the back content and then back again.
				

Finally, the __isFrozen__ property manually starts and stops the periodic updates of the tile.
					This is handy when a hub tile is programmatically hidden from the screen. In this case, it should not update itself
					and its __isFrozen__ property should therefore be set to true.
				>
						When using RadHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
						<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
						RadHubTile needs its parent element to have non-zero size when it is initialized.
					

# Related Topics
