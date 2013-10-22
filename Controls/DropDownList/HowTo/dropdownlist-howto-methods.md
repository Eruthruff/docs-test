---
title: Interact with RadDropDownList Programmatically
meta_title: Interact with RadDropDownList Programmatically
meta_description: description.
slug: 
tags:interact,with,raddropdownlist,programmatically
publish:True
---


__RadDropDownList__ methods provide ways to interact with the control programmatically. You can search the data records, open the dropdown 
        list, close the dropdown list, when it is opened, toggle the dropdown list and focus the control through your code. The following article displays basic 
        examples of how to do these actions programmatically.
      

# Section1

In order to be able to interact with the __RadDropDownList__, you need to first initialize it and access it in your JavaScript code.
          The code snippets below show how you can define the control in the mark-up and get it afterwards in the code-behind. In the current example the
          __Telerik.UI.find.DropDownList()__ method is used, which "casts" the control object to its proper type and you are provided with
          IntelliSense. You can find more information regarding the __find__ and __to__ method groups in
          this article: [](92c688df-0ae5-47dd-882d-1405d5ee849b).
        


 __html__
    


				<span id="dropDownList" data-win-control="Telerik.UI.RadDropDownList"></span>
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
    


				    dropDown = Telerik.UI.find.DropDownList("#dropDownList");
	
				    var dropDownDS = new Telerik.Data.DataSource({
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
	
				    dropDown.dataSource = dropDownDS;
				    dropDown.dataTextField = "ProductName";
				    dropDown.dataValueField = "ProductID";
				    dropDown.filter = "contains";
	
				    document.getElementById("openBtn").addEventListener("click", openList);
				    document.getElementById("closeBtn").addEventListener("click", closeList);
				    document.getElementById("toggleBtn").addEventListener("click", toggleList);
					document.getElementById("focusBtn").addEventListener("click", focusControl);
					document.getElementById("searchBtn").addEventListener("click", SearchDataSource);



There are also five buttons defined. Each of the interaction methods is attached as an event handler to the corresponding button. The "Search"
          button also have an input text field next to it to get string values for the method.
        

To open the dropdown list programmatically, use the __open()__ method.
        


 __js__
    


		function openList() {
		    dropDown.open();
		}



You can force the dropdown list to close, if it is opened, by using the __close()__ method. Note that this method resets the search
          settings.
        


 __js__
    


		function closeList() {
		    dropDown.close();
		}



Use the __toggle()__ method to toggle the dropdown list between its opened and closed state. Note that this method, like the
          __close()__ method, resets the search settings.
        


 __js__
    


		function toggleList() {
		    dropDown.toggle();
		}



To focus the control, use its __focus()__ method. It will cause the control to be highlighted.
        


 __js__
    


		function focusControl() {
		    dropDown.focus();
		}



Use the __search()__ method to force the control to filter its data records. The __search()__ method takes a string as
          an argument and filters the __DataSource__ based on the __filter__ property value of the control. The result is the
          dropdown list is opened and populated with the filtered data.
        


 __js__
    


		function SearchDataSource() {
		    var searchText = document.getElementById("searchText").value;
		    dropDown.search(searchText);
		}



# Related Topics
