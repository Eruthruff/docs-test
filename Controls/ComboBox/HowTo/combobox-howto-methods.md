---
title: Interact with RadComboBox Programmatically
meta_title: Interact with RadComboBox Programmatically
meta_description: description.
slug: 
tags:interact,with,radcombobox,programmatically
publish:True
---


There are multiple ways to interact with __RadComboBox__ programmatically. You can open, close or toggle the dropdown list. You can force a 
        suggestion or you can filter the __DataSource__ and show the filtered data in the dropdown list. The following article describes how you can 
        do these things with your code.
      

# Section1

In order to be able to interact with the __RadComboBox__, you need to first initialize it and access it in your JavaScript code.
          The code snippets below show how you can define the control in the mark-up and get it afterwards in the code-behind. In the current example the
          __Telerik.UI.find.ComboBox()__ method is used, which "casts" the control object to its proper type and you are provided with
          IntelliSense. You can find more information regarding the __find__ and __to__ method groups in
          this article: [](92c688df-0ae5-47dd-882d-1405d5ee849b).
        


 __html__
    


				<span id="comboBox" data-win-control="Telerik.UI.RadComboBox"></span>
	            <div id="interactionBtnsWrapper">
	                <div class="interactionControls">
	                    <input id="openBtn" type="button" value="Open" />
	                    <input id="closeBtn" type="button" value="Close" />
	                    <input id="toggleBtn" type="button" value="Toggle" />
	                    <input id="focusBtn" type="button" value="Focus" />
	                </div>
	                <div class="interactionControls">
	                    <input id="suggestion" type="text" />
	                    <input id="suggestBtn" type="button" value="Suggest" />
	                </div>
	                <div class="interactionControls">
	                    <input id="searchText" type="text" />
	                    <input id="searchBtn" type="button" value="Search" />
	                </div>
	            </div>




 __js__
    


				    comboBox = Telerik.UI.find.ComboBox("#comboBox");
	
				    var comboBoxDS = new Telerik.Data.DataSource({
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
	
				    comboBox.dataSource = comboBoxDS;
				    comboBox.dataTextField = "ProductName";
				    comboBox.dataValueField = "ProductID";
				    comboBox.filter = "contains";
	
				    document.getElementById("openBtn").addEventListener("click", openList);
				    document.getElementById("closeBtn").addEventListener("click", closeList);
				    document.getElementById("toggleBtn").addEventListener("click", toggleList);
					document.getElementById("focusBtn").addEventListener("click", focusControl);
					document.getElementById("suggestBtn").addEventListener("click", SuggestWord);
					document.getElementById("searchBtn").addEventListener("click", SearchDataSource);



There are also six buttons defined. Each of the interaction methods is attached as an event handler to the corresponding button. The "Suggest" and "Search"
          buttons also have an input text field next to them to get string values for the methods.
        

To open the dropdown list programmatically, use the __open()__ method.
        


 __js__
    


		function openList() {
		    comboBox.open();
		}



You can force the dropdown list to close, if it is opened, by using the __close()__ method. Note that this method resets the search 
          settings.
        


 __js__
    


		function closeList() {
		    comboBox.close();
		}



Use the __toggle()__ method to toggle the dropdown list between its opened and closed state. Note that this method, like the 
          __close()__ method, resets the search settings.
        


 __js__
    


		function toggleList() {
		    comboBox.toggle();
		}



To focus the control, use its __focus()__ method. It will cause the control to be highlighted, the insertion cursor is
          displayed and the user can start typing text.
        


 __js__
    


		function focusControl() {
		    comboBox.focus();
		}



In order to force a suggestion on the __RadComboBox__ use the __suggest()__ method. It takes a string as
          an argument and focuses the control, populates it with the string and highlights it. In the current scenario, the suggestion string is passed as the value of an
          input text box.
        


 __js__
    


		function SuggestWord() {
		    var suggestion = document.getElementById("suggestion").value;
		    comboBox.suggest(suggestion);
		}



Use the __search()__ method to force the control to filter its data records. The __search()__ method takes a string as
          an argument and filters the __DataSource__ based on the __filter__ property value of the control. The result is the
          dropdown list is opened and populated with the filtered data.
        


 __js__
    


		function SearchDataSource() {
		    var searchText = document.getElementById("searchText").value;
		    comboBox.search(searchText);
		}



# Related Topics
