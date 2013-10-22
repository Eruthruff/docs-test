---
title: Custom Editors
meta_title: Custom Editors
meta_description: description.
slug: 
tags:custom,editors
publish:True
---


RadGrid displays different editor controls for the different data types and thanks to this, meets the requirements of most editing scenarios. However, in more
				specific cases, you may want to display a custom edit control in one or more of the grid cells. In this article you will learn how to display controls of your
				choice in RadGrid's edited cells.
			

# Section1Using Custom Editors in RadGrid

To display a custom editor in RadGrid, you need to assign the __editor__ property a function that adds the editor. In the function you
					need to:
				

* 

Create a wrapper element for the control that you are going to define.

* 

Two arguments will be passed to your function—the first one is the __container__ element of the edited cell; the second is a
							set of two options—__field__ (the field name of the edited item) and __model__ (the model of the currently
							edited data item). You need to add the control wrapper as a child of the cell container element.

* 

Instantiate the control. You can access the current value of the edited cell through __options.model.[propertyName]__.
						

* 

To allow RadGrid to access the edited value you need to ensure that there is an __input__ element in the template, with a
							__name__ attribute set to the name of the field that is currently edited. The input must always contain the latest edited value.
						

These steps are implemented in the example shown below.

For clarity, this is how an item in the datasource is structured:


 __js__
    


		{ id: 1, BikeModelName: "BlueBird", BikeType: "Track", BikeModelYear: 2012, Rating: 4 }



In the RadGrid declaration below, you can see how the __editor__ property of the Rating column is set to a function.
				


 __js__
    


					var grid = new Telerik.UI.RadGrid(grid1, {
						dataSource: {
							data: dataArrayBikes,
							schema: {
								model: {
									id: "id",
									fields: {
										id: { editable: false, type: "number" },
										BikeModelName: { type: "string", validation: { required: true } },
										BikeType: { type: "string" },
										BikeModelYear: { type: "number", defaultValue: 2013, validation: { max: 2013 } },
										Rating: { type: "number" }
									}
								}
							}
						},
						columns: [
						{ field: "BikeModelName", title: "model" },
						{ field: "BikeType", title: "type", values: ["Road", "Mountain", "Racing", "Track", "Bmx", "Portable", "Junior"], width: 150 },
						{ field: "BikeModelYear", title: "year", format: "{0:yyyy}", width: 150 },
						{ field: "Rating", title: "rating", editor: getRatingEditor }
						],
						editable: {
							enabled: true,
							mode: "row"
						},
						onsave: function (e) {
							//set id to inserted items
							if (e.model.id == 0) {
								e.model.id = e.target.dataSource.data.length;
							}
						},
						height: 330
					});



The function implements the steps from the list with instructions you saw above to add a WinJS.UI.Rating control to the edit cell:


 __js__
    


		function getRatingEditor(container, options) {
			var ratingWrapper = document.createElement("div");
			//create a hidden input to be able to store the cell value
			var valueInput = document.createElement("input");
			valueInput.type = "hidden";
			valueInput.name = options.field;
	
			$(valueInput).appendTo(container);
			$(ratingWrapper).appendTo(container);
			var rating = new WinJS.UI.Rating(ratingWrapper, {
				//access the Rating value from the passed data item
				userRating: options.model.Rating,
				tooltipStrings: ["Bad", "Wouldn't recommend", "Good", "Great", "Superb!"],
				//handle the onchange event to update the hidden input with the latest rating value
				onchange: function (e) {
					var input = $("input[type=hidden]", $(e.target).parent());
					input.val(e.target.winControl.userRating).change();
				}
			});
		}



Here is the result of this implementation:![grid-editing-custom-editors 1](../Media/Controls\Grid\grid-editing-custom-editors_1.png)

# Related Topics
