---
title: "Conference organizer activity report"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, wlooney
ms.topic: article
ms.assetid: 03a255d4-0e1d-4b24-b73d-7a62fae36254
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: 
- O365E_ReportsS4BOrgActivity
ms.custom:
- Reporting
description: "Learn how to get the Skype for Business Conference Organized Activity report, and how to interpret and customize it. "
---

# Conference organizer activity report

The new Office 365 **Reports** dashboard shows you the activity overview across the Office 365 products in your organization. It enables you to drill in to individual product level reports to give you more granular insight about the activities within each product. For example, you can use the **Skype for Business conference organizer activity** report to see how much your users are organizing conferences that use IM, audio/video, application sharing, Web, dial-in/out - 3rd party, and dial-in/out - Microsoft. 

Check out the [Reports overview](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263) to learn more.
  
This report, along with the other Skype for Business reports, gives you details on organized conferences activity across your organization. These details are very helpful when you are investigating, planning, and making other business decisions for your organization. 
  
> [!NOTE]
> You can see all of the Skype for Business reports when you log on as an administrator to the Office 365 admin center. 
  
## How to get to the Skype for Business conference organizer report

1. Go to the **Office 365 admin center** > **Reports** > **Usage**.
    
2. On the **Usage** page, click **Skype for Business conference organizer activity** on the **Select a report list** on the left. Or, click the **Skype for Business activity** widget and then click **Skype for Business conference organizer activity** on the **Skype for Business activity** list.
    
     ![Menu for Skype reports with Business conference organizer activity highlighted](../images/3fee95f4-efa1-48f2-89af-a705f8f8b732.PNG)
  
    > [!IMPORTANT]
    > Depending on the Office 365 subscription you have, you might not see all the products and activity reports shown here. 
  
## Interpret the Skype for Business conferences organizer report

You can get a view into your Skype for Business conferences that were organized by looking at the **Activity**, **Users**, and **Minutes** charts.
  
![Skype for business Organized conferences report](../images/0ab0e5e8-cf18-4f8f-a31a-94048e375a0f.PNG)
  
***
![Number 1](../images/sfbcallout1.png)<br/>The **Skype for Business Conference Organizer Activity** report can be viewed for trends over the last 7 days, 30 days, 90 days, or 180 days. However, if you click into a particular day in the report, the table (see number 7) will show data for 30 days, up to the date (see number 2) for when the report was generated.

> [!NOTE]
> If you click into the details of a specific day, the table will only show data for the 30 days up to the date when the report was generated.

***
![Number 2](../images/sfbcallout2.png)<br/>Each report has a date for when this report was generated. The reports usually reflect a 24- to 48-hour latency from time of activity. 
***
![Number 3](../images/sfbcallout3.png)<br/>Use the interactive chart and real-time data on the **Activity** chart to understand usage trends and to see the total number of conferences that were organized and the type of conferences that are being held in your organization. It will show you the total number and types of **IM**, **Audio/video**, **Application sharing**, **Web**, **Dial-in/out - 3rd party**, and **Dial-in/out Microsoft** conferences that were organized across your organization. 
***
![Number 4](../images/sfbcallout4.png)<br/>Use the interactive chart and real-time data on the **Users** chart to understand usage trends and to see the number of unique users that have organized conferences that are being held in your organization. It will show you the total number of users along with the types of **IM**, **Audio/video**, **Application sharing**, **Web**, **Dial-in/out - 3rd party**, and **Dial-in/out Microsoft** of conferences that were organized. 
***
![Number 5](../images/sfbcallout5.png)<br/>Use the interactive chart and real-time data on the **Minutes** chart to understand usage trends and to see the number of minutes that are used by users when they organize a conference using audio/video, and dial-in and dial-out - Microsoft as their conferencing provider. It will show you the total number of minutes of **Audio/video** and **Dial-in Microsoft minutes**, and **Dial-out Microsoft minutes** that are used during conferences that were organized.
***
![Number 6](../images/sfbcallout6.png)<br/>
Each chart has an 'X' (horizontal) and 'Y' (vertical) axis.
*    On the **Activity** activity chart, the Y axis is the total number of IM, audio/video, application sharing, Web, dial-in/out- 3rd party, and dial-in/out Microsoft of conferences that your users organized in your organization. 
*    On the **Users** activity chart, the Y axis is the total number users that held IM, audio/video, application sharing, Web, dial-in/out - 3rd party, and dial-in/out - Microsoft of conferences that your users organized in your organization.
*    On the **Minutes** activity chart, the Y axis is the total number of minutes audio/video, dial-in Microsoft minutes, and dial-out Microsoft minutes for conferences that your users organized in your organization.  

The X axis on both charts is the selected date range for this specific report. 
***
![Number 7](../images/sfbcallout7.png)<br/>
You can filter the series you see on the chart by clicking on an item in the legend. For example, on the **Activity** chart, click or tap **IM**, **Audio/video**, **Application sharing**, **Web**, **Dial-in/out - 3rd party**, and **Dial-in/out Microsoft** to see only the info related to each one. Changing this selection doesn't change the info in the grid table.
***
![Number 8](../images/sfbcallout8.png)<br/>The table shows you a breakdown of the organized conference activities per user. This shows all users that have Skype for Business assigned to them and conferences that they organized. You can add additional columns to the table. 
* **User name** is the name of the user. 
* **Deleted** indicates that the user's license was removed.<br/><br/>
  > [!NOTE]
  > Activity for a deleted user will still display in a report as long as he or she was licensed at some time during the selected time period. The **Deleted** column helps you to note that the user may no longer be active, but contributed to the data in the report.
     
* **Deleted date** is the date on which the user's license was removed. 
* **Last activity date (UTC)** is the last activity date (UTC) for that user. 
* **IM** shows the total number of IM conferences that were organized. 
* **Audio/video** shows the total number of audio/video conferences that were organized.
* **Application sharing** shows the total number of application sharing conferences that were organized. 
* **Web** shows the total number of Web conferences that were organized. 
* **Dial-in/out - 3rd party** shows the total number of dial-in/out Audio Conferences that were organized that use a 3rd party audio conferencing provider. 
* **Dial-in/out Microsoft** shows the total number of dial-in/out Audio Conferences that were organized. 
* **Audio/video minutes** shows the total number of minutes used in organized conferences that used audio/video. 
* **Dial-in Microsoft minutes** shows the total number of dial-in minutes used in meetings that were organized that use Microsoft as the Audio Conferencing provider. 
* **Dial-out Microsoft minutes** shows the total number of dial-out minutes used in meetings that were organized that use Microsoft as the Audio Conferencing provider. 

If your organization's policies prevents you from viewing reports where user information is identifiable, you can change the privacy setting for all these reports. Check out the **How do I hide user level details?** section in the [Activity Reports in the Office 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263).
***
![Number 9](../images/sfbcallout9.png)<br/>You can also export the report data into an Excel .csv file, by clicking or tapping **Export**.           <br/> ![Skype for Business Reporting Export Button.](../images/de7e2ab7-d70c-422f-a0ec-178b10f7dd51.png)<br/>This exports data of all users and enables you to do simple sorting and filtering for further analysis. If you have less than 2000 users, you can sort and filter within the table in the report itself. If you have more than 2000 users, in order to filter and sort, you will need to export the data.
***
![Number 10](../images/sfbcallout10.png)<br/>Click or tap the **Columns** icon in any of the columns to add or remove columns from the report.           <br/> ![Skype for Business Online Reporting Manage Button.](../images/4c8f5387-cebb-4d6c-b7d3-05c954a2c234.png)
   
## Want to see other Skype for Business reports?

- [Skype for Business activity report](activity-report.md) You can see how much your users are using peer-to-peer, organized, and participated in conferencing sessions.
    
- [Skype for Business device usage report](device-usage-report.md) You can to see the devices including Windows-based operating systems and mobile devices that have the Skype for Business app installed and are using it for IM and meetings.
    
- [Skype for Business conference participant activity report](conference-participant-activity-report.md) You can see how many IM, audio/video, application sharing, Web and dial-in/out conferencing conferences are being participated in.
    
- [Skype for Business peer-to-peer activity report](peer-to-peer-activity-report.md) You can see how much your users are using IM, audio/video, application sharing, and transferring files.
    
- [Skype for Business users blocked report](users-blocked-report.md) You can see the users in your organization that have been blocked from making PSTN calls.
    
- [Skype for Business PSTN usage report](pstn-usage-report.md) You can see the number of minutes spent in inbound/outbound calls and cost for these calls.
    
- [Skype for Business PSTN minute pools report](pstn-minute-pools-report.md) you can see the number of minutes consumed during the current month within your organization.

- [Skype for Business session details report](session-details-report.md) You can see details about individual user's call experiences.

## Related topics
[Activity Reports in the Office 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

  
 
