---
title: RadPictureRotatorHubTile
meta_title: RadPictureRotatorHubTile
meta_description: description.
slug: 
tags:radpicturerotatorhubtile
publish:True
---


RadPictureRotatorHubTile has very similar API to the [RadMosaicHubTile](e4ddddac-fc0f-11e1-9841-e6e46088709b),
				even simpler. You just need to define the __picturesSource__, which should be a JavaScript array of image paths
				and you are good to go. These could be both paths to local files or links to images hosted at a remote point. Below is a
				sample definition of a picture rotator hub tile.
			

# 


 __js__
    


					var pictureRotatorHubtile = new Telerik.UI.RadPictureRotatorHubTile(document.getElementById("pictureRotatorHubTile"), {
						picturesSource: DefaultData.foodImagePaths
					});



The data contained inside *DefaultData.foodImagePaths* is an array of image paths, as shown below:
				


 __js__
    


		foodImagePaths: [
			'/images/food/1.jpg',
			'/images/food/2.jpg',
			'/images/food/3.jpg',
			'/images/food/4.jpg',
			'/images/food/5.jpg',
			'/images/food/6.jpg',
			'/images/food/7.jpg',
			'/images/food/8.jpg'
		]

![Rotator tile](../Media/Controls\HubTile\hubtile-rotator.png)

The main difference between RadMosaicHubTile and RadPictureRotatorHubTile is the presentation of the randomly selected images -
					the former presents multiple images at a time, while the latter rotates images one at a time.
				>
						When using RadPictureRotatorHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
						<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
						RadPictureRotatorHubTile needs its parent element to have non-zero size when it is initialized.
					

# Related Topics
