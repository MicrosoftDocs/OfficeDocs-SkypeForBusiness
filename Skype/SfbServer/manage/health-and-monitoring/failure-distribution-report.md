---
title: "Failure Distribution Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 365c7beb-24d4-40f5-92e7-4978b9688916
description: "Summary: Learn about the Failure Distribution Report in Skype for Business Server."
---

# Failure Distribution Report in Skype for Business Server
 
**Summary:** Learn about the Failure Distribution Report in Skype for Business Server.
  
The Failure Distribution Report ranks failed sessions in the following categories:
  
- Top diagnostic reasons
    
- Top modalities
    
- Top pools
    
- Top sources
    
- Top components
    
- Top from users
    
- Top to users
    
- Top from user agents
    
You can use these categories to determine exactly where a problem is occurring and, in some cases, why the problem is occurring. For example, suppose you recorded 242 failed audio/video sessions during a given day. If you look at the Failure Distribution Report, it might show that 237 of those failed sessions took place in your Dublin pool. That gives you a good place to start when it comes to tracking down and diagnosing the causes behind those failures. If you click on the Dublin pool under the **Top pools** category, you will see a Failure Distribution Report just for that pool. You can then begin analyzing why the Dublin pool was experiencing so many difficulties.
  
## Viewing the Failure Distribution Report

You can access the Failure Distribution Report from any of the following reports by clicking either the **Expected failure volume** or the **Unexpected failure volume** metric:
  
- [Top Failures Report in Skype for Business Server](top-failures-report.md)
    
- [Conference Diagnostic Report in Skype for Business Server](conference-diagnostic-report.md)
    
- [Peer-to-Peer Activity Diagnostic Report in Skype for Business Server](peer-to-peer-activity-diagnostic-report.md)
    
From the Failure Distribution Report, you can click any of the following metrics to view the [Failure List Report in Skype for Business Server](failure-list-report.md):
  
- Top diagnostic reasons (sessions)
    
- Top modalities (sessions)
    
- Top pools (sessions)
    
- Top sources (sessions)
    
- Top components (sessions)
    
- Top from users (sessions)
    
- Top to users (sessions)
    
- Top from user agents (sessions)
    
## Using the Failure Distribution Report

Depending on your monitor size and screen resolution, it's possible that some of the data shown in the Failure Distribution Report might be truncated when you view it onscreen. This is especially true for metrics such as user agents, which can have very long labels. For example, a user agent with a name like "UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Lync 2013)" might only partially appear onscreen: 
  
UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Ly...
  
Fortunately, you can see the entire label simply by holding your mouse over the truncated value.
  
One interesting metric that you can filter on by using the Failure Distribution Report is Diagnostic ID. If you see the same Diagnostic ID cropping up in other reports you can filter on that ID in the Failure Distribution Report and get a very detailed look at exactly where, and how often, that ID has been reported during a failed session.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Failed Distribution Report enables you to filter on such things as the activity type (peer-to-peer session or conferencing session) or by the diagnostic ID that accompanied each failed session.
  
The following table lists the filters that you can use with the Failure Distribution Report.
  
**Failure Distribution Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Activity type** <br/> | Type of activity to filter on. Select one of the following: <br/>  [All] <br/>  Peer-to-peer <br/>  Conference <br/> |
|**Session category** <br/> | Indicates whether the activity in question succeeded or failed. Select one of the following: <br/>  [All] <br/>  Success <br/>  Expected failure <br/>  Unexpected failure <br/>  An "expected failure" is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail. An "unexpected failure" is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure. <br/> |
|**Diagnostic ID** <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.  <br/> |
   
## Metrics for Top Diagnostic Reasons

The following table lists the information provided in the Failure Distribution Report based on the most frequently reported diagnostic ID.
  
**Metrics for Top Diagnostic Reasons**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on diagnostic IDs. The diagnostic ID is a unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.  <br/> |
|**Top diagnostic reasons** <br/> |No  <br/> |Diagnostic ID generated in a session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions where the specified diagnostic ID was generated.  <br/> |
   
## Metrics for Top Modalities

The following table lists the information provided in the Failure Distribution Report based on the session modalities that experienced the most failures.
  
**Metrics for Top Modalities**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking based of failed session based on session type (for example, an audio/video conference or a peer-to-peer file transfer session).  <br/> |
|**Top modalities** <br/> |No  <br/> |Session type.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions involving the specified modality.  <br/> |
   
## Metrics for Top Pools

The following table lists the information provided in the Failure Distribution Report based on the pools that experienced the most failures.
  
**Metrics for Top Pools**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on the Registrar pool or Edge Server where the session was conducted.  <br/> |
|**Top pools** <br/> |No  <br/> |Name of the Registrar pool or Edge Server.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per Registrar pool or Edge Server.  <br/> |
   
## Metrics for Top Sources

The following table lists the information provided in the Failure Distribution Report based on the computers that experienced the most failures.
  
**Metrics for Top Sources**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking failed sessions per computer.  <br/> |
|**Top sources** <br/> |No  <br/> |Name of the computer involved in the failed session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per computer.  <br/> |
   
## Metrics for Top Components

The following table lists the information provided in the Failure Distribution Report based on the components that experienced the most failures.
  
**Metrics for Top Components**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on component (for example, ExumRouting, GroupChat, or MediationServer).  <br/> |
|**Top components** <br/> |No  <br/> |Name of the component involved in the failed session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per component.  <br/> |
   
## Metrics for Top From Users

The following table lists the information provided in the Failure Distribution Report based on users who experienced the most failures when they tried to call someone else (known as "From" users).
  
**Metrics for Top From Users**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on the user who was invited to join the session.  <br/> |
|**Top from users** <br/> |No  <br/> |SIP address of the user invited to join the session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per user.  <br/> |
   
## Metrics for Top To Users

The following table lists the information provided in the Failure Distribution Report based on the users who experienced the most failures when another user tried to call them (known as "To" users).
  
|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on the user who initiated the session.  <br/> |
|**Top to users** <br/> |No  <br/> |SIP address of the user who initiated the session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per user.  <br/> |
   
## Metrics for Top User Agents

The following table lists the information provided in the Failure Distribution Report based on the endpoint software that experienced the most failures.
  
**Metrics for Top User Agents**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |No  <br/> |Relative ranking of failed sessions based on the user agent (software) involved in the session. For example: RTCC/4.0.0.0 Inbound Routing/4.0.0.0.  <br/> |
|**Top user agents** <br/> |No  <br/> |Name of the user agent involved in the failed session.  <br/> |
|**Sessions** <br/> |No  <br/> |Total number of failed sessions per user agent.  <br/> |
   

