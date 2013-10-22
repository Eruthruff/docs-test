---
title: Filter Template
meta_title: Filter Template
meta_description: description.
slug: 
tags:filter,template
publish:True
---


Starting with Q2 2013, RadGrid offers templating for its filter item. It allows you to entirely customize the content of the filter popup that appears when
				the user taps the filter icon in the column header. Templates are applied on per column basis and to specify one you need to work with three properties:
			

* 

__column.filterable.template__: The filter item template.
					

* 

__column.filterable.apply__: A function which will return a filter expression that contains the filter item values.
					

* 

__column.filterable.refresh__: Set it to a function that applies the passed values to the filter item controls.
					

This help article explains how to create a RadGrid with a filter template for one of its columns.

# Section1Using a Filter Template in RadGrid

In the next steps we will define a RadGrid, with one if its columns (a numeric one) showing a custom filter item. It contains a RadSlider control that
					allows the user to select a numeric value to filter by.
				

* 

*Define Radgrid.* In one or more of its columns, set the __filterable__ property with the
							properties listed in the above section (__template__, __apply__ and __refresh__).
						


 __html__
    


				<div id="grid" data-win-control="Telerik.UI.RadGrid" data-win-options="{					
					dataSource: FilterTemplate.ds,
					columns: [
						{ 
							field: 'Product'
						},
						{ 
							field: 'Price', 
							format: '{0:C}',
							filterable: {
								template: select('#priceFilterTemplate'),
								apply: FilterTemplate.applyPriceFilter,
								refresh: FilterTemplate.refreshPriceFilter
							} 
						},
						{ 
							field: 'AvailableSince', 
							title: 'Available Since', 
							format: '{0:MM/dd/yyyy}' 
						}
					],
					filterable: true
				}">
				</div>



For clarity, below is the definition of the DataSource used to bind RadGrid. Along with the functions from the next steps	, it is placed inside a
							namespace called after the example—*FilterTemplate*.
						


 __js__
    


			ds: {
				data: [
					{ Product: "Southwestern Twisted Chips", Price: 7.99, AvailableSince: new Date(2012, 7, 4) },
					{ Product: "Top Shelf Combo Appetizer", Price: 9.49, AvailableSince: new Date(2012, 3, 14) },
					{ Product: "Blue Cheese and Hazelnut Shortbread", Price: 10.69, AvailableSince: new Date(2012, 5, 21) },
					{ Product: "Avocado Feta Salsa", Price: 8.59, AvailableSince: new Date(2012, 3, 14) },
					{ Product: "Red Cherry Boost", Price: 6.99, AvailableSince: new Date(2012, 2, 28) },
				],
				schema: {
					model: {
						fields: {
							Product: { type: "string" },
							Price: { type: "number" },
							AvailableSince: { type: "date" }
						}
					}
				}
			}



* 

*Define the filter template*. The template can contain a control of your choice and a customized layout. In this
							specific example you can see a RadSlider as a filter control.
						

To trigger filtering you must add a button with __type="submit"__
							attribute. If you want to allow the user to clear the filter expression for this column, add a button with __type="reset"__
							setting.
						

You can also notice that we use some of RadGrid's predefined classes to pick up the default styles of the filter item buttons.


 __html__
    


				<div id="priceFilterTemplate" data-win-control="WinJS.Binding.Template">
					<div class="customized-price">
						<span class='price-label'>Price less than: 
							<b>$11</b>
						</span>
						<span id="priceSlider" data-win-control="Telerik.UI.RadSlider" data-win-options="{						
							tickPlacement: 'none',
							min: 1,
							max: 11,
							onslide: FilterTemplate.updatePriceLabel,
							onchange: FilterTemplate.updatePriceLabel,
							tooltip: { enabled: false }
						}"></span>
	
						<button class="k-button" type="submit">Filter</button>
						<div class="t-filter-buttons">
							<button class="k-button" type="reset">Clear filter</button>
						</div>
					</div>
				</div>



To make the label in the template update together with the movement of the slider, we handle its __onslide__ and
							__onchange__ events and set the label text accordingly.
						


 __js__
    


			updatePriceLabel: WinJS.Utilities.markSupportedForProcessing(function (e) {
				$(e.target.element).parents("form").find("b").text("$" + e.value);
			})



* 

*Handle filter actions in the template*. In the functions that you assign to the __apply__
							and __refresh__ properties, you need to perform the following logic:
						

* 

__apply__: build a filter expression for RadGrid's DataSource, using the data gathered from the filter controls.
									Your function will be passed to arguments - the filter item DOM element and the current filter expression of the grid. You need to
									add the filter expression corresponding to the current column to the grid filter expression and return the grid filter expression as a
									result.
								


 __js__
    


			applyPriceFilter: WinJS.Utilities.markSupportedForProcessing(function (element, expression) {
				var filters = getFiltersForField(expression, "Price"),
					slider = element.querySelector("#priceSlider").winControl;
	
				if (filters.length) {
					if (slider.value === slider.max) {
						//reset the form and return no expression
						element.reset();
						return false;
					}
					else {
						//update existing filter
						filters[0].value = slider.value;
					}
				}
				else if (slider.value !== slider.max) {
					//add new filter
					expression.filters.push({
						field: "Price",
						operator: "lte",
						value: slider.value
					});
				}
	
				return expression;
			})



* 

__refresh__: populate the control(s) in the template with the current values from the filter expression. The function
									is again passed the same arguments. This time you need to extract the expression for the current column and use its value(s) to
									populate the filter control(s).
								


 __js__
    


			refreshPriceFilter: WinJS.Utilities.markSupportedForProcessing(function (element, expression) {
				var filters = getFiltersForField(expression, "Price"),
					label = element.querySelector(".price-label b"),
					slider = element.querySelector("#priceSlider").winControl,
					value = filters.length ? filters[0].value : 11;
	
				setTimeout(function () {
					label.innerText = "$" + value
					slider.value = value;
				}, 500)
			})



Below you can see the helper function used to extract the filter expression for the current column from the grid filter expression:


 __js__
    


		function getFiltersForField(expression, field) {
			var filters = [];
	
			((expression || {}).filters || []).forEach(function (filter) {
				if (filter.field === field) {
					filters.push(filter);
				}
			});
	
			return filters;
		}



This image shows the result of the above implementation:![grid-filtering-template](../Media/Controls\Grid\grid-filtering-template.png)

# Related Topics
