---
title: RadMosaicHubTile
meta_title: RadMosaicHubTile
meta_description: description.
slug: 
tags:radmosaichubtile
publish:True
---


RadMosaicHubTile mimics the people hub tile on the Windows Phone home screen. It is grid of small tiles that individually flip
				themselves to display a random image. Every now and then, an image is selected and is displayed magnified by multiple tiles
				in one of the corners the mosaic tile.
			

# Using RadMosaicHubTile

Since RadMosaicHubTile is designed to exclusively display images, it has a simple API that makes displaying images very easy.
					The only property that must be set is called __picturesSource__ and its value should be a JavaScript array of strings
					representing image URLs. These could be both paths to local files or links to images hosted at a remote point. Below is a
					sample definition of a mosaic hub tile.
				


 __html__
    


				<div id="mosaicHubTile" data-win-control="Telerik.UI.RadMosaicHubTile" data-win-options="{
							picturesSource: DefaultData.imagePaths
						}">
				</div>



The data contained inside *DefaultData.imagePaths* is an array of image paths, as shown below:
				


 __js__
    


		imagePaths: [
			'/images/mosaicTile/1.jpg',
			'/images/mosaicTile/2.jpg',
			'/images/mosaicTile/3.jpg',
			'/images/mosaicTile/4.jpg',
			'/images/mosaicTile/5.jpg',
			'/images/mosaicTile/6.jpg',
			'/images/mosaicTile/7.jpg',
			'/images/mosaicTile/8.jpg'
		]
	

![Mosaic tile](../Media/Controls\HubTile\hubtile-mosaic.png)

By default, the images are shown individually in the small mosaic tiles. However, if the __flipMode__ property of
					RadMosaicHubTile is set to "row", the component will display one large image and flip it in/out row by row. The default value of the
					property is "individual".
				

If you want to provide custom styling for each mosaic tile, you can assign a string value to the __tileCssClass__
					property.
				

To see all available configuration options, go to T:Telerik.UI.RadMosaicHubTile>
						When using RadMosaicHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
						<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
						RadMosaicHubTile needs its parent element to have non-zero size when it is initialized.
					

# Related Topics
