---
title: Binding RadGrid to Data from a Local File
meta_title: Binding RadGrid to Data from a Local File
meta_description: description.
slug: 
tags:binding,radgrid,to,data,from,a,local,file
publish:True
---


You can bind RadGrid to JSON or XML data from a local file. This is useful if you want the user data to be stored locally, or to cut down on the number
				of requests made to a service when its data is not constantly changing.
			

# Section1Binding to Local XML Data

To be able to bind to XML data from a local file, perform these steps.
				

* 

Assign the path of the local file to the __transport.read.url__ property.
						

* 

In the __schema__ options, specify the __type__ of the read data. In this case - "xml".
						

* 

In the __schema__ options, set the __data__ property to point to the XML element, which will 
							represent a single data record.
						

* 

Define the fields that you want RadGrid to display in the __schema.model.fields__ property. Here you can also specify
							their data type if needed to further process data.
						


 __xml__
    


	<books>
		<book title="Eloquent JavaScript">
			<author>Marijn Haverbeke</author>
			<url>
				http://www.amazon.com/Eloquent-JavaScript-Modern-Introduction-Programming/dp/1593272820
			</url>
		</book>




 __js__
    


					var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport:
							{
								read: {
									url: "/Examples/DataBinding/LocalFiles/Books.xml"
								}
							},
							schema: {
								// specify the the schema is XML
								type: "xml",
								// the XML element which represents a single data record
								data: "/books/book",
								// define the model - the object which will represent a single data record
								model: {
									// configure the fields of the object
									fields: {
										// the "title" field is mapped to the text of the "title" XML element
										title: "@title",
										// the "author" field is mapped to the text of the "author" XML element
										author: "author/text()",
										// the "url" field is mapped to the text of the "url" XML element
										url: "url/text()",
										// the "cover" field is mapped to the "id" attribute of the "book" XML element
									}
								}
							}
						},
						height: 300
					});



# Binding to Local JSON Data

To bind to JSON data residing in a local file, make sure you follow the steps below:

* 

Assign the path of the local file to the __transport.read.url__ property.
						

* 

Specify the type of the data that you are going to read through __transport.read.dataType__. In this case - "json".
						

* 

In the __schema__ options, set the __type__ property to "json".
						

* 

In the __schema.data__ property, specify the JSON object that represents a single data record.
						>
						If the JSON schema contains nested objects inside the ones that are assigned as data items, make sure that you define the columns
						explicitly. In the field property of the specific column, point to the object value using [childObject].[propertyName].
					

	
				{
				  "books": {
					"book": [
					  {
						"title": "Eloquent JavaScript",
						"info": {
							"author": "Marijn Haverbeke",
							"url": "http://www.amazon.com/Eloquent-JavaScript-Modern-Introduction-Programming/dp/1593272820"
						}
					  }
				.....
				




 __js__
    


					var grid2Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid2"), {
	
						dataSource: {
							transport:
							{
								read: {
									url: "/Examples/DataBinding/LocalFiles/BooksJSON.json",
									dataType: "json"
								}
							},
							schema: {
								// specify the the schema is JSON
								type: "json",
								// the JSON object which represents a single data record
								data: "books.book"
							},
						},
						columns: [
							{ field: "title" },
							{ field: "info.author" },
							{ field: "info.url" }
						],
						height: 300
					});



# Related Topics
