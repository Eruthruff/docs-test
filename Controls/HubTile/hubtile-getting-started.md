---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


All hub tile components derive from one base class, which defines the common functionality for all tiles:
			

* 

A time interval specifying how often the tile will flip from its front to its back side.

* 

Freezing logic so that tiles can be stopped from flipping (e.g. if they are hidden). A tile without a back side defined is always frozen.

* 

A title that is overlayed over the tile content on the bottom left.

* 

A backContentTemplate property. Setting the back content property will make the tile periodically flip to show the back content.

* 

A tileinvoked event that is raised when the user clicks/taps the tile.

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a Tile

To create a RadHubTile component in the HTML markup, add an empty __div__
							element with a __data-win-control__ attribute
							with a value of __Telerik.UI.RadHubTile__:
						

	
							<div data-win-control="Telerik.UI.RadHubTile">
							</div>
						



Alternatively, you can create a HubTile programmatically through JavaScript by first
							defining a __div__ element with an id and then passing it
							as a first argument to the HubTile constructor:
						

	
							<div id="myHubTile">
							</div>
						



	
							var hubTile = new Telerik.UI.RadHubTile(document.getElementById("myHubTile"));
						



Defining a __RadHubTile__ control without any properties set will render an empty blue rectangle with the default 
              Modern UI tile size 248x120. To fill the tile with content, you need to set value to some of the control's properties. Below you can
              find an example of how you can set property values to __RadHubTile__ to achieve a better looking and more usable 
              control.
            >
								When using RadHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
								<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
								RadHubTile needs its parent element to have non-zero size when it is initialized.
							>For example, if you will use the above-defined RadHubTile in a template, its host element should be defined like this:>&lt;div id="myHubTile" style="height: 150px; width: 248px"&gt;&lt;/div&gt;

# optionsSetting Tile Options

Just like any other Windows Runtime JavaScript control, the tile component options can be defined
							through the __data-win-options__ attribute.
						


 __html__
    


				<div id="markupHubTile" data-win-control="Telerik.UI.RadHubTile" data-win-options="{
						    title: 'Sales',
	                        imageSource: '/images/charts-icon.png'
						}"></div>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						


 __html__
    


				<div id="codeHubTile"></div>




 __js__
    


				    var hubTile = new Telerik.UI.RadHubTile(document.getElementById("codeHubTile"), {
				        title: 'Sales',
				        imageSource: '/images/charts-icon.png'
				    });



The examples above provide a title to the tile, identical to the application names on Windows 8 start screen tiles, and an icon to display in the middle 
              of the tile. To see all available configuration options, go to T:Telerik.UI.RadHubTile

Both of the declarations output the same tile. Here is an image of the result:
            ![hubtile-gettingstarted](../Media/Controls\HubTile\hubtile-gettingstarted.png)

# accessAccessing and Modifying RadHubTile

You can get hold of the hubtile object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						

	
							var tile = document.getElementById("myTile").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							tile.updateInterval = 1;
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var tile = new Telerik.UI.RadMosaicHubTile(document.getElementById("myTile"), {
								onchange: tileInvokedHandlerFnName
							});
							// OR
							var tile = new Telerik.UI.RadMosaicHubTile(document.getElementById("myTile"), {
								ontileinvoked : function(e) {//...}
							});
						

>
								If you attach the event handler as shown above but in HTML mark-up you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							tile.addEventListener("tileinvoked", tileInvokedHandlerFnName);
						



# Related Topics

 * [RadHubTile]({{slug:radhubtile}})

 * [RadCustomHubTile]({{slug:radcustomhubtile}})

 * [RadMosaicHubTile]({{slug:radmosaichubtile}})

 * [RadPictureRotatorHubTile]({{slug:radpicturerotatorhubtile}})

 * [RadSlideHubTile]({{slug:radslidehubtile}})

 * [Templates]({{slug:templates}})

 * [Events]({{slug:events}})
