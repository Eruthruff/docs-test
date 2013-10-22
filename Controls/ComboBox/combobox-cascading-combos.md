---
title: Create Cascading ComboBox
meta_title: Create Cascading ComboBox
meta_description: description.
slug: 
tags:create,cascading,combobox
publish:True
---


From Q2 2013 on, RadComboBox supports automatic cascading functionality. This means that you can have two or more RadComboBox controls in your application, each
				(except the first) showing its data based on the selection of the previous one.
			

# Section1Using Cascading RadComboBox Controls

To be able to use the automatic cascading feature, you first need to make sure that the data you use is in proper format. This means that the
					__dataValueField__ name of the first combobox must be present in the data source of the second one. For example, if the first RadComboBox
					is bound to categories with its __dataValueField__ being CategoryID, the data source of the second must have a field CategoryID of the
					same data type.
				>
						If you get your data from a remote point and the field names do not match, you can use the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">parse</legacyBold> function of the DataSource
						component, where you can process the response, which is passed as an argument, and return appropriately named fields.
					

Once you have the correct setup, you just need to set the __cascadeFrom__ property of each RadComboBox (except the first) to the
					id of the wrapper element of the RadComboBox that you want to cascade from. For example:
				


 __html__
    


			<span id="categoriesCombo"></span>
			<span id="productsCombo"></span>




 __js__
    


					var categories = new Telerik.UI.RadComboBox(categoriesCombo, {
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
						dataValueField: "CategoryID"
					});
	
	
					var products = new Telerik.UI.RadComboBox(productsCombo, {
						dataSource: {
							transport: {
								read: {
									url: "http://services.odata.org/Northwind/Northwind.svc/Products",
									dataType: "json"
	
								}
							},
							schema: {
								data: "value"
							}
						},
						dataTextField: "ProductName",
						dataValueField: "ProductID",
						cascadeFrom: "categoriesCombo"
					});



Now, only the first RadComboBox will appear as enabled when loaded. The products list will be disabled until the user selects a category. Upon selection
					in the first combobox, the second one will be filtered and enabled.
				

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *ComboBox/CascadingComboBoxes*.
        

# Related Topics

 * [Getting Started]({{slug:getting-started}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})

 * [Configuring Remote Binding]({{slug:configuring-remote-binding}})
