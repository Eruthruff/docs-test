---
title: Interact with RadTokenInput Programmatically
meta_title: Interact with RadTokenInput Programmatically
meta_description: description.
slug: 
tags:interact,with,radtokeninput,programmatically
publish:True
---


There are multiple ways to interact with __RadTokenInput__ programmatically. You can open, close or focus  the dropdown list. 
        You can also filter the __DataSource__ and show the filtered data in the dropdown list. The following article describes how you can
        do these things with your code.
      

# Section1

In order to be able to interact with the __RadTokenInput__, you need to first initialize it and access it in your JavaScript code.
          The code snippets below show how you can define the control in the mark-up and get it afterwards in the code-behind. In the current example the
          __Telerik.UI.find.TokenInput()__ method is used, which "casts" the control object to its proper type and you are provided with
          IntelliSense. You can find more information regarding the __find__ and __to__ method groups in
          this article: [](92c688df-0ae5-47dd-882d-1405d5ee849b).
        


 __html__
    


				<span id="tokenInput" data-win-control="Telerik.UI.RadTokenInput"></span>
	            <div id="interactionBtnsWrapper">
	                <div class="interactionControls">
	                    <input id="openBtn" type="button" value="Open" />
	                    <input id="closeBtn" type="button" value="Close" />
	                    <input id="toggleBtn" type="button" value="Toggle" />
	                    <input id="focusBtn" type="button" value="Focus" />
	                </div>
	                <div class="interactionControls">
	                    <input id="searchText" type="text" />
	                    <input id="searchBtn" type="button" value="Search" />
	                </div>
	            </div>




 __js__
    


				    tokenInput = Telerik.UI.find.TokenInput("#tokenInput");
	
				    var tokenInputDS = new Telerik.Data.DataSource({
				        transport: {
				            read: {
				                url: "http://services.odata.org/Northwind/Northwind.svc/Products",
				                dataType: "json"
				            }
				        },
				        schema: {
				            data: "value"
				        }
				    });
	
				    tokenInput.dataSource = tokenInputDS;
				    tokenInput.dataTextField = "ProductName";
				    tokenInput.dataValueField = "ProductID";
				    tokenInput.filter = "contains";
	
				    document.getElementById("openBtn").addEventListener("click", openList);
				    document.getElementById("closeBtn").addEventListener("click", closeList);
				    document.getElementById("toggleBtn").addEventListener("click", toggleList);
					document.getElementById("focusBtn").addEventListener("click", focusControl);
					document.getElementById("searchBtn").addEventListener("click", SearchDataSource);



There are also five buttons defined. Each of the interaction methods is attached as an event handler to the corresponding button. The "Search"
          button also have an input text field next to it to get string values for the method.
        

You can force the dropdown list to open by using the __open()__ method.
        


 __js__
    


		function openList() {
		    tokenInput.open();
		}



To close the dropdown list, when it is opened, use the __close()__ method. Note that this method resets the search settings.
        


 __js__
    


		function closeList() {
		    tokenInput.close();
		}



To focus the control, use its __focus()__ method. It will cause the control to be highlighted.
        


 __js__
    


		function focusControl() {
		    tokenInput.focus();
		}



Use the __search()__ method to force the control to filter its data records. The __search()__ method takes a string as
          an argument and filters the __DataSource__ based on the __filter__ property value of the control. The result is the
          dropdown list is opened and populated with the filtered data.
        


 __js__
    


		function SearchDataSource() {
		    var searchText = document.getElementById("searchText").value;
		    tokenInput.search(searchText);
		}



# Related Topics
