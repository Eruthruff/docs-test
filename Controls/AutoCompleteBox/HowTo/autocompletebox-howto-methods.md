---
title: Interact with RadAutoCompleteBox Programmatically
meta_title: Interact with RadAutoCompleteBox Programmatically
meta_description: description.
slug: 
tags:interact,with,radautocompletebox,programmatically
publish:True
---


__RadAutoCompleteBox__ methods provide ways to interact with the control programmatically. You can search the data records, provide a 
        suggestion, close the dropdown list, when it is opened, and focus the control through your code. The following article displays basic examples of how to do 
        these actions programmatically.
      

# Section1

In order to be able to interact with the __RadAutoCompleteBox__, you need to first initialize it and access it in your JavaScript code. 
          The code snippets below show how you can define the control in the mark-up and get it afterwards in the code-behind. In the current example the 
          __Telerik.UI.find.AutoCompleteBox()__ method is used, which "casts" the control object to its proper type and you are provided with 
          IntelliSense. You can find more information regarding the __find__ and __to__ method groups in
          this article: [](92c688df-0ae5-47dd-882d-1405d5ee849b).
        


 __html__
    


				<span id="autoComplete" data-win-control="Telerik.UI.RadAutoCompleteBox"></span>
	            <div id="interactionBtnsWrapper">
	                <div class="interactionControls">
	                    <input id="closeBtn" type="button" value="Close" />
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
    


				    autoComplete = Telerik.UI.find.AutoCompleteBox("#autoComplete");
	
				    var autoCompleteDS = new Telerik.Data.DataSource({
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
	
				    autoComplete.dataSource = autoCompleteDS;
				    autoComplete.dataTextField = "ProductName";
				    autoComplete.filter = "contains";
	
					document.getElementById("closeBtn").addEventListener("click", closeList);
					document.getElementById("focusBtn").addEventListener("click", focusControl);
					document.getElementById("suggestBtn").addEventListener("click", SuggestWord);
					document.getElementById("searchBtn").addEventListener("click", SearchDataSource);



There are also four buttons defined. Each of the interaction methods is attached as an event handler to the corresponding button. The "Suggest" and "Search" 
          buttons also have an input text field next to them to get string values for the methods.
        

To focus the control, use its __focus()__ method. It will cause the control to be highlighted, the insertion cursor is 
          displayed and the user can start typing text.
        


 __js__
    


		function focusControl() {
		    autoComplete.focus();
		}



You can force the dropdown list to close, if it is opened, by using the __close()__ method. Note that this method resets the search 
          settings.
        


 __js__
    


		function closeList() {
		    autoComplete.close();
		}



In order to force a suggestion on the __RadAutoCompleteBox__ use the __suggest()__ method. It takes a string as 
          an argument and focuses the control, populates it with the string and highlights it. In the current scenario, the suggestion string is passed as the value of an 
          input text box.
        


 __js__
    


		function SuggestWord() {
		    var suggestion = document.getElementById("suggestion").value;
		    autoComplete.suggest(suggestion);
		}



Use the __search()__ method to force the control to filter its data records. The __search()__ method takes a string as 
          an argument and filters the __DataSource__ based on the __filter__ property value of the control. The result is the 
          dropdown list is opened and populated with the filtered data.
        


 __js__
    


		function SearchDataSource() {
		    var searchText = document.getElementById("searchText").value;
		    autoComplete.search(searchText);
		}



# Related Topics

 * [Getting Started]({{slug:getting-started}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})
