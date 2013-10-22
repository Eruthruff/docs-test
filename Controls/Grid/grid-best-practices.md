---
title: Best Practices
meta_title: Best Practices
meta_description: description.
slug: 
tags:best,practices
publish:True
---


The following article provides guidelines and suggestions regarding best practices and performance issues you might experience using __RadGrid__.  
      

# Section1Best Practices using RadGrid

The following guidances and recommendations are intended to help you deliver a better experience with __RadGrid__ to your users.

# Remote Data Binding

In the most common scenario you will need to bind __RadGrid__ to a remote data source. While you can use the 
              __WinJS.xhr()__ method to retrieve data and use a binding list to bind it to the control, it is advisable to use the
              Telerik __DataSource__ for remote data binding. The __DataSource__ control was specifically built 
              for RadControls, so you can request, modify and bind data seamlessly. It provides many features and properties, that 
              __RadGrid__ interprets and visualizes. The __DataSource__ also automatically provides a loading 
              indicator to the __RadGrid__ while the data is retrieved and ready to be visualized. This provides for a better user 
              experience and you should implement this feature manually in case you bind data to __RadGrid__ in some other way.
            

# Error Handling

There are many errors that can occur during remote data retrieval including lack of internet connection on the user side, downtime on 
              the server side and others. The good user experience practices dictate, that you should handle these error states and display a user 
              friendly and informative message in your application. If you use the Telerik __DataSource__ control for data 
              binding, use its __onerror__ event and its arguments to get different properties of the error.
            

# Data Model

__RadGrid__ benefits greatly from a provided data model. Different data types have different column UI, e.g. type "boolean" 
              is displayed as a checkbox that is checked for *true* and unchecked for *false*. Almost all 
              of __RadGrid__'s features benefit from a correct data model including filtering, sorting, data editing and more.
            

More information on how to provide a data model using __DataSource__ is provided in these two articles:
              [DataSource Remote Binding](5764a8ba-3fe5-49dc-9d6c-7248f48939fc)

# RadGrid Performance Tips

Below you can find guidelines you can refer to in case you start experiencing some performance issues using __RadGrid__.
        

# Avoid Retrieving Large Amounts of Remote Data

__RadGrid__’s performance can be hindered if the retrieval of remote data, needed to populate the grid, takes too much time.
              Mobile devices often have limited or slow internet access, so this can be a really big problem for users. Try requesting
              only the necessary amount of data over the internet. Enabling __virtual scrolling__ can greatly help to 
              enhance performance. This feature makes the __DataSource__ retrieve only data that is going to be visualized.
            

For a full set of instructions how to set up the virtual scrolling feature, refer to this article:
              [RadGrid Scrolling](d54c69fb-7664-4e14-ad48-4675b627ac03)

# Minimize the Number of Columns

If you are experiencing performance issues using __RadGrid__ and you have plenty of columns in your grid, try
              keeping only the most important and necessary ones. This can help enhance performance and provide the users with a more informative
              data table.
            

# Minimize the Use of Other Controls in RadGrid

Using a visualization control inside __RadGrid__, e.g. __RadSparkLine__, can provide a
              better user experience, but also can lead to performance loss. The problem is, the controls need to be initialized by the
              __processAll()__ method and because __RadGrid__ can contain thousands of data entries,
              thousands of controls need to be initialized, which takes some time. To provide a better user experience, you should call the
              __processAll()__ method individually for each control and use the __requestAnimationFrame()__ 
              method for better visualization animation.
            

Code samples and information regarding how this can be done are provided in the following article: 
              [](a0dd0c7f-7692-42d6-bd37-7ba42ed59108)

# Related Topics
