---
title: "PSTN usage report"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, wlooney
ms.topic: article
ms.assetid: 74eda791-c41f-4fd9-ae0b-913342e7ab04
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- Reporting 
description: "The new Skype for Business Admin Center Reports area shows you calling and audio conferencing activity in your organization. It enables you to drill into reports to give you more granular insight about the activities of each user. For example, you can use the Skype for Business PSTN usage details report to see the number of minutes spent in inbound/outbound calls and cost for these calls. You can view Audio Conferencing PSTN usage details including the cost of the call so that you can understand your usage and call billing details to determine usage within your organization."
---

# PSTN usage report

The new Skype for Business Admin Center **Reports** area shows you calling and audio conferencing activity in your organization. It enables you to drill into reports to give you more granular insight about the activities of each user. For example, you can use the **Skype for Business PSTN usage details** report to see the number of minutes spent in inbound/outbound calls and cost for these calls. You can view Audio Conferencing PSTN usage details including the cost of the call so that you can understand your usage and call billing details to determine usage within your organization.
  
Check out the [Reports overview](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263) for more reports that are available.
  
This report, along with the other Skype for Business reports, gives you details on activity including calling usage across your organization. These details are very helpful when you investigating, planning, and making other business decisions for your organization and for setting up [Communications Credits](/microsoftteams/what-are-communications-credits)
  
> [!NOTE]
> You can see all of the Skype for Business reports when you log on as an administrator to the Office 365 admin center. 
  
## How to get to the Skype for Business PSTN usage details report

![An icon showing the Skype for Business logo](../images/sfb-logo-30x30.png) **Using the Skype for Business admin center**

- Go to **Office 365 admin center** > **Admin centers** > **Skype for Business admin center** > **Reports** > **PSTN usage details**.
    
    > [!NOTE]
    > Depending on the Office 365 subscription you have, you might not see all the products and reports that are shown here. 
  
## Interpret the Skype for Business PSTN usage report

You can get a view into your user's Skype for Business PSTN usage by looking at each of the columns that are displayed.
  
This is what the report looks like.
  
![Skype for Business PSTN usage report](../images/79d7aadf-c69e-4d6a-8179-ab69dbbb2472.png)

***
![Number 1](../images/sfbcallout1.png)<br/>The table shows you a breakdown of the all PSTN usage per user. This shows all users that have Skype for Business assigned to them and their PSTN usage. You can add/remove columns to the table.
*    **Call ID** is the call ID for a call. It is a unique identifier for the call that is used when calling Microsoft service support.
*    **User ID** is the user's sign in name.
*    **Phone number** is the Skype for Business phone number that received the call for inbound calls or the number dialed for outbound calls.
*    **User location** is the country/region where the user is located.
*    **Caller ID** is caller's telephone number (Caller ID) for inbound calls, the number from which the call originated or the Skype for Business number from which the call originated for outbound calls.
*    **Call type** is whether the call was a PSTN outgoing or incoming call and the type of call such as a call placed by a user or an audio conference. The call types you may see are: 

     **Calling Plan Call Types** 
     *    **user_in** (the user received an inbound PSTN call) 
     *    **user_out** (the user placed an outbound PSTN call) 
     *    **user_out_conf** (the user added 2 or more PSTN participants to the call such as a 3-way conference call) 
     *    **user_out_transfer** (the user transferred the call to a PSTN number) 
     *    **user_out_forwarding** (the user forwarded the call to a PSTN number)

     **Audio Conferencing Call Types**
     *    **conf_in** (an inbound call to the Audio Conferencing bridge) 
     *    **conf_out** (an outbound call from the Audio Conferencing bridge usually to add a PSTN number to the conference)

     **Unified Communication Applications (UCAP)** 
     *    **ucap_in** (an inbound PSTN call to the UC application such as auto attendant or call queue) 
     *    **ucap_out** (an outbound PSTN call from the UC application such as auto attendant or call queue)
     *    **Note:** Calls that were transferred to a user from the UC application such as an auto attendant or call queue will not appear in the PSTN usage report as these call legs are peer to peer (P2P) audio calls. You may access the P2P calls in the Skype for Business Admin Center under "Tools > Skype for Business Call Analytics" and search by User Name or SIP address correlating the call by date/time and/or originating CLID (calling line ID). 
*     
     **Domestic/International** tells you whether the call that was placed was considered domestic (within a country/region) or international (outside of a country/region) based on the user's location. 
*    **Destination dialed** is the name of the country/region destination that is dialed such as France, Germany, or the United States (U.S.). 
*    **Number type** is the type of phone number that is from a user's phone number, a service or toll-free number.  
*    **Start Time (UTC)** is the time that the call was started or placed. 
*    **Duration** is how long the call was connected.  
*    **ConfID** is the conference ID of the audio conference. 
*    **Charge** is the amount of money or cost of the call that is being charged to your account. 
*    **Currency** is the type of currency that is used to calculate the cost of the call. 
*    **Capability** is the license used for the call. The license types you may see are: 
     *    **MCOPSTNPP** - Communications Credits <br/> **MCOPSTN1** - Domestic Calling Plan (3000 min US / 1200 min EU plans) 
     *    **MCOPSTN2** - International Calling Plan 
     *    **MCOPSTN5** - Domestic Calling Plan (120 min calling plan) 
     *    **MCOPSTN6** - Domestic Calling Plan (240 min calling plan) Note: Limited Availability
     *    **MCOMEETADD** - Audio Conferencing
     *    **MCOMEETACPEA** - Pay Per Minute Audio Conferencing
> [!NOTE]
> If you would like to run a report to include only pay per minute calls that are not included in your calling or conferencing subscription, filter the report with capability "MCOPSTNPP". Doing so will provide an itemization of all pay per minute calls.  For pay per minute audio conferencing, filter by "MCOMEETACPEA" instead of "MCOPSTNPP".  
***
> [!NOTE]
> You may also see "no data" in some fields. "No data" means the field is not applicable to the call type or capability. 
***
> [!NOTE]
> If you have a Telstra calling plan, you will not see any call detail records in the PSTN usage report. Please contact Telstra for your reporting needs. 
***
![Number 2](../images/sfbcallout2.png)<br/>Click to drag a column to **To group by a particular column, drag and drop the column header here** if you want to create a view that groups all of the data in one or more columns.
 ***
![Number 3](../images/sfbcallout3.png)<br/>You can also export the report data into a TAB delimited Excel file, by clicking or tapping the **Export to Excel** button. <br/><br/> This exports data of all users and enables you to do simple sorting and filtering for further analysis. If you have less than 2000 users, you can sort and filter within the table in the report itself. 
    > [!Note] 
    > Despite the export file named as .CSV (which implies a comma delimited export), as there may be commas in the data set, the file is actually delimited with **TABS** and not **COMMAS**.

## Want to see other Skype for Business reports?

- [Skype for Business activity report](activity-report.md) You can see how much your users are using peer-to-peer, organized, and participated in conferencing sessions.
    
- [Skype for Business device usage report](device-usage-report.md) You can to see the devices including Windows-based operating systems and mobile devices that have the Skype for Business app installed and are using it for IM and meetings.
    
- [Skype for Business conference organizer activity report](conference-organizer-activity-report.md) You can see how much your users are organizing conferences that use IM, audio/video, application sharing, Web, /dial out - 3rd party, and /dial out - Microsoft.
    
- [Skype for Business conference participant activity report](conference-participant-activity-report.md) You can see how many IM, audio/video, application sharing, Web and dial out audio conferences are being participated in.
    
- [Skype for Business peer-to-peer activity report](peer-to-peer-activity-report.md) You can see how much your users are using IM, audio/video, application sharing and transferring files.
    
- [Skype for Business users blocked report](users-blocked-report.md) You can see the users in your organization that have been blocked from making PSTN calls.

- [Skype for Business PSTN minute pools report](pstn-minute-pools-report.md) you can see the number of minutes consumed during the current month within your organization.

- [Skype for Business session details report](session-details-report.md) You can see details about individual user's call experiences.
    
## Related topics
[Activity Reports in the Office 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
  
  
 
