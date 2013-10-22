---
title: Provide Default Values on Insert
meta_title: Provide Default Values on Insert
meta_description: description.
slug: 
tags:provide,default,values,on,insert
publish:True
---


When you enable CRUD operations in __RadGrid__, you may want to pre-populate some fields in the grid on create operation. This can easily
				be achieved through the model of the underlying [DataSource](142aaf90-387f-4688-9e64-11e31edbdf75).
			

# Section1How to Specify Default Insert Values Statically

To display default values when you insert a new item in RadGrid, you can set the __defaultValue__ property for the respective
					fields, listed in the __dataSource.model.fields__ object. For example, if you insert a new record in a RadGrid with data fields: Name, City,
					JobTitle and AccessType and you want to predefine the City, JobTitle and AccessType values, you will need a model definition like the one shown below.
				


 __html__
    


				<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
	                    width: 800,
	                    dataSource: {
				            data: Configuration.SampleData,
				            schema: {
				                model: {
				                    id: 'RecID',
				                    fields: {
				                        RecID: {
				                            type: 'number',
				                            editable: false,
				                            nullable: true
				                        },
				                        Name: {
				                            validation: {
				                                required: true
				                            }
				                        },
				                        City: {
				                           defaultValue: 'Boston'
				                        },
				                        JobTitle: {
				                            defaultValue: 'Sales Associate'
				                        },
										AccessType: {
											type: 'number',
											defaultValue: 2
										}
				                    }
				                }
				            }
				        },
		                columns: [
	                         {field: 'Name', width: 200},
	                         {field: 'City'},
	                         {field: 'JobTitle', title: 'Job Title', width: 350},
							 {field: 'AccessType', title: 'Access Type', width: 150, format: '{0:N0}', values: [1, 2, 3]}
		                ],
	                    editable: {
	                        enabled: true,
	                        mode: 'row'
	                    },
	                    theme: 'light',
						onedit: Configuration.edit
	                }">
				</div>



For clarity, this is the data definition:


 __js__
    


			SampleData: [{
				Name: 'Kenya Bruni',
				City: 'Anchorage',
				JobTitle: 'Chief Accounting Officer',
				RecID: 1,
				AccessType: 3
			}, {
				Name: 'Karry Evertt',
				City: 'San Antonio',
				JobTitle: 'Chief Information Technology Officer',
				RecID: 2,
				AccessType: 3
			}, {
				Name: 'Jacklyn Emayo',
				City: 'Boston',
				JobTitle: 'Chief Development Officer',
				RecID: 3,
				AccessType: 2
			}, {
				Name: 'Robin Crotts',
				City: 'New York',
				JobTitle: 'Chief Financial Officer',
				RecID: 4,
				AccessType: 3
			}]



This image shows how the above-defined RadGrid will look if you insert a new row:![grid-editing-default-values](../Media/Controls\Grid\grid-editing-default-values.png)>The default values set through the model cannot be changed dynamically because, once set, the model cannot be modified.

# How to Specify Default Insert Values Dynamically

If you want to dynamically set the default insert values for RadGrid, you can handle the __onedit__ RadGrid event and
					manually set the values to the edit control(s). If we take the above example and want to set the City value dynamically, the code would look like this:
				


 __js__
    


			edit: WinJS.Utilities.markSupportedForProcessing(function (e) {
				$("td .k-input[name=City]", e.container) //access edit control
				.val("Boston") //set the default value
				.change(); //trigger change in order to notify the model binding
			})



# Related Topics

 * [Binding RadGrid to Local Data]({{slug:binding-radgrid-to-local-data}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Events]({{slug:events}})
