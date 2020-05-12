---
title: "Install Power BI Connector to use CQD query templates"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: siunies
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
description: "Install Power BI Connector to use CQD query templates"
---


# Install Power BI Connector to use CQD query templates

Before you can use the Power BI query templates for CQD (PBIX files), you'll need to install the Power BI Connector for Microsoft CQD, using the *MicrosoftCallQuality.pqx* file included in the [download](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). 

Read [Use Power BI to analyze CQD data for Teams](CQD-Power-BI-query-templates.md) to learn about these templates.

Make sure you have the right [CQD access role](https://docs.microsoft.com/microsoftteams/turning-on-and-using-call-quality-dashboard#assign-roles-for-accessing-cqd) to access the Power BI reports. 

## Installation

The process for installing a custom connector and adjusting security to enable use of the connector is described in detail in the [Power BI documentation](https://docs.microsoft.com/power-bi/desktop-connector-extensibility). For the sake of simplicity, here's a quick explanation:

1.  Check to see if your computer already has a *\[Documents\]\\Power BI Desktop\\Custom Connectors* folder. If not, create this folder.<sup>1</sup>

2.  Download the connector file (either a *\*.mez* or *\*.pqx* file) and place it in the *Custom Connectors* directory.

3.  **If the connector file is a *\*.mez* file,** you will also need to adjust your security settings as described in the [custom connector setup documentation](https://docs.microsoft.com/power-bi/desktop-connector-extensibility#data-extension-security).

If a new version of this Power BI Connector for Microsoft Teams is released, simply replace the old connector file in the *Custom Connectors* directory with the new file.

## Setup

In order to build a report and run queries, you will first need to connect to the CQD data source. Follow the steps below in order to connect:

1.  In the Home tab of Power BI Desktop, click on *Get Data*.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector1.png)

2.  The *Get Data* window should appear at this point. Navigate to *Online Services*, then select *Microsoft Call Quality (Beta)* and hit *Connect*.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector2.png)

3.  You will be prompted to login next. Use the same credentials that you use for CQD.<sup>2</sup>

4.  The next prompt will give you the option between two *Data Connectivity modes*. Select *DirectQuery* and hit *OK*.

5.  Finally, you will be given a final prompt showing you the entire data model for CQD. No data will be visible at this point, only the data model for CQD. Select *Load* to complete the setup process.

6.  At this point, Power BI will load the data model onto the right side of the window. The page will remain otherwise blank, and no queries will be loaded by default. Proceed to **Building Queries** below in order to build a query and return data.

If any of the steps during this setup process were not completely clear, a more detailed explanation of the process can be found [here](https://docs.microsoft.com/power-bi/desktop-quickstart-connect-to-data).

## Building Queries

Once setup is complete, you should see the names of several hundred dimensions and measures load in the *Fields* pane. Constructing actual queries from here is simple, just select the dimensions and measures you want for your query, then drag and drop them onto the page. Here's a more detailed explanation, with a simple example:

1.  Select the visualization you want to use from the *Visualizations* pane. A blank version of that visualization should appear on the page. For the purposes of this example, we will be using the *Table* visualization.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector3.png)

2.  Determine which dimensions and measures (denoted by an aggregation symbol by their name) you wish to use for your query, then manually select them and drag them onto the black visualization. Alternately, drag them onto the *Values* field beneath the visualization options.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector4.png)

    > [!IMPORTANT] 
    > Call Quality Dashboard requires a measure for any query to run. Failure to add a measure to a query will cause that query to fail.

3.  Next, select any dimensions you want to filter on and drag them to the *Filters on this visual* field in the *Filters* pane. The CQD Power BI Connector currently supports *Basic filtering* (select values from a list of possible dimension values), *Advanced filtering* (manually specify values and operands to filter on, similar to Advanced CQD), and *Relative date filtering* (only available for the *End Time* and *Start Time* dimensions). Filtering according to *Top N* is not supported by CQD.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector5.png)

4.  Finally, select the *Format* tab within the *Visualizations* pane to style and format your query.

    > [!NOTE]
    > CQD queries require at least one measure in order to run. If your query does not load, double check that you have included a measure in the query.

## Creating a Drillthrough Report

[Drillthrough in Power BI](https://docs.microsoft.com/power-bi/desktop-drillthrough) allows you to create focused reports that you can quickly filter using the values of other reports as context. Once you know how to create your first query with the CQD Connector, creating a drillthrough is even simpler.

1.  Create another page for the focused report, and then add your queries to that page.

2.  Select the dimension you want to use as a drillthrough filter and drag them onto the *Drillthrough* field under on the *Visualizations* pane.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector6.png)

3.  **That's it\!** Any other query on another page that uses that dimension can now drillthrough to that page, automatically applying the drillthrough dimension's value as a filter.

    ![Screenshot: Power BI Connector](media/CQD-power-bi-connector7.png)

Unlike Advanced CQD, Power BI supports non-sequential drillthrough. So long as a query includes the necessary dimension, it can drillthrough to any other page.

### Best practice

Call Quality connector queries should be designed with drillthrough functionality in mind. Instead of trying to load all the data at once, and then slicing down with filters, start with broader, low-cardinality queries and drill down to high-cardinality queries. For instance, when attempting to diagnose which subnets contribute most to quality issues, it's helpful to first identify those regions and countries which contribute to the problem, then drill down to the subnets in that region or country. The Call Quality connector templates have been designed in this manner in order to act as an example.

## Limitations

Despite making use of Power BI, not all Power BI functionality is support by the CQD Connector, either as a result of limitations on CQD data model or on DirectQuery connectors in general. The list below notes some of the Connector's more noteworthy limitations, but this list should not be considered exhaustive:

1.  **Calculated Columns –** DirectQuery connectors in general have limited support for calculated columns in Power BI. While some calculated columns may work with the Connector, these should be considered exceptions. As a general rule, calculated columns will not function.

2.  **Aggregations –** The CQD data model is built on a cube model, meaning that aggregations are already supported in the form of measures. Attempting to manually add aggregations to different dimensions or changing the aggregation type of a measure will not work with the Connector, and it will generally result in an error.

3.  **Custom Visuals –** While the CQD Connector does work with a range of custom visuals, we are unable to guarantee compatibility with all custom visuals. Many custom visuals rely on the use of calculated columns or imported data, neither or which are supported by DirectQuery connectors.

4.  **Referencing Cached Data –** Power BI currently does not support referencing cached data from a DirectQuery connector in any way. Any attempt to reference the results of a query will result in a new query. 

5.  **Relative Data Filtering –** Is supported in the CQD Connector, but only with the *Start Time* and *End Time* dimensions. Although the *Date* dimension may be the obvious choice for relative date filtering, *Date* is not stored as a date time object and thus does not support relative date filtering in Power BI.

Please note, although the Connector is in preview, these limitations are unlikely to change with the final release of the Connector. Most of these issues are either restrictions to DirectQuery connector design in Power BI or fundamental to the design of the CQD data model.

## Troubleshooting

### I'm trying to use the Date column as a Date slicer. As soon as I convert the data type of this column to Date, I get this error:

> **Couldn't load the data for this visual**: OLE DB or ODBC error: [Expression.Error] We couldn't fold the expression to the data source. Please try a simpler expression. 

Date slicers aren't supported with the Power BI Connector. To specify a date range, apply two filters to the report, specifying a less than and greater than date.

Alternatively, if the dates you want to view are recent, apply a relative date filter to show only data for the last N days/weeks/months.

## Error Codes

Because the CQD Power BI Connector is less restricted than the browser app in terms of kinds of queries you can construct, you may occasionally encounter a number of errors while building your queries. In the event that you receive an error message of the type "CQDError. RunQuery – Query Execution Error", reference the list below with the ErrorType number provided in order to troubleshoot the possible issue with the query. The following are the most common Error Type codes you may encounter with the CQD Power BI Connector:

  - **ErrorType 1 - Query Structure Error:** A query structure error is typically caused by the Connector failing to build a properly formatted query. This happens most often when using unsupported functionality, as specified in the Limitations above. Double check that you are not using any calculated columns or custom visuals for that query.

  - **ErrorType 2 - Query Building Error:** A query building error is caused by the CQD Connector being unable to properly parse the query you are attempting to build. This happens most often when using unsupported functionality, as specified in the Limitations above. Double check that you are not using any calculated columns or custom visuals for that query.

  - **ErrorType 5 - Execution Timeout:** The query has reached the maximum possible runtime before timing out. Try adding more filters to the query in order to limit its scope. Narrowing the data range is often the most effective way to achieve this.

  - **ErrorType 7 - No Measurements Error:** CQD queries require a measure in order to function. Double check that your query includes measure. Measures in the CQD Connector are denoted by the aggregation (sum) symbol before their name.

If you encounter any additional errors outside of this scope, please notify the CQD team so that we can help troubleshoot the issue and update the documentation as appropriate.

## Footnotes

**<sup>1</sup>** Certain processes and apps (e.g., OneDrive) may cause your Documents root folder to change; make sure that the *Power BI Desktop\\Custom Connectors* directory is placed inside of the current root folder Documents folder.

**<sup>2</sup>** The login credentials you use for CQD *do not* need to be the same credentials you use for logging into the Power BI Desktop app itself.

## Frequently asked questions

### When will the Power BI Connector be updated from "Beta" status?

Despite the Beta tag, the Call Quality Connector for Power BI is the release version of the connector and has been officially security signed by the Power BI team to reflect this. The certification process to remove that Beta tag is an extensive one and requires a commitment from the Power BI team to provide direct support to the connector as well. Due to time constraints, the Power BI team is currently unable to provide that support and broader certification, but is still prepared to attest to the security, authenticity, and general functionality of the Microsoft Call Quality connector.

### Why does the connector seem so slow compared to Advanced CQD in the browser? What can I do to improve performance?

Query performance for the various templates is actually the same in both the browser and in the connector. The difference comes in the number of concurrent queries being run. Because the in-browser version of CQD had less well-developed and information-dense visualization options, most of our reports were limited to loading 2-3 queries at a time. On the other hand, the connector templates often display 20+ concurrent queries. If you wish to build reports that are just as responsive as the older ones you were used to, try creating reports with no more than 2-3 queries per tab.

### I find that I routinely run into the 10,000-row limit when running queries. How can I get the connector to return more than 10,000 rows?

The 10,000-row limit is actually specified on the API end, and it is designed to help significantly improve performance and reduce the risk of query execution errors resulting from low memory conditions.

Instead of attempting to increase the result row count, it is best to restructure your reports according to connector best practices. The templates we have included are designed to demonstrate these best practices. Where possible, start by looking at your KPIs using broader, lower-cardinality dimensions, such as Month, Year, Date, Region, Country, etc. From there, you can drill down into increasingly higher-cardinality dimensions. The Helpdesk and Location-Enhanced Reports both provide good examples of this drill down workflow.



## Related topics

[Use Power BI to analyze CQD data for Teams](CQD-Power-BI-query-templates.md)
