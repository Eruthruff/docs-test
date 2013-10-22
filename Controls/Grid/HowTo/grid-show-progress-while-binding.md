

Sometimes loading data in RadGrid may take a few seconds, for example if it is requested from a remote point or if the data set is
				large. In such scenarios you may want to display a progress indicator, so the end-user is notified that a background operation
				is taking place. This article describes one possible way to display a progress ring over RadGrid, while it is
				loading.
			

# Section1Implementation

The following example creates a RadGrid, which loads data from a remote point. It displays a progress bar
					from the beginning of its initialization until it is completely loaded. To achieve this scenario, follow the steps below:
				

* 

Define the wrapper element for RadGrid and the progress control. At first the progress will be hidden using CSS and when needed, the
							__hidden__ class will be removed. The __win-large__ and
							__win-ring__ classes are predefined by the Windows Library for JavaScript. For more information on displaying
							progress in Windows Store apps, check the Related Resources section of this article.
						


 __html__
    


			<div class="example">
				<div id="grid1"></div>
				<div class="progressHolder">
					<progress id="progress" class="win-large win-ring hidden" />
				</div>
			</div>



* 

Define a function that shows and on demand hides the progress control:
						


 __js__
    


		function working() {
			document.getElementById("progress").classList.remove("hidden");
			return {
				finished: function () {
					document.getElementById("progress").classList.add("hidden");
				}
			}
		}
	
		app.working = working;



* 

Style the progress area, so it displays at the desired position:


 __none__
    


	.progressHolder {
		position: absolute;
		width: 1120px;
		height: calc(100% - 36px - 250px);
		left: 0;
		top: 36px;
		display: -ms-flexbox;
	}
	
	.progressHolder progress {
		margin: auto;
	}
	
	.hidden {
		display: none;
	}



* 

Call the __working__ function just before initializing RadGrid and then define the control. Inside the constructor, declare a handler
							function for the __databound__ event:
						


 __js__
    


					var work = WinJS.Application.working();
	
					var grid = new Telerik.UI.RadGrid(document.getElementById("grid1"), {
						dataSource: {
							transport: {
								read: {
									url: 'http://services.odata.org/Northwind/Northwind.svc/Order_Details',
									dataType: 'json'
								}
							},
							schema: {
								data: 'value'
							},
							filter: { field: "Discount", operator: "gt", value: 0 }
						},
						columns: [
							{ field: "OrderID", title: "Order ID" },
							{ field: "ProductID", title: "Product ID" },
							{ field: "UnitPrice", title: "Unit Price ($)" },
							{ field: "Quantity", title: "Quantity" },
							{ field: "Discount", title: "Discount", format: "{0:p}" },
							{
								title: "Total Price",
								template: "<span style='color:cyan'>#='$'+(UnitPrice * Quantity * (1-Discount)).toFixed(2) #</span>"
							}
						],
						ondatabound: dataBound,
						height: 410,
						sortable: "multiple, allowUnsort"
					});



* 

In the __dataBound__ event handler function, call the __finished__ function
							to hide the progress control. Then, you can remove the event listener for the __databound__ event. The progress does not
							need to be shown anymore for operations that take less time (like local sorting, filtering, etc.).
						


 __js__
    


					function dataBound(e) {
						work.finished();
						e.target.removeEventListener("databound", dataBound);
					}



# Related Topics[Quickstart: adding progress controls (Windows Store apps using JavaScript and HTML)](http://msdn.microsoft.com/en-us/library/windows/apps/hh465487.aspx)[How to style progress controls (Windows Store apps using JavaScript and HTML)](http://msdn.microsoft.com/en-us/library/windows/apps/jj651676.aspx)[Guidelines and checklist for progress controls (Windows Store apps)](http://msdn.microsoft.com/en-us/library/windows/apps/hh465469.aspx)