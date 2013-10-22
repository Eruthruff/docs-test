---
title: Data Binding
meta_title: Data Binding
meta_description: description.
slug: 
tags:data,binding
publish:True
---


RadSparkline can be bound to both local and remote sources of data. For reading data from a web service or a file, the control uses the built-in
				[Telerik.Data.DataSource](d27deb0c-aa3f-4549-8308-6c2e0f99d2df) component API.
			

# Section1Binding to Local Data

RadSparkline allows for a very simple set-up, when using local data. You just need to set an array of values to the __data__
					property and, if you want to change the RadSparkline type, set the __type__ property to the name of your choice.
				


 __html__
    


				Population growth:
				<span id="localBoundSparkline" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'column',
					data: [200, 450, 300, 125]
				}"></span>

![sparkline-databinding-local](../Media/Controls\Sparkline\sparkline-databinding-local.png)

You can also define the RadSparkline as a __series__ with __type__ and __data__ options
					defined and get the same result.
				


 __html__
    


				Population growth:
				<span id="localBoundSparklineWithSeries" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					series: [{
						type: 'column',
						data: [200, 450, 300, 125]
					}]
				}"></span>



# Binding to Remote Data

To bind RadSparkline to remote data, you can use the underlying Telerik.Data.DataSource component. The set-up of the data read would be the same
					as with any other control binding. For further information on the API exposed by the DataSource component, click here:
					[](5764a8ba-3fe5-49dc-9d6c-7248f48939fc).
				

The following example shows how you can define RadSparkline when binding to a remote web service:


 __html__
    


				Products price comparison:
				<span id="remoteBoundSparkline" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
							dataSource: {
							pageSize: 10,
								transport: {
									read: {
										url: 'http://services.odata.org/Northwind/Northwind.svc/Products',
										dataType: 'json'
									}
								},
								schema: {
									data: 'value'
								}
							},
							series: [{
								type: 'column',
								field: 'UnitPrice'
							}],
							categoryAxis: {
								field: 'ProductName'
							}
						}"></span>

![sparkline-databinding-remote](../Media/Controls\Sparkline\sparkline-databinding-remote.png)

# Related Topics
