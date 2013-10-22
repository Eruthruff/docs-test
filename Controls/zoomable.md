---
title: RadZoomable
meta_title: RadZoomable
meta_description: description.
slug: 
tags:radzoomable
publish:True
---


RadZoomable is a helper component used as a placeholder for content that you want to visualize using the
				[WinJS.UI.SemanticZoom](http://msdn.microsoft.com/en-us/library/windows/apps/br229690.aspx) control from the Windows Library for JavaScript.
			

As noted in the semantic zoom's documentation, the only native control that can be put inside it is the [WinJS.UI.ListView](http://msdn.microsoft.com/en-us/library/windows/apps/br211837.aspx).
				In case you want to display another control, you need to extend it to implement the [IZoomableView](http://msdn.microsoft.com/en-us/library/windows/apps/br229794.aspx) interface.
			

To save time and effort, we created the RadZoomable control that allows you to put any
				content in the SemanticZoom one, including pure HTML and/or another control.
			

# Example Using RadControls

Below you can see an example showing how RadZoomable works without issues with RadControls nested in it. It zooms in and out between a RadHubTile
					displaying a current price and a RadChart control showing how the price changed in the last few months.
				![Sample using RadControls](../Media/Controls\Zoomable\zoomable-sample-chart.png)

The code used to achieve this is shown below.


 __html__
    


				<div id="semanticZoom" style="width: 500px;" data-win-control="WinJS.UI.SemanticZoom" data-win-options="{enableButton: false}">
					<div id="zoom1" class="gridLayoutSingleCell" data-win-control="Telerik.UI.RadZoomable">
						<div id="hubTile" data-win-control="Telerik.UI.RadCustomHubTile" data-win-options="{
									frontContentTemplate: select('#template')
								}">
						</div>
					</div>
					<div id="zoom2" class="gridLayoutSingleCell" data-win-control="Telerik.UI.RadZoomable">
						<div id="chart" data-win-control="Telerik.UI.RadChart" data-win-options="{
									series: [
										{
											data: [21, 20.5, 19.79, 20, 19.99, 19.59],
											name: 'Price',
											labels: {
												visible: true,
												template: '$#=value#'
											}
										}
									],
									categoryAxis: {
										categories: ['January', 'February', 'March', 'April', 'May', 'June']
									},
									width: 400,
									height: 300
								}">
						</div>
					</div>
				</div>
				<div id="template" style="display: none;">
					<div style="font-size: 13pt; width: 75%; color: white; margin: 40px auto;">
						<p>Price this month: 19.59$</p>
					</div>
				</div>




 __none__
    


	.gridLayoutSingleCell {
		display: -ms-grid;
		-ms-grid-columns: 1fr;
		-ms-grid-rows: 1fr;
	}
	
	.gridLayoutSingleCell > div {
		-ms-grid-column: 1;
		-ms-grid-row: 1;
		-ms-grid-column-align: center;
		-ms-grid-row-align: center;
	}



# Example Using Pure HTML

Below is an example of one possible usage of RadZoomable. You can see that it wraps pure HTML and makes it available to the semantic zoom.
				

The result will be an info block about the city of Paris zooming into a view with some fast facts about it.![RadZoomable Sample](../Media/Controls\Zoomable\zoomable-sample.jpg)

The code to achieve this result follows below.


 __html__
    


				<div style="width: 700px; height: 400px" data-win-control="WinJS.UI.SemanticZoom" data-win-options="{enableButton: false}">
					<div data-win-control="Telerik.UI.RadZoomable" id="zoomable1">
						<div class="zoomableContainer">
	
							<div class="firstCol">
								<span style="text-transform: uppercase">Paris</span> is the capital and largest city of France. It is situated on the river Seine, in northern France, at the heart of the Île-de-France region. 
						An important settlement for more than two millennia, Paris had become, by the 12th century, one of Europe's foremost centres of learning and the arts 
						and the largest city in the Western world until the 18th century. Paris is today one of the world's leading business and cultural centres and its 
						influences in politics, education, entertainment, media, science, and the arts all contribute to its status as one of the world's major global cities.
										<button id="zoomInBtn">Click to view more info</button>
							</div>
							<div class="lastCol">
								<img src="/images/Paris.jpg" alt="Paris" />
							</div>
						</div>
					</div>
					<div data-win-control="Telerik.UI.RadZoomable" id="zoomable2">
						<h2>Fast facts on Paris</h2>
						<div class="zoomableContainer">
							<div class="firstCol">
								<ul>
									<li>Country: France</li>
									<li>Region: Île-de-France</li>
									<li>Land area: 105.4 km<sup>2</sup> (40.7 sq mi)</li>
									<li>Population: 2.234 million</li>
									<li>Density: 21,196/km<sup>2</sup></li>
									<li>Time zone: CET (UTC +1)</li>
									<li>Home to: Eiffel Tower, Notre Dame,<br />
										Louvre Museum, Versailles Palace, etc.</li>
								</ul>
								<button id="zoomOutBtn">Back to main view</button>
							</div>
							<div class="lastCol">
								<img src="/images/coa.png" alt="Coat of arms" />
							</div>
						</div>
					</div>
				</div>




 __js__
    


					var zoomInBtn = document.getElementById("zoomInBtn");
					var zoomOutBtn = document.getElementById("zoomOutBtn");
					zoomInBtn.addEventListener("click", function () {
						document.getElementById("zoomable1").winControl.triggerZoom();
					});
					zoomOutBtn.addEventListener("click", function () {
						document.getElementById("zoomable2").winControl.triggerZoom();
					});




 __none__
    


	.zoomableContainer {
		display: -ms-grid;
		-ms-grid-columns: 3fr 2fr;
	}
	
	.firstCol {
		-ms-grid-column: 1;
	}
	
	.lastCol {
		-ms-grid-column: 2;
	}
	
	#zoomInBtn {
		margin-top: 27px;
		display: block;
	}
	
	.zoomable .zoomableContainer button {
		width: 220px;
	}



As previously noted, you could also use the zoomable component to wrap RadControls for Windows 8 HTML or native controls from the Windows Runtime library
					for JavaScript.
				

# RadZoomable API

The RadZoomable control exposes the following public properties and methods:Properties

Name

Description

__isZoomedOut__

Gets a value determining whether the control is the zoomedOut view.

__isCurrentView__

Gets a value determining whether the control is the current view of the parent semantic zoom. You can use this property in combination
								with the triggerZoom method to toggle the zoomed view of the RadSemanticZoom control on custom user action.
							Methods

Name

Description

__triggerZoom__

Triggers zoomOut if the control provides the zoomed-in view or zoomIn if the control provides the zoomed-out view.

# Related Topics
