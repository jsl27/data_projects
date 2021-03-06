### Overview 

Events are a key driver of tourism. Airbnb teams (local ops, pricing, growth, public policy and PR) rely on an understanding of events to inform their strategic planning. This "one-button" data product was created in RMarkdown to facilitate automated, easy-to-understand data and metrics around events in local markets.

Integrated with Google Sheets and our internal Presto engine, the 600-line .Rmd file downloads event parameters from the Sheet (event name, location, dates); dynamically builds and executies SQL queries for the event and surrounding same-day periods; and visualizes data and metrics on a single brand-colored, ready-to-send .html infographic report.

The project utilized:
* Dynamic, highly optimized SQL code (just 3 queries pull all data in the report)
* Advanced ggplot2, design and data manipulating techniques in R 
* Advanced RMarkdown looping techniques to accomodate multiple events in one report  

The following is an example report. For data privacy reasons, the three sections of the report shown here are from three different events, and some data points are also whited-out.

![](images/report1.png)

![](images/report3.png)

![](images/report2.png)