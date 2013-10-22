---
title: Binding RadGrid to Remote Data
meta_title: Binding RadGrid to Remote Data
meta_description: description.
slug: 
tags:binding,radgrid,to,remote,data
publish:True
---


Using the powerful __DataSource__ component that represents the data layer of __RadGrid__, you can easily 
        bind the control to data from remote sources.
      

The most important part here is to configure the __DataSource__ for consuming remote data—its __transport__ options 
        are used for setting what is needed for retrieving the data and the __schema__ ones are used for processing the data after retrieval. Detailed
				information on configuring the __DataSource__ for remote data access is available in this article:
			

[](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)

# Binding RadGrid to Remote Data

The only differences in settings when binding to remote data, compared to binding to a local array, are found in the __dataSource__ 
          definition:
        


 __js__
    


				    var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
				        dataSource: {
				            transport: {
				                read: {
				                    url: "http://services.odata.org/Northwind/Northwind.svc/Invoices",
				                    dataType: "json"
				                }
				            },
				            schema: {
				                data: "value",
				                model: {
				                    fields: {
				                        ShipName: { type: "string" },
				                        ShipCity: { type: "string" },
				                        ShipCountry: { type: "string" },
				                        ProductName: { type: "string" },
				                        Quantity: { type: "number" },
				                        UnitPrice: { type: "number" }
				                    }
				                }
				            }
				        },
				        columns: [
							{ field: "ShipName", title: "Ship Name", width: 250 },
							{ field: "ShipCity", title: "Ship City" },
							{ field: "ShipCountry", title: "Ship Country" },
							{ field: "ProductName", title: "Product", width: 250 },
	                        { field: "Quantity", width: 100 },
	                        { field: "UnitPrice", title: "Unit Price", format: "{0:c0}", width: 100 }
				        ],
				        sortable: "single, allowUnsort",
				        height: 400
				    });



# Related Topics
