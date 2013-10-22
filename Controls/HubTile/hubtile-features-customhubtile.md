---
title: RadCustomHubTile
meta_title: RadCustomHubTile
meta_description: description.
slug: 
tags:radcustomhubtile
publish:True
---


RadCustomHubTile is the most customizable tile in the sense that its front and back sides are completely blank.
				It is simply two content holders for the front and back sides on top of the core hub tile API. 
				RadCustomHubTile only defines two properties - __frontContentTemplate__ and __backContentTemplate__, 
				which you can use to provide any content to the tiles, without any predefined behavior or layout.
			

# Using RadCustomHubTile

Usage of RadCustomHubTile is simple - set front content and/or back content template and you're good to go.
				


 __html__
    


				<div id="customHubTile" data-win-control="Telerik.UI.RadCustomHubTile" data-win-options="{
							frontContentTemplate:select('#frontTemplate'), 
							backContentTemplate:select('#backTemplate')
						}">
				</div>
				<div id="frontTemplate" style="display: none">
					<h2 style="margin: 40px 0 0 20px;">Weather</h2>
				</div>
				<div id="backTemplate" style="display: none">
					<div style="display: -ms-grid; -ms-grid-columns: 4fr 3fr; -ms-grid-rows: 1fr 4fr 1fr; height: 100%">
						<div style="-ms-grid-column: 1; -ms-grid-row: 2; -ms-grid-column-align: center; -ms-grid-row-align: center;">
							<img src="/images/sun.png" alt="sunny" />
						</div>
						<div style="-ms-grid-column: 2; -ms-grid-column-align: center; -ms-grid-row: 2; -ms-grid-row-align: center;">
							<h2>Helsinki</h2>
							<h4>5&deg;</h4>
							<h5>Sunny</h5>
							<h5>1&deg;C - 7&deg;C</h5>
						</div>
					</div>
				</div>

![Custom tile](../Media/Controls\HubTile\hubtile-custom.png)

To see all available configuration options, go to T:Telerik.UI.RadCustomHubTile>
						When using RadCustomHubTile in a <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">WinJS.Binding.Template</legacyBold> or any other scenario, in which the control is added to the DOM
						<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">after</legacyItalic> it is already initialized, you must specify inline width and height for the host element. This is so because
						RadCustomHubTile needs its parent element to have non-zero size when it is initialized.
					

# Related Topics
