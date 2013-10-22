---
title: Using DataSource with UI Controls
meta_title: Using DataSource with UI Controls
meta_description: description.
slug: 
tags:using,datasource,with,ui,controls
publish:True
---


# ui-controlsUsing DataSource with UI controls

The __DataSource__ component can be used together with data-bound controls like __RadChart__,
					__RadGrid__, __RadAutoComplete__ etc. These UI controls have a __dataSource__
					property that is of type __Telerik.Data.DataSource__. DataSource settings for these controls can be set either declaratively
					through the HTML __data-win-options__ attribute, or dynamically through JavaScript. See the next two code samples for examples 
					of setting the __dataSource__ property for the RadChart control.
				

Here is an example mark-up of a __RadGrid__, that is bound to a __DataSource__. Note that the
					__DataSource's__ fields are used to set up other properties in the __RadGrid__ like the
					__columns__ definition.
				


 __html__
    


	        <div id="grid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
	                dataSource: External.DataSource,
	                columns: [
	                    {field: 'ID', width: 50},
	                    {field: 'Name'},
	                    {field: 'Description'},
	                    {field: 'Price'},
	                    {field: 'Rating'},
	                ],
	                height: 257
	            }"></div>



Below you can find the actual __DataSource__ declaration. It is bound to a remote web service and has a parsing function to
					transform the response to the current needs. The __DataSource__ is initialized in a namespace so it can be referenced in the mark-up.
					Alternatively you can bind the __DataSource__ to the control programmatically.
				


 __js__
    


		WinJS.Namespace.define("External", {
		    DataSource: new Telerik.Data.DataSource({
		        transport: {
		            read: {
		                url: "http://services.odata.org/V3/OData/OData.svc/Products",
		                dataType: "json"
		            },
		        },
		        schema: {
		            parse: parseResponse
		        }
		    }),
		});



And here is the parsing function for reference:
				


 __js__
    


		function parseResponse(response) {
		    var parsedResponse = [];
	
		    response.value.forEach(function (item) {
		        parsedResponse.push({
		            ID: item.ID,
		            Name: item.Name,
		            Description: item.Description,
		            Price: parseFloat(item.Price),
		            Rating: item.Rating
		        });
		    });
		    return parsedResponse;
		}



Additionally you can bind a single instance of the __DataSource__ object to multiple data-bound controls. Below is an example of a
					__RadChart__ and a __RadDropDownList__, that are bound to the same __DataSource__.
				


 __html__
    


	        <div id="chart" data-win-control="Telerik.UI.RadChart" data-win-options="{
	                dataSource: External.DataSource,
	                series: [
	                    {
	                        type: 'column',
	                        field: 'Rating',  
	                    }
	                ],
	                categoryAxis: {
	                    field: 'Name'
	                },
	                theme: 'light'
	            }"></div>
	
	        <span id="dropdown" data-win-control="Telerik.UI.RadDropDownList" data-win-options="{
	                dataSource: External.DataSource,
	                dataTextField: 'Name',
	                dataValueField: 'ID'
	            }"></span>



Finally you can see three images of the three controls, that were bound to the same __DataSource__ simultaneously:
				![datasource-ui-grid](../Media/Controls\DataSource\datasource-ui-grid.png)![datasource-ui-chart](../Media/Controls\DataSource\datasource-ui-chart.png)![datasource-ui-dropdown](../Media/Controls\DataSource\datasource-ui-dropdown.png)>
						The <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">transport</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">schema</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">type</legacyBold> properties used with binding to
						remote data can be specified during initialization only. They are read-only
						after the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">DataSource</legacyBold> instance is created.
					

# Related Topics
