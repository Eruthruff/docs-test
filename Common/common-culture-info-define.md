---
title: Define Culture Information
meta_title: Define Culture Information
meta_description: description.
slug: 
tags:define,culture,information
publish:True
---


__RadControls's__ built-in culture support gets all the information needed about a certain culture from WinJS's Globalization API. This 
        ensures that the cultures are always up to date. You can, however, modify an existing culture to your liking or even create an entirely new culture. This article 
        will provide information regarding the __culture__ object's properties, that you can modify.
      

# 

Below you can find a code sample of the culture object with the properties of the default culture *en-US* and descriptions 
          of each member.
        


 __js__
    


	                var en = {
	                    //The culture string
	                    name: "en-US",
	                    //The clock format. It is of type boolean - true means 24 hours format and false means 12 hours format.
	                    twentyFourHour: false,
	                    //Holds a set of general number formatting properties.
	                    numberFormat: {
	                        //The number format pattern is an array and has only one pattern - for negative numbers.
	                        //It's value must be one of these: "(n)", "-n", "- n", "n-", "n -".
	                        pattern: ["-n"],
	                        //The number of decimal places.
	                        decimals: 2,
	                        //The string that separates the number groups.
	                        ",": ",",
	                        //The string that separates the whole number from the fractional part.
	                        ".": ".",
	                        //The length of each number group.
	                        groupSize: [3],
	                        //Holds a set of properties that format the percent numbers.
	                        percent: {
	                            //Negative number pattern's possible values:
	                            //"-n %", "-n%", "-%n", "%-n", "%n-", "n-%", "n%-", "-% n", "n %-", "% n-", "% -n", "n- %".
	                            //Positive number pattern's possible values: 
	                            //"n %", "n%", "%n", "% n".
	                            pattern: ["-n %", "n %"],
	                            //The number of decimal places.
	                            decimals: 2,
	                            //The string that separates the number groups.
	                            ",": ",",
	                            //The string that separates the whole number from the fractional part.
	                            ".": ".",
	                            //The length of each number group.
	                            groupSize: [3],
	                            //The percent symbol.
	                            symbol: "%"
	                        },
	                        //Holds the set of properties that format the currency numbers.
	                        currency: {
	                            //Negative number pattern's possible values: 
	                            //"($n)", "-$n", "$-n", "$n-", "(n$)", "-n$", "n-$", "n$-", "-n $", "-$ n", "n $-", "$ n-", "$ -n", "n- $", "($ n)", "(n $)"
	                            //Positive number pattern's possible values: 
	                            //"$n", "n$", "$ n", "n $"
	                            pattern: ["($n)", "$n"],
	                            //The number of decimal places.
	                            decimals: 2,
	                            //The string that separates the number groups.
	                            ",": ",",
	                            //The string that separates the whole number from the fractional part.
	                            ".": ".",
	                            //The length of each number group.
	                            groupSize: [3],
	                            //The currency symbol.
	                            symbol: "$"
	                        }
	                    },
	                    //Holds the set of properties for calendar date formatting.
	                    calendars: {
	                        standard: {
	                            //Holds the different name formats of the days of the week.
	                            days: {
	                                //An array with the full names of the days of the week.
	                                names: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
	                                //An array with the abbreviated names of the days of the week.
	                                namesAbbr: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
	                                //An array with the short names of the days of the week.
	                                namesShort: ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa"]
	                            },
	                            //Holds the different name formats of the months of the year.
	                            months: {
	                                //An array with the full names of the months of the year.
	                                names: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
	                                //An array with the abbreviated names of the months of the year.
	                                namesAbbr: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
	                            },
	                            //Holds an array with the AM designators (standard, lower case and upper case).
	                            AM: ["AM", "am", "AM"],
	                            //Holds an array with the PM designators (standard, lower case and upper case).
	                            PM: ["PM", "pm", "PM"],
	                            //Holds a set of predefined date and time patterns used by the culture.
	                            patterns: {
	                                d: "M/d/yyyy",
	                                D: "dddd, MMMM dd, yyyy",
	                                F: "dddd, MMMM dd, yyyy h:mm:ss tt",
	                                g: "M/d/yyyy h:mm tt",
	                                G: "M/d/yyyy h:mm:ss tt",
	                                m: "MMMM dd",
	                                M: "MMMM dd",
	                                s: "yyyy'-'MM'-'ddTHH':'mm':'ss",
	                                t: "h:mm tt",
	                                T: "h:mm:ss tt",
	                                u: "yyyy'-'MM'-'dd HH':'mm':'ss'Z'",
	                                y: "MMMM, yyyy",
	                                Y: "MMMM, yyyy"
	                            },
	                            //The string that separates the date components (day, month, year).
	                            "/": "/",
	                            //The string that separates the time components (hours, minutes, seconds).
	                            ":": ":",
	                            //A property for the first day of the week (0 = Sunday, 1 = Monday etc.).
	                            firstDay: 0,
	                            //Represents the last year of a 100-year interval, that can be represented by a 2-digit formatted year. 
	                            //For example if this property is set to 2013, then in the date 04.05.12 will mean the 
	                            //year is 2012 and not 1912.
	                            twoDigitYearMax: 2029
	                        }
	                    }
	                };



In order to modify an existing culture, you need to first get the culture through the __getCultureInfo()__ method. Accessing properties 
          is done like in any other javascript object. Note that to modify the string members (__","__, __"."__, 
          __"/"__ and __":"__) you will need to access them through an indexer. After modifying the culture object, 
          you have to save it through calling the __setCultureInfo()__ method. A code sample of modifying the 
          *en-US* culture can be found below:
        


 __js__
    


	                var modEN = Telerik.Culture.getCultureInfo("en-US");
	                modEN.numberFormat[","] = ".";
	                modEN.numberFormat["."] = ",";
	                modEN.numberFormat.decimals = 3;
	                Telerik.Culture.setCultureInfo("en-US", modEN);



# Related Topics

 * [Overview]({{slug:overview}})

 * [Formatting]({{slug:formatting}})
