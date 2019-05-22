---
title: "Peer-to-peer activity report"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, wlooney
ms.topic: article
ms.assetid: d3b2d569-4ee9-44b8-92bf-d518142f0713
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords:
- O365E_ReportsS4BPeerActivity
- O365M_ReportsS4BPeerActivity
- O365P_ReportsS4BPeerActivity
ms.custom:
- Reporting
description: "Get a Skype for Business Peer-to-peer activity report, and learn how to interpret and customize it for your needs. "
---

# Peer-to-peer activity report

The new Office 365 **Reports** dashboard shows you the activity overview across the Office 365 products in your organization. It enables you to drill in to individual product level reports to give you more granular insight about the activities within each product. For example, you can use the **Skype for Business peer-to-peer activity** report to see how much your users are using IM, audio, video, application sharing, and transferring files. 

Check out the [Reports overview](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263).
  
This report, along with the other Skype for Business reports, gives you details on activity across your organization. These details are very helpful when you investigating, planning, and making other business decisions for your organization. 
  
> [!NOTE]
> You can see all of the Skype for Business reports when you log on as an administrator to the Office 365 admin center. 
  
## How to get to the Skype for Business peer-to-peer activity report

1. Go to the **Office 365 admin center** > **Reports** > **Usage**.
    
2. On the **Usage** page, click **Skype for Business peer-to-peer activity** on the **Select a report list** on the left. Or, click the **Skype for Business activity** widget and then click **Skype for Business peer-to-peer activity** on the **Skype for Business activity** list.
    
     ![Skype peer to peer menu selected](../images/603ec74a-7f39-4e12-8f10-00979f7ee977.PNG)
  
    > [!IMPORTANT]
    > Depending on the Office 365 subscription you have, you might not see all the products and activity reports shown here. 
  
## Interpret the Skype for Business peer-to-peer activity report

You can get a view into your Skype for Business peer-to-peer activity by looking at **Activity**, **Users**, and **Minutes** charts.
  
![Skype peer to peer report with callouts.](../images/82dec398-ca05-46c7-b0fe-affcbfc0ddd5.PNG)
  
***
![Number 1](../images/sfbcallout1.png)<br/>The **Skype for Business peer-to-peer activity** report can be viewed for trends over the last 7 days, 30 days, 90 days, or 180 days. However, if you click into a particular day in the report, the table (see number 7) will show data for 30 days, up to the date (see number 2) for when the report was generated.

> [!NOTE]
> If you click into the details of a specific day, the table will only show data for the 30 days up to the date when the report was generated.

***
![Number 2](../images/sfbcallout2.png)<br/>Each report has a date for when this report was generated. The reports usually reflect a 24- to 48-hour latency from time of activity. 
***
![Number 3](../images/sfbcallout3.png)<br/>Use the interactive chart data on the **Activity** chart to understand usage trends and to see the total number of sessions per session type being held in your organization. It will show you the total number and types of **IM**, **Audio**, **Video**, **Application sharing**, and **File transfers** sessions across your organization. 
***
![Number 4](../images/sfbcallout4.png)<br/>Use the interactive chart data on the **Users** chart to understand usage trends and to see the number of unique users that are participating in peer-to-peer activities that are being held in your organization. It will show you the total number of users along with the types of **IM**, **Audio**, **Video**, **Application sharing**, and **File transfers** in peer-to-peer sessions.
***
![Number 5](../images/sfbcallout5.png)<br/>Use the interactive chart data on the **Minutes** chart to understand usage trends and to see the number of minutes that are used by users doing peer-to-peer activities using audio and video. It will show you the total number of minutes of **Audio** and **Video** that is used in peer-to-peer sessions.
***
![Number 6](../images/sfbcallout6.png)<br/>Each chart has an 'X' (horizontal) and 'Y' (vertical) axis. 
*    On the **Activity** activity chart, the Y axis is the total number of IM, audio, video, application sharing and transferring files sessions that your users held in your organization.
*    On the **Users** activity chart, the Y axis is the total number users that held IM, audio, video, application sharing, and transferring files sessions. 
*    On the **Minutes** activity chart, the Y axis is the total number of minutes that users across your organization spent using audio and video peer-to-peer sessions. 

The X axis on both charts is the selected date range for this specific report.
***
![Number 7](../images/sfbcallout7.png)<br/>You can filter the series you see on the chart by clicking on an item in the legend. For example, on the **Activity** chart, click or tap **IM**, **Audio**, **Video**, **Application sharing**, and **File transfers** to see only the info related to each one. Changing this selection doesn't change the info in the grid table. 
***
![Number 8](../images/sfbcallout8.png)<br/>The table shows you a breakdown of the peer-to-peer activities per user. This shows all users that have Skype for Business assigned to them and their peer-to-peer activities. You can add additional columns to the table.
*    **User name** is the name of the user.
*    **Deleted** indicates that the user's license was removed. <br/> <br/> **Note:**  Activity for a deleted user will still display in a report as long as he or she was licensed at some time during the selected time period. The **Deleted** column helps you to note that the user may no longer be active, but contributed to the data in the report.  <br/><br/>
*    **Deleted date** is the date on which the user's license was removed. 
*    **Last activity date (UTC)** is the last activity date (UTC) for that user.
*    **IM** shows the total number of peer-to-peer sessions that the user used.
*    **Audio** shows the total number of peer-to-peer sessions that used audio.
*    **Video** shows the total number of peer-to-peer sessions that used video.
*    **Application sharing** shows the total number of peer-to peer application sharing sessions.
*    **File transfers** shows the total number of peer-to peer file transfer sessions.
*    **Audio minutes** shows the total number of audio minutes that were used across your organization. 
*    **Video minutes** shows the total number of video minutes that were used across your organization. 

If your organization's policies prevents you from viewing reports where user information is identifiable, you can change the privacy setting for all these reports. Check out the **How do I hide user level details?** section in the [Activity Reports in the Office 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263). 
***
![Number 9](../images/sfbcallout9.png)<br/>You can also export the report data into an Excel .csv file, by clicking or tapping **Export**.           <br/> ![Skype for Business Reporting Export Button.](../images/de7e2ab7-d70c-422f-a0ec-178b10f7dd51.png)<br/>This exports data of all users and enables you to do simple sorting and filtering for further analysis. If you have less than 2000 users, you can sort and filter within the table in the report itself. If you have more than 2000 users, in order to filter and sort, you will need to export the data.
***
![Number 10](../images/sfbcallout10.png)<br/>![Skype for Business Online Reporting Manage Button.](../images/4c8f5387-cebb-4d6c-b7d3-05c954a2c234.png)<br/>Click or tap the **Columns** icon in any of the columns to add or remove columns from the report.         
   
## Want to see other Skype for Business reports?

- [Skype for Business activity report](activity-report.md) You can see how much your users are using peer-to-peer, organized, and participated in conferencing sessions.
    
- [Skype for Business device usage report](device-usage-report.md) You can to see the devices including Windows-based operating systems and mobile devices that have the Skype for Business app installed and are using it for IM and meetings.
    
- [Skype for Business conference organizer activity report](conference-organizer-activity-report.md) You can see how much your users are organizing conferences that use IM, audio/video, application sharing, Web, dial-in/out - 3rd party, and dial-in/out - Microsoft.
    
- [Skype for Business conference participant activity report](conference-participant-activity-report.md) You can see how many IM, audio/video, application sharing, Web and dial-in/out conferencing conferences are being participated in.
    
- [Skype for Business users blocked report](users-blocked-report.md) You can see the users in your organization that have been blocked from making PSTN calls.
    
- [Skype for Business PSTN usage report](pstn-usage-report.md) You can see the number of minutes spent in inbound/outbound calls and cost for these calls.
    
- [Skype for Business PSTN minute pools report](pstn-minute-pools-report.md) you can see the number of minutes consumed during the current month within your organization.

- [Skype for Business session details report](session-details-report.md) You can see details about individual user's call experiences.
    
## Related topics
[Activity Reports in the Office 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

  
 