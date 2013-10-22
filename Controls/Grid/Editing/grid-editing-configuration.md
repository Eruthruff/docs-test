---
title: Editing Configuration
meta_title: Editing Configuration
meta_description: description.
slug: 
tags:editing,configuration
publish:True
---


To configure the editing behavior in __RadGrid__, use the options that belong to the __editable__ property of __RadGrid__. They control which
				edit operations are enabled,
			

# Editing settings

The __editable__ property receives an object with the following options as settings for __RadGrid__ editing:
				

Property

Description

__enabled__

Used to enable editing in __RadGrid__. By default is set to *false*.
							

__mode__

Use this property to switch between the edit modes of __RadGrid__. Its accepted values are *"cell"*,
								*"cellBatch"* and *"row"*. More information on edit modes is available here:
								[](0e7ed261-b633-4538-9d68-ef58ddd4cdea). The default value is "cell".
							

__create__

To disable insert, while update and delete are enabled, set the __create__ property to
								*false*. This way, pressing the insert button will not result in a new row being
								inserted.
							

__createAt__

This property indicates whether the newly created record should be inserted at the top or at the bottom of the currently
								available grid data. Accepted values are "top" and "bottom". The default value is "top", meaning that when the insert button
								in the service column is pressed, a new item will be added at the top of the grid items.
							

__update__

To disable update, while insert and delete are enabled, set the __update__ property to
								*false*. This way, double clicking an item will not put it in edit mode.
							

__destroy__

You can choose between two behaviors when deleting items - they can either be immediately deleted
								(*destroy: true*) or only marked for deletion(*destroy: false*). The default value of this
								property is *true*.
							

Here is a full code sample of __RadGrid__ with data editing enabled. The code includes:
        

* 

Definition of a __dataSource__ with a defined __model__. Without the __model__ the 
              data editing feature will not behave correctly.
            

* 

Definition of the __columns__ for better visual layout.
            

* 

Definition of the __editable__ property with __mode__ set to *row*, 
              __update__ set to *true*, __create__ and __destroy__ set to
			  *false*. This means that the grid will be editable but insertion and deletion of records will be disabled.
            


 __html__
    


				<div id="grid" data-win-control="Telerik.UI.RadGrid" data-win-options="{
	                    width: 800,
	                    dataSource: {
				            data: Configuration.Data,
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
				                            validation: {
				                                required: true
				                            }
				                        },
				                        JobTitle: {
				                            validation: {
				                                required: true
				                            }
				                        }
				                    }
				                }
				            }
				        },
		                columns: [
	                         {field: 'RecID', title: 'ID', width: 50},
	                         {field: 'Name', width: 200},
	                         {field: 'City'},
	                         {field: 'JobTitle', title: 'Job Title', width: 350}
		                ],
	                    editable: {
	                        enabled: true,
	                        mode: 'cellBatch',
	                        create: false,
	                        update: true,
	                        destroy: false
	                    },
	                    theme: 'light'
	                }">
				</div>



And here is the data array for reference:
        


 __js__
    


			Data: [{
				Name: 'Kenya Bruni',
				City: 'Anchorage',
				JobTitle: 'Chief Accounting Officer',
				RecID: 1
			}, {
				Name: 'Karry Evertt',
				City: 'San Antonio',
				JobTitle: 'Chief Information Technology Officer',
				RecID: 2
			}, {
				Name: 'Jacklyn Emayo',
				City: 'Boston',
				JobTitle: 'Chief Development Officer',
				RecID: 3
			}, {
				Name: 'Robin Crotts',
				City: 'New York',
				JobTitle: 'Chief Financial Officer',
				RecID: 4
			}]



# Related Topics
