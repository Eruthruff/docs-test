---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of RadHubTile and their most notable event arguments.
			

# Section1Events

Event Name

Description

Arguments

__tileinvoked__

Raised when the user taps or clicks on the hub tile.
							

__e.target__ - The RadHubTile control which was invoked.
							

Below you can see a sample where the __tileinvoked__ event is handled to prepare a navigation link:
				


 __js__
    


					var hubTileCtrl = new Telerik.UI.RadHubTile(document.getElementById("hubTile"), {
						imageSource: "/images/controls/Hubtile.png",
						title: "RadHubTile",
						ontileinvoked: function (e) {
							var info = document.getElementById("info");
							info.className = info.className == "invisible" ? "visible" : "invisible";
						}
					});



# Related Topics
