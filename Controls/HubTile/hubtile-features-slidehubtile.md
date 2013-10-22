---
title: RadSlideHubTile
meta_title: RadSlideHubTile
meta_description: description.
slug: 
tags:radslidehubtile
publish:True
---


RadSlideHubTile is the tile to use when some kind of information needs to be associated with one image or you need to 
				alternate between two content templates. For that purpose RadSlideHubTile exposes two properties: __topContentTemplate__
				and __bottomContentTemplate__. Both can be either a template (HTML string or DOM element) or an image URL. 
				If an image is specified, its size will be scaled to fit the tile width/height.
			

# Using RadSlideHubTile

Here is how RadSlideHubTile is used in HTML:
				


 __html__
    


				<div id="slideHubTile" style="background-color: saddlebrown" data-win-control="Telerik.UI.RadSlideHubTile" data-win-options="{
							topContentTemplate:'&lt;h2&gt;Chocolate&lt;/h2&gt;', 
							bottomContentTemplate:'/images/food/3.jpg'
						}">
				</div>

![Slide tile](../Media/Controls\HubTile\hubtile-slide.png)

To see all available configuration options, go to T:Telerik.UI.RadSlideHubTile>
						When using RadSlideHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
						<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
						RadSlideHubTile needs its parent element to have non-zero size when it is initialized.
					

# Related Topics
