---
title: Show Live Data in RadCustomHubTile
meta_title: Show Live Data in RadCustomHubTile
meta_description: description.
slug: 
tags:show,live,data,in,radcustomhubtile
publish:True
---


There are scenarios in which the content and images you want to display in a __RadHubTile__ component are not stored locally on the 
        device and need to be dynamically accessed or updated from a remote point. This demo shows one way to implement such scenario - it gets all the products  
        from the Northwind Products service and displays information about one random product in a __RadCustomHubTile__.
			

# Section1Implementation

The following steps describe how to implement the scenario above:

* 

To make sure that the templates of the __RadCustomHubTile__ are loaded after data is available 
              (to avoid showing empty templates), you should first access the remote point and after a result is returned, instantiate the hub tile. 
              The first step is to call the WinJS.xhr function and pass the data access parameters. The function returns a WinJS.Promise and you can process 
              data and define your tile in the complete function:
						


 __js__
    


					WinJS.xhr({
					    url: "http://services.odata.org/V3/Northwind/Northwind.svc/Products?$format=json",
					}).then(function (result) {
						//result is the JSON response from the service, we call JSON.parse to parse it into a JavaScript object
						var response = JSON.parse(result.response);
					    //there are 20 product items inside the "value" object. We take one randomly, so we can have a different one every time.
						products = response.value;
						var rndmItem = Math.floor(Math.random() * 19);
						var currentItem = products[rndmItem];
						//create the hub tile once the data is available
						hubTile = new Telerik.UI.RadCustomHubTile(document.getElementById("hubTile"), {
							frontContentTemplate: '<h2>&nbsp;Newest Deal</h2>',
							backContentTemplate: LiveDataSample.getProduct(currentItem),
						});
					});



* 

For better customization options, use a function to create the __RadCustomHubTile__ template. In the control definition, 
              you can pass the currently retrieved item of data as a parameter to the template function (see code snippet above). Then, in the function itself,
							extract the needed data from this item and populate the template:
						


 __js__
    


	WinJS.Namespace.define("LiveDataSample", {
	    getProduct: WinJS.Utilities.markSupportedForProcessing(function (item) {
		    var template = ["<div class='grid'><div class='cell1'><p class='smallerText'>",
			item.ProductName, "</p><p>Price: ",
			Telerik.Utilities.toString(parseFloat(item.UnitPrice), "c2", "en-US"),
	        "</p></div><div class='cell2'><img height=130 src='/images/Products/",
			item.ProductID, ".jpg' alt='Picture'/></div></div>"].join("");
	
			return template;
		})
	});



* 

To keep the HTML string as short as possible, we assign only classes for styling purposes and put the actual styles in the
							page's stylesheet file:
						


 __none__
    


	/*tile appearance*/
	div.t-hubtile {
		width: 310px;
		height: 150px;
	}
	
	div.t-tile {
		background-color: #009D00;
		color: #fff;
	}
	
	.t-tile h2 {
		margin: 10px;
	}
	
	.grid {
		display: -ms-grid;
		-ms-grid-columns: 2fr 0.5fr 2fr;
		-ms-grid-rows: 1;
		margin: 10px;
	}
	
	.cell1 {
		-ms-grid-column: 1;
	    -ms-grid-column-align: center;
	}
	
	.cell2 {
		-ms-grid-column: 3;
	    -ms-grid-column-align: center;
	    -ms-grid-row-align: center;
	}
	
	.smallerText {
		font-size: 10pt;
	}



The resulting tile will look like this:![hubtile-live-data](../Media/Controls\HubTile\hubtile-live-data.png)

Additionally, the example adds a button to refresh the hubtile. On click it gets a new random number from 0 to 19 and changes the content of the hubtile to the 
          product item with the corresponding ID.
        


 __js__
    


					document.getElementById("refreshBtn").addEventListener("click", refreshHubTile);




 __js__
    


		function refreshHubTile() {
		    var rndmItem = Math.floor(Math.random() * 19);
		    var currentItem = products[rndmItem];
	
		    hubTile.backContentTemplate = LiveDataSample.getDeal(currentItem);
		}



This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *HubTile/ShowLiveDataWithCustomHubTile*.
        

# Related Topics[WinJS.xhr() function](http://msdn.microsoft.com/en-us/library/windows/apps/br229787.aspx)

 * [Templates]({{slug:templates}})
