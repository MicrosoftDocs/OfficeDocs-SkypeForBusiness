---
title: "Call Admission Control Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ea4b0c9f-7f93-4b8a-b901-01e1636c44fb
description: "Summary: Learn about the Call Admission Control Reports used in Skype for Business Server."
---

# Call Admission Control Report in Skype for Business Server
 
**Summary:** Learn about the Call Admission Control Reports used in Skype for Business Server.
  
The Call Admission Control Report provides information about peer-to-peer and conferencing sessions that were conducted under restrictions set in place by Call Admission Control. Call Admission Control provides a way for administrators to allow (or not allow) communication sessions based on bandwidth constraints. For example, administrators can create policies that impose a limit on the amount of bandwidth available for voice and video calls. If that bandwidth limit has been reached, then no new voice or video calls can be placed until one of the current calls has ended and freed up the required network resources.
  
## Accessing the Call Admission Control Report

The Call Admission Control Report is accessed from the Monitoring Reports home page. From the Call Admission Control Report you can drill down to either of the following reports:
  
- Conference Detail Report - To access this report, click the Details metric from a conference session. 
    
- Peer-to-Peer Session Detail Report - To access this report, click the Details metric for a peer-to-peer session.
    
## Making the Best Use of the Call Admission Control Report

To get a list of calls that failed because of insufficient bandwidth, select Calls rejected because of call admission control from the Call category dropdown list. Most of the returned calls will likely have a diagnostic ID of 5:
  
Insufficient bandwidth to establish session. Attempt PSTN re-route.
  
That indicates that Call Admission Control limitations were preventing the call from being made on the VoIP network.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Call Admission Control Report enables you to filter calls by the user who initiated the call or by the user who was being called. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Call Admission Control Report.
  
**Call Admission Control Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/17/12015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/17/12015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/13/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/17/12015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/17/12015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/13/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Activity type** <br/> | Type of activity. Select one of the following activities: <br/>  [All] <br/>  Peer-to-Peer <br/>  Conference <br/> |
|**Call category** <br/> | Indicates the reason that CAC was used for the call. Select one of the following: <br/>  [All] <br/>  Call rejected because of call admission control <br/>  Calls rerouted through PSTN because of call admission control <br/> |
   
## Metrics for Peer-to-Peer Sessions

The following table lists the information provided in the Call Admission Control Report for peer-to-peer sessions (that is, sessions involving just two participants).
  
**Metrics for Peer-to-Peer Sessions**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Detail** <br/> |No  <br/> |When you click this item, the report shows you a Peer-to-Peer Session Detail Report for the specified session.  <br/> |
|**From user** <br/> |Yes  <br/> |SIP address of the user who initiated the session.  <br/> |
|**To user** <br/> |Yes  <br/> |SIP address of the user who was invited to join the session.  <br/> |
|**Modalities** <br/> |Yes  <br/> |Communication modalities (such as audio and video) that were used during the session.  <br/> |
|**Invite time** <br/> |Yes  <br/> |Date and time the initial session invitation was sent to the From user.  <br/> |
|**Response time** <br/> |Yes  <br/> |Date and time that the invitation acceptance was received.  <br/> |
|**End time** <br/> |Yes  <br/> |Date and time that the session ended.  <br/> |
|**Diagnostic ID** <br/> |Yes  <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.  <br/> |
   
## Metrics for Conferencing Sessions

The following table lists the information provided in the Call Admission Control Report for conferencing sessions (that is, sessions involving three or more participants).
  
**Metrics for Conferencing Sessions**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Conference URI** <br/> |Yes  <br/> |Unique identifier for the conference. When you click this item, the report shows the individual conference participants.  <br/> |
|**Organizer** <br/> |Yes  <br/> |SIP address of the user who organized the conference.  <br/> |
|**Pool** <br/> |Yes  <br/> |Edge Server used in the conference.  <br/> |
|**Start time** <br/> |Yes  <br/> |Date and time that the conference started.  <br/> |
|**End time** <br/> |Yes  <br/> |Date and time that the conference ended.  <br/> |
   
## Metrics for Individual Conference Participants

The following table lists the information provided in the Call Admission Control Report for individual conference participants.
  
**Metrics for Individual Conference Participants**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Role** <br/> |No  <br/> |Role (for example, Presenter) played by the conference participant.  <br/> |
|**Participant** <br/> |No  <br/> |SIP address of the conference participant.  <br/> |
|**Connectivity** <br/> |No  <br/> |Network connectivity (typically From Internal or From External) for the participant.  <br/> |
|**Modality** <br/> |No  <br/> |Conference type (for example, A/V conferencing).  <br/> |
|**Join time** <br/> |No  <br/> |Date and time that the participant joined the conference.  <br/> |
|**Leave time** <br/> |No  <br/> |Date and time that the participant left the conference.  <br/> |
|**Diagnostic ID** <br/> |No  <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.  <br/> |
   

