---
title: Conditional Formatting
meta_title: Conditional Formatting
meta_description: description.
slug: 
tags:conditional,formatting
publish:True
---


Formatting cells content differently, based on the values in the data item, is easily achieved in RadGrid using cell templates. For simpler
				conditions, you can directly use a string template with a ternary operator expression. If you have more logic to process before having the final output
				for the cell, you can use a templating function. For more information on the template options in RadGrid, see
				[](a27cfadb-2990-4c07-be2a-8557b9cf722e).
			

This article will explain the two main scenarios with conditional formatting: formatting the cell content and the cell element itself.

# Formatting Cell Content

In the cell template ([column].template property) you have a binding context that provides you with the entire data item corresponding to the
					current row index. You can show any data from this context on a certain condition provided in the context. In most scenarios with conditional
					formatting a check on a certain value is performed and based on it you provide a certain output.
				

In the code snippet below you can see two implementations of conditional formatting. The Price column cells are templated and the content is
					colored red when the price is greater than 7, otherwise, green; and the Discount column displays a percent formatted value only when the
					discount is different than 0.
				


 __js__
    


					var grid1Ctrl = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							data: [
								{ Product: "Southwestern Twisted Chips", Price: 6.99, Discount: 0.2 },
								{ Product: "Top Shelf Combo Appetizer", Price: 9.49, Discount: 0 },
								{ Product: "Blue Cheese and Hazelnut Shortbread", Price: 10.69, Discount: 0.1 },
								{ Product: "Avocado Feta Salsa", Price: 6.99, Discount: 0.2 },
								{ Product: "Red Cherry Boost", Price: 6.99, Discount: 0 },
							]
						},
						columns: [
							{ field: "Product" },
							{
								field: "Price",
								template: "#=Price > 7 ? '<span style=\"color: red\">$' + Price + '</span>': '<span style=\"color: lightgreen\">$' + Price + '</span>'#"
							},
							{
								field: "Discount",
								template: "#=Discount != 0 ? Discount*100 + '% off' : ''#",
								attributes: {
									style: "#=Formatting.getBackground(data)#"
								},
							}
						]
					});



# Formatting the Cell Element

In case you want to style the entire cell (or maybe even a row) when a certain condition is fulfilled, you can do so through the
					__attributes__	property of the column. It allows you to template the value of the given attribute, so you can use the
					data context to decide what style or class name to assign to the current cell.
				

Based on the grid definition in the previous section, the sample below will provide green background to the cells displaying a discount. You can see that 
					the Discount column already has a style attribute listed, calling a function, which is expected to return the attribute value. The function is passed a 
					data object, which contains the current row values. Then it performs a conditional check on the value of interest and returns a style setting.
				


 __js__
    


	WinJS.Namespace.define("Formatting", {
		getBackground: function (data) {
			return data.Discount != 0 ? "background: green" : "background: transparent";
		}
	});



The resulting grid is shown below:![grid-conditional-formatting](../Media/Controls\Grid\grid-conditional-formatting.png)

# Related Topics
