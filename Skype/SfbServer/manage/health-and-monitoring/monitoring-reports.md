---
title: "Using Monitoring Reports in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 733577d0-c70f-4c70-ab7b-59b89fb495a8
description: "Summary: Learn about Monitoring Reports in Skype for Business Server."
---

# Using Monitoring Reports in Skype for Business Server 
 
**Summary:** Learn about Monitoring Reports in Skype for Business Server.
  
Skype for Business Server includes a set of standard reports that are published by Microsoft SQL Server Reporting Service. These reports, which are accessible by using a web browser, provide usage, call diagnostic information, and media quality information, all based on call detail recording (CDR) and Quality of Experience (QoE) records stored in the CDR and QoE databases.
  
To use these reports, you must install Monitoring Reports on a computer that is running an instance of the SQL Server.
  
## In This Section

- [Using the Monitoring Dashboard in Skype for Business Server](monitoring-dashboard.md) Provides administrators with a quick overview of their system health and system usage.
    
- [System usage reports in Skype for Business Server](system-usage-reports.md) Provides system usage information based on CDR data collected by Skype for Business Server.
    
- [Call Diagnostic Reports (per user) in Skype for Business Server](call-diagnostic-reports-per-user.md) Provides per-user information about failed peer-to-peer and conferencing sessions.
    
- [Call Diagnostic Reports in Skype for Business Server](call-diagnostic-reports.md) Provides summary information and diagnostic data for failed peer-to-peer and conferencing sessions.
    
- [Media Quality Diagnostic Reports in Skype for Business Server](media-quality-diagnostic-reports.md) Provides information about call quality as well as diagnostic and troubleshooting information for failed calls.
    
## Locating Records

Monitoring Reports only show a limited number of records on the screen at any one time. The actual number of records displayed on a screen varies depending on the report. To view the records that are not currently shown on the screen you can use the standard forward and backward control (found on each report's toolbar) that enable you to page through the data. You can also quickly jump to the first page or the last page of the dataset.
  
In addition to using the forward and backward controls, you can also jump to any page in the dataset simply by typing the page number in the **Current Page** box, and then press ENTER.
  
In addition to providing the ability to page through the data, each report also includes the limited ability to find records. To find records based on a given value, type that value into the **Find** box, and then click **Find**. The report begins searching through the data and stops on the first instance of the value that you entered in the **Find** box. To find the next record that meets the search criteria, click **Next**.
  
As noted, the Monitoring Reports provide only the most basic search functions. For example, you cannot specify which field the value should be found in. The search mechanism automatically searches for matching values in every field in every record. You cannot use wildcards in your searches, and all searches look for partial values. That means that if you search for 111 the search returns the value 111 along with the values 11100, 811, 3112, 611A5B, and any other fields that include the value 111 anywhere within that field.
  
Each report is configured to show a default set of records. For example, by default the User Registration Report shows user registration activities for the past week. In some cases, this might result in a report that returns no records. In this case, it means that no user registrations have taken place in the past week. If you see the message "No results match the report filters," try changing the filter values (for example, change the time period to the past month rather than the past week) and rerun the query. For details, see the "Filtering Data" section later in this topic.
  
## Filtering Data

There will likely be times when you want to look at only a subset of records. For example, only peer-to-peer sessions as opposed to both peer-to-peer sessions and conference sessions. Likewise, there will be times when you need to reduce the number of records that are returned. By default, a report can only display the first 1,000 records in a data set. To address these issues, most reports include a number of filtering options. For example, if you want to view only records for the time period January 1, 2011 through January 15, 2011, you can enter January 1, 2011 in the **From** box and January 15, 2011 in the **To** box. If you then click **View Report**, the returned data will be limited to activities that took place between January 1, 2011 and January 15, 2011.
  
The filters available to you vary depending on the report that you are viewing. For details about a specific report, see the help topic for that report.
  
## Exporting Data

The Monitoring Reports provide at least two different ways to export the data included in a report. You can use the **Export** option in the toolbar that appears at the top of each report. To use this option, select the desired export format from the **Select a format** drop-down list. The following formats are available to you:
  
- XML file with report data
    
- CSV (comma delimited)
    
- Acrobat (PDF) file
    
- MHTML (web archive)
    
- Excel
    
- TIFF file
    
- Word
    
After selecting a format, click **Export**. When the **File Download** dialog box appears, click **Save**. In the **Save As** dialog box, select a destination folder, enter a file name, and then click **Save**.
  
If you have Microsoft OneNote installed, you can also copy the report data to OneNote. To do this, right-click the **View Report** button on the toolbar. In the **Select Location in OneNote** dialog box select the section in OneNote where you want to copy the data, and then click **OK**.
  

