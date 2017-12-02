### Overview 

Events are a key element of tourism — in fact, Airbnb was founded in 2008 to offer affordable accommodation during periods of high, event-driven demand. Many Airbnb teams — local operations, pricing, supply growth, public policy and PR — rely on an understanding of events to inform everything from product changes to city policy negotiations.

This "one-button" data product was created in RMarkdown. Integrated with Google Sheets and our internal Presto engine, the .Rmd file downloads event parameters from the Sheet (event name, location, dates), dynamically builds and executies SQL queries, and visualizes the data in a brand-style, ready-to-use .html infographic report.

The project utilized:
* Dynamic, highly optimized SQL code (just 3 queries pull all data in the report)
* Advanced ggplot2 and design techniques in R 
* Advanced RMarkdown looping techniques to accomodate multiple events in one report  

![](images/report1.png)

![](images/report2.png)

![](images/report3.png)