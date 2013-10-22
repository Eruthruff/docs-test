---
title: Implement External Filtering
meta_title: Implement External Filtering
meta_description: description.
slug: 
tags:implement,external,filtering
publish:True
---


Thanks to the intuitive filtering API of the underlying [Telerik.Data.DataSource](69ac0343-692f-402f-a04d-0d00498f34da) component, you can
				easily implement an external filtering scenario - you can declare controls of your choice to gather filter criteria from the user. Then, you can build filter objects
				and add them to the __filter__ array of the DataSource.
			

# 

The steps below will guide you through the implementation of a RadGrid that is filtered externally by a RadDropDownList and two RadNumericTextBox controls.
				

* 

Declare the host elements for the controls:


 __html__
    


				<div class="filterItem">
					<span id="categories"></span>
					<span id="priceFrom"></span>
					<span id="priceTo"></span>
					<button id="filterBtn">Filter</button>
				</div>
				<div id="grid1"></div>



* 

Define RadGrid and make sure that you specify a __model__ for the data, so that filtering is done based on the specific
							data-type. In the code below, we "tell" the DataSource that the UnitPrice and CategoryID fields are numbers, so numeric filtering should be applied on
							them.
						


 __js__
    


					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Products",
									dataType: "json"
								}
							},
							schema: {
								data: "value",
								model: {
									id: "ProductID",
									fields: {
										ProductName: { type: "string" },
										UnitPrice: { type: "number" },
										CategoryID: { type: "number" }
									}
								}
							}
						},
						columns: [
							{
								field: "ProductName",
								title: "Product"
							},
							{
								field: "UnitPrice",
								title: "Price",
								format: "{0:C}"
							}
						],
						height: 320
					});



* 

Define a RadDropDownList. If you are not going to apply initial filtering, you can specify an empty value through the
							__optionLabel__ property. This will prompt the user about the purpose of the control and will prevent a mismatch between the
							RadDropDownList selection and the RadGrid data.
						


 __js__
    


					var categoriesDdl = new Telerik.UI.RadDropDownList(document.getElementById("categories"), {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Categories",
									dataType: "json"
								}
							},
							schema: {
								data: "value"
							}
						},
						dataTextField: "CategoryName",
						dataValueField: "CategoryID",
						optionLabel: "Choose a category to filter by..."
					});



* 

Define two RadNumericTextBox controls. To sync their behavior, handle their __change__ event and modify their min and max
							values accordingly. In the sample code below, we get the value of the "priceFrom" box and set it as a min value of the "priceTo" box. Then, the
							value of the "priceTo" box is set as a max value of the "priceFrom" box. This way the second value is always greater than or equal to the first value.
						


 __js__
    


					var fromNumericBox = new Telerik.UI.RadNumericBox(document.getElementById("priceFrom"), {
						min: 0,
						placeholder: "Enter min price",
						onchange: function (e) {
							document.getElementById("priceTo").winControl.min = e.target.value;
						}
					});
	
					var toNumericBox = new Telerik.UI.RadNumericBox(document.getElementById("priceTo"), {
						placeholder: "Enter max price",
						onchange: function (e) {
							document.getElementById("priceFrom").winControl.max = e.target.value;
						}
					});



* 

To trigger the filter action, add an event listener for the click event of the Filter button:


 __js__
    


					filterBtn.addEventListener("click", filterGrid);



* 

Create the logic that builds the filter objects for RadGrid's dataSource and apply filtering. Below you can see the step-by-step explanation of the following code
							snippet.
						

* 

Access all needed control instances.

* 

Create an empty array which will hold the RadGrid filter.

* 

Check if the RadDropDownList instance has a selected value. If so, push a filter object to the newly created array, using this value.

* 

Check if the two RadNumericBox controls have values and add a filter object for each that uses its value with a
									corresponding filter operator ("greater than or equal to" for the "priceFrom" box and "less than or equal to" for the "priceTo" box.
								

* 

Assign the resulting array to the grid.dataSource.filter property and refresh RadGrid, so the filter is applied.
								


 __js__
    


		function filterGrid() {
			var grid = document.getElementById("grid1").winControl;
			var categoriesDdl = document.getElementById("categories").winControl;
			var fromNumericBox = document.getElementById("priceFrom").winControl;
			var toNumericBox = document.getElementById("priceTo").winControl;
	
			var filter = [];
	
			if (categoriesDdl.value != "") {
				filter.push({ field: "CategoryID", operator: "eq", value: parseInt(categoriesDdl.value) });
			}
	
			if (fromNumericBox.value) {
				filter.push({ field: "UnitPrice", operator: "gte", value: fromNumericBox.value });
			}
	
			if (toNumericBox.value > 0) {
				filter.push({ field: "UnitPrice", operator: "lte", value: toNumericBox.value });
			}
	
			grid.dataSource.filter = filter;
			grid.refresh();
		}



The initial result of this definition looks like this:![grid-filtering-external 1](../Media/Controls\Grid\grid-filtering-external_1.png)

After the user specifies filter criteria and taps the Filter button, the result will be similar to the screenshot below.![grid-filtering-external 2](../Media/Controls\Grid\grid-filtering-external_2.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Grid/ExternalGridFiltering*.
        

# Related Topics

 * [Binding RadGrid to Remote Data]({{slug:binding-radgrid-to-remote-data}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Getting Started]({{slug:getting-started}})

 * [Getting Started]({{slug:getting-started}})

 * [Filtering]({{slug:filtering}})
