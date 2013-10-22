---
title: Best Practices
meta_title: Best Practices
meta_description: description.
slug: 
tags:best,practices
publish:True
---


The following article presents a mixture of best practices and performance tips about __RadChart__, so you can use the control
        in your applications seamlessly and realize its full potential.
      

# 
        Best Practices using RadChart
      

The following guidances and recommendations are intended to help you deliver a better experience with __RadChart__ to your users.
        

# Remote Data Binding

__RadChart__ is a data-bound control and most of the time it needs to be bound to a remote data source from a web service. 
              While you can use __WinJS.xhr()__ method to retrieve remote data and bind it to __RadChart__, it is advisable to always use the 
              Telerik __DataSource__ control for data binding. Among other features built specifically for RadControls, the __DataSource__ also 
              provides a good looking loading indicator on top of the __RadChart__ while it retrieves the remote data. This provides for a better 
              user experience and you should implement this feature manually in case you bind data to __RadChart__ in some other way.
            

You can find more information regarding how you can set up __RadChart__'s data binding using Telerik __DataSource__ in this article: 
              [RadChart Data Binding](253f6f05-3f32-4ee9-82fb-2e360d156f5f).
            

# Error Handling

There are many errors that can occur during remote data retrieval including lack of internet connection on the user side, 
              downtime on the server side and others. The good user experience practices dictate, that you should handle these error states 
              and display a user friendly and informative message in your application. If you use the Telerik __DataSource__ control for data 
              binding, use its __onerror__ event and its arguments to get different properties of the error.
            

More information on __DataSource__ events and how you can use them can be found in this article:
              [DataSource Event Handling](5d07ce3a-e282-425a-a9f3-cff72b38e089).
            

# RadChart Performance Tips

Below you can find guidelines you can refer to in case you start experiencing some performance issues using __RadChart__.

# Avoid Retrieving Large Amounts of Remote Data

__RadChart__’s performance can be hindered if the retrieval of remote data, needed to populate the chart, takes too much time. 
              Mobile devices often have limited or slow internet access, so this can be a really big problem for users. Try requesting 
              only the necessary amount of data over the internet. Another thing you can do to speed up data visualization is to save the 
              retrieved data locally and update it less frequently or only when needed.
            

# Apply a Filter to the DataSource to Display only Part of the Data

__RadChart__ is rendered as a vector graphic. Therefore, the less objects there are to be rendered, the better the performance is. 
              In case you have a lot of data entries, it is advisable to filter them through the __DataSource__ control, so you display only the first ten, 
              twenty or thirty of them. You can then implement some kind of navigation to browse the rest of the data. Displaying only part of the 
              data entries can also provide a better user experience, because often a __RadChart__ with a hundred data columns can look messy and become 
              uninformative.
            

For information on how to filter data using Telerik __DataSource__, refer to this article: 
              [DataSource Filtering](69ac0343-692f-402f-a04d-0d00498f34da).
            

# Aggregate Data to Minimize Data Points

Another way to handle large amount of data is to aggregate it by a field, e.g. by month, category, type etc. Grouping the 
              data this way will result in fewer vector objects to be drawn, which means better performance. You can then implement some 
              kind of a zoom navigation to view the data entries in each aggregated entry.
            

Here are two examples of how this can be done using __RadChart__ series:
              [](13a2a5fd-7c09-4f0a-8800-03693e4e1832) and [](e5748a7e-bbbf-4c8d-80eb-7f87c450bff9).
            

# Turn off Animated Transitions

You can do this by setting __RadChart__’s __transitions__ property value to *false*. 
              Animations can be a big performance hit, especially on low end devices or when there are multiple active charts on the page.
            


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
	                    series: [{
	                        type: 'column',
	                        data: [1, 2, 3]
	                    }],
	                    transitions: false
	                }"></div>



Alternatively, you can set the __transitions__ property value to *false* after the 
              initial load of the __RadChart__, meaning the chart will animate at start, but any new refreshes will not trigger the animation again.
            


 __html__
    


	            <div id="chart2" data-win-control="Telerik.UI.RadChart" data-win-options="{
	                    series: [{
	                        type: 'column',
	                        data: [1, 2, 3]
	                    }]
	                }"></div>




 __js__
    


				args.setPromise(WinJS.UI.processAll().then(function () {
				    var chart = Telerik.UI.find.Chart("#chart2");
				    chart.transitions = false;
				}));



# Turn off Series Gradient Fill

Gradients can affect performance greatly. By default the series __overlayGradient__ property is set to *"none"*, but if you have 
              used one of the gradient options and experience performance issues, setting the property value to *"none"* can help.
            


 __html__
    


	            <div id="chart3" data-win-control="Telerik.UI.RadChart" data-win-options="{
	                    series: [{
	                        type: 'column',
	                        data: [1, 2, 3],
	                        overlayGradient: 'none'
	                    }],
	                    transitions: false
	                }"></div>



# Related Topics
