---
title: "Using the Monitoring Dashboard in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e00e5783-116f-481f-ad17-3af847d6769a
description: "Summary: Learn about the Monitoring Dashboard in Skype for Business Server."
---

# Using the Monitoring Dashboard in Skype for Business Server
 
**Summary:** Learn about the Monitoring Dashboard in Skype for Business Server.
  
The Monitoring Dashboard provides administrators with a quick overview of their Skype for Business Server system health and system usage. The Dashboard is designed to show an aggregate view of key system metrics and to do so by displaying either:
  
- Totals for the current day. Note that values shown for the current day represent data that has been recorded from midnight until the current time (based on the local time of the reporting server). That means that you will typically be viewing data for a partial day and not for a 24-hour period. For example, if the local time of the server is 8:00 AM, you see eight hours' worth of data because there are eight hours between midnight and the current time of 8:00 AM.
    
- Totals for the week, and trend totals for the past six weeks.
    
- Totals for the month, and trend totals for the past six months (for system usage only).
    
Note that you can use the [Get-CsReportingConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csreportingconfiguration?view=skype-ps) cmdlet to return the URL used for accessing Skype for Business Server Monitoring Reports:
  
```
Get-CsReportingConfiguration
```

By default, the Monitoring Dashboard shows data for the following metrics for the current week (and trend totals for the previous six weeks):
  
## System Usage Metrics

 **Registration**
  
- Unique user logons
    
  **Peer-to-peer**
  
- Total sessions
    
- IM sessions
    
- Audio sessions
    
- Video sessions
    
- Application sharing
    
- Total audio session minutes
    
- Avg. audio session minutes
    
  **Conference**
  
- Total conferences
    
- IM conferences
    
- A/V conferences
    
- Application sharing conferences
    
- Web conferences
    
- Total organizers
    
- Total A/V conference minutes
    
- Avg. A/V conference minutes
    
- Total PSTN conferences
    
- Total PSTN participants
    
- Total PSTN participant minutes
    
In addition to the System Usage metrics, the following metrics displays total for the current day and the previous six days (if you select **Weekly View**) or for the current week and the past six weeks if you select **Monthly View**.
  
## Per-User Call Diagnostics

 **Users with call failures**
  
- Total users with call failures
    
- Conference organizers with call failures
    
  **Users with poor quality calls**
  
- Total users with poor quality calls
    
## Call Diagnostics

Peer-to-peer
  
- Total failures
    
- Overall failure rate
    
- IM failure rate
    
- Audio failure rate
    
- Application sharing failure rate
    
Conference
  
- Total failures
    
- Overall failure rate
    
- IM failure rate
    
- A/V failure rate
    
- Application sharing failure rate
    
Top five servers by failed sessions
  
## Media Quality Diagnostics

Peer-to-peer
  
- Total poor quality calls
    
- Poor quality call percentage
    
- PSTN calls with poor quality
    
Conference
  
- Total poor quality calls
    
- Poor quality call percentage
    
- PSTN calls with poor quality
    
Top worst servers by poor quality call percentage
  
## Working with the Monitoring Dashboard

As noted, by default totals are shown for the current week and trend values are shown for the past six weeks. If you would prefer to see totals for the current month (as well as trend values for the past six months), click the **Monthly View** link in the upper right corner of the dashboard. If you decide to view monthly totals, the link text will change to **Weekly View**. You can switch back to the weekly view by clicking that link.
  
> [!TIP]
> The Monitoring Dashboard restricts you to looking at totals for the current week (or month) and trend values for the past six weeks (or months). You cannot change these dates and times. For example, you cannot use the Dashboard to view report totals for the time period beginning nine months ago. 
  
The values shown in the **This week**, **This month**, or **Today** columns link you to more detailed information about the item. Keep in mind that the column name and the values displayed in that column will often differ depending on the metric chosen and depending on whether you have selected weekly view or monthly view. For example, if you click the totals shown for the **Unique user logons** metric you will see the **User Registration Report** for the specified time period. You can return to the Monitoring Dashboard at any time by clicking **Dashboard**.
  
> [!TIP]
> You can also access the Monitoring Server Reports home page by clicking the **Reports** link in the upper right corner of the Dashboard.
  
The **Trend** column displays a simple line graph that shows totals for the past six weeks (or, depending on the metric and the time interval, the past six days or the past six months). These simple line graphs display one unlabeled data point for each time period (for example, one unlabeled data point for each of the past six weeks). However, you can retrieve actual values for these graphs by holding your mouse pointer over the graph. In that case, a tool tip shows you the maximum and minimum values in the graph.
  
## Exporting Data from the Monitoring Dashboard

The Monitoring Dashboard provides a number of ways to export the current dashboard view. On the Dashboard toolbar, you'll see an icon that looks like a floppy disk with a green arrow attached to it. If you click this icon, a dropdown list will appear giving you the following data export formats:
  
- XML file with report data
    
- CSV (comma delimited)
    
- PDF
    
- MHTML (web archive)
    
- Excel
    
- TIFF file
    
- Word
    
To export the current dashboard view (and its values), click the desired export option. Skype for Business Server generates a report in the specified format and then give you the option of opening that report or saving it. Note that, by default, Skype for Business Server titles the report **Monitoring Dashboard** and saves it to your Downloads folder. To give the report a different name or to store it in a different folder, click the arrow next to the **Save** button and then click **Save As**. If you are fine with name **Monitoring Dashboard** and with having the report saved in the Downloads folder you can just click the **Save** button.
  
It's possible that, when you try to export dashboard data, a **Security Alert** dialog box will appear along with the message "Your current settings do not allow this file to be downloaded." If that occurs, do the following:
  
- In Internet Explorer, select **Internet Options**.
    
- In the **Internet Options** dialog box, on the **Security** tab, click **Trusted sites** and then click **Sites**.
    
- In the **Trusted sites** dialog box, click **Add** to add the Skype for Business Server that is running Skype for Business Server Reports to the collections of trusted websites.
    
- Click **Close** and then click **OK**.
    
You will then need to refresh the Monitoring Dashboard before the changes take effect. To do that, either press F5 or click the **Refresh** icon in the Dashboard toolbar. (The **Refresh** icon is a circle with a pair of green arrows in it.)
  
You can also create an Excel spreadsheet that includes live data feeds, which includes links to the latest Monitoring Dashboard data. To create a live data feed file, click the orange **Export to Data Feed** icon in the toolbar.
  
If you would prefer to print the current Dashboard then click the printer icon in the toolbar.
  

