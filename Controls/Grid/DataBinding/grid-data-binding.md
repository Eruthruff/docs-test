---
title: Data Binding Overview
meta_title: Data Binding Overview
meta_description: description.
slug: 
tags:data,binding,overview
publish:True
---


Binding a __RadGrid__ is done the same way as binding the other data-bound controls in the RadControls for Windows 8 HTML 
        suite—the control exposes a __dataSource__ property of type __Telerik.Data.DataSource__ which 
        provides a solid data layer for binding to local and remote data. To learn about the numerous features of the 
        __DataSource__ control, check its documentation
				[here](d27deb0c-aa3f-4549-8308-6c2e0f99d2df).
			

This article will introduce you to the basics of binding __RadGrid__. 
        For further details about more specific scenarios, check the rest of the resources in this section.
			

# Setting a DataSource to RadGrid

You can set a __dataSource__ for __RadGrid__, 
          either during initialization, or later on, whenever you are ready with retrieving data in your app.
        

# Setting the Grid Datasource During Initialization

Since the __dataSource__ of __RadGrid__ is a 
              __DataSource__ object, you can directly set it in the grid constructor, the
							same way as you would configure a standalone __DataSource__ control. 
              Depending on the type of data that you are accessing, you can either
							assign an array of data to the __data__ property for local data binding, or configure the
							__transport__ options to retrieve data from a remote point or from a file. 
              In this example binding to a simple array of objects is demonstrated.
						


 __js__
    


	                var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
	                    dataSource: {
	                        transport: {
	                            read: {
	                                url: "http://services.odata.org/Northwind/Northwind.svc/Employees",
	                                dataType: "json"
	                            }
	                        },
	                        schema: {
	                            data: "value"
	                        }
	                    },
	                    columns: [
	                        { field: "FirstName", title: "First Name" },
	                        { field: "LastName", title: "Last Name" }
	                    ],
	                    height: 400,
	                    sortable: 'single',
	                    filterable: true
	                });



# Setting the Grid Datasource After the Control is Initialized

If you would like to [share the DataSource between more components](db6b39c3-0af1-4a3c-af52-828d61b43da3) 
              , you can define it as a separate control. Inside the complete function of the WinJS.Promise returned by the 
              __DataSource's read()__ method, you can assign it
              as a __dataSource__ for __RadGrid__ and call 
              __refresh()__ for the grid.
						


 __js__
    


	                var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
	                    columns: [
	                        { field: "FirstName", title: "First Name" },
	                        { field: "LastName", title: "Last Name" }
	                    ],
	                    height: 400
	                });
	
	                var dataSource = new Telerik.Data.DataSource({
	                    transport: {
	                        read: {
	                            url: "http://services.odata.org/Northwind/Northwind.svc/Employees",
	                            dataType: "json"
	                        }
	                    },
	                    schema: {
	                        data: "value"
	                    }
	                });
	                dataSource.read().then(function () {
	                    grid2Ctrl.dataSource = dataSource;
	                    grid2Ctrl.refresh();
	                });



# Auto-binding

__RadGrid__ is set to automatically bind to data by default. 
          This means that it will make the underlying __DataSource__ instance query data as
					soon as it is loaded. This can be prevented by setting the __autoBind__ property of 
          __RadGrid__ to *false*. 
					This is especially useful when you want the grid to not be initially bound or if you bind multiple 
          controls to the same __DataSource__
					instance.
				

To make __RadGrid__ bind when its __autoBind__ property is 
          set to *false*, you should call
					the __read()__ method of its __dataSource__.
				

	
					gridInstance.dataSource.read();
				



You can see an example of this behavior in the [](9575c779-7e45-47c8-b336-afe93f19e5fd) help article.
			

# Using Different Data Types

There are scenarios in which you might need __RadGrid__ to be aware of the 
          data type of the fields it displays data from. Such scenarios include:
				

* 

__Filtering__: when you want to have the filter functions applicable to a certain data type and not the default ("string"). The controls in the 
              drop down filter menu also change depending on the data type. For example, if you have a field of type date and filtering is turned on, 
              you will have a __RadDatePicker__ control inside the filter menu to filter by date.
						

* 

__Sorting__: by default you will have alphabetic sorting for all fields, since they are all considered string by default. To have them
							sorted numerically or as chronologically, the grid should be "aware" of that.
						

* 

__Column UI__: in the case where you want to display checkboxes for boolean fields. 
              __RadGrid__ will display the values as strings of "true" and "false" or "1" and "0" if 
              the field is not declared of type "boolean".
            

* 

__Data Editing__: if the field data type is correctly defined in the __dataSource schema model__, 
              __RadGrid__ will display the correct input control when the cell is in editing mode.
            

To make __RadGrid__ handle values based on a certain data type, you need to specify a model 
          for the data fields in the control's dataSource. This is done by listing the fields' data types in 
          __dataSource.schema.model.fields__ as shown below:
				


 __js__
    


	                var grid3Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid3"), {
	                    dataSource: {
	                        data: [
	                            { Name: 'Peter', BirthDate: new Date(1990, 10, 22), Points: 22.6, Passed: false },
	                            { Name: 'Mary', BirthDate: new Date(1984, 3, 13), Points: 221, Passed: true },
	                            { Name: 'Mark', BirthDate: new Date(1982, 4, 4), Points: 200, Passed: true }
	                        ],
	                        schema: {
	                            model: {
	                                fields: {
	                                    Name: { type: 'string' },
	                                    BirthDate: { type: 'date' },
	                                    Points: { type: 'number' },
	                                    Passed: { type: 'boolean' }
	                                }
	                            }
	                        }
	                    },
	                    columns: [
	                            { field: "Name" },
	                            { field: "BirthDate", format: "{0:MMMM yyyy}", title: "Born" },
	                            { field: "Points", title: "Score", format: "{0:N2}" },
	                            { field: "Passed" }
	                    ],
	                    sortable: 'single',
	                    filterable: true
	                });



# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Binding RadGrid to Remote Data]({{slug:binding-radgrid-to-remote-data}})

 * [Binding RadGrid to Data from a Local File]({{slug:binding-radgrid-to-data-from-a-local-file}})
