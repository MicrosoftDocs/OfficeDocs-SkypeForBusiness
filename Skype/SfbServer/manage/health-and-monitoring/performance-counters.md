---
title: "Mobility performance counters in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d18ed85a-673d-4695-aa3f-ac83a38ab90a
description: "Summary: Learn about the performance counters that you can use to monitor servers running the Unified Communications Web API (UCWA) and the Skype for Business Server Mcx Mobility Service."
---

# Mobility performance counters in Skype for Business Server
 
**Summary:** Learn about the performance counters that you can use to monitor servers running the Unified Communications Web API (UCWA) and the Skype for Business Server Mcx Mobility Service.
  
The following tables list the names and descriptions of performance counters that you can use to monitor servers running the Unified Communications Web API (UCWA) and the Skype for Business Server Mcx Mobility Service. 
  
The category name for the counters in the UCWA table is **LS:WEB - UCWA**.
  
The category name for the counters in the Mcx Mobility Service table is **LS:WEB - Mobile Communication Service**.

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
## Performance Counters for UCWA

|Counter|Description|
|:-----|:-----|
|Active Application Count  <br/> |The current number of applications  <br/> |
|Active Application Sharing Modality Count  <br/> |The current number of Application Sharing modality  <br/> |
|Active Audio Modality Count  <br/> |The current number of Audio modality  <br/> |
|Active Data Collaboration Modality Count  <br/> |The current number of Data Collaboration modality  <br/> |
|Active Directory Photo Get Latency (ms)  <br/> |This counter shows the average time (in milliseconds) to retrieve a photo from active directory  <br/> |
|Active Messaging Modality Count  <br/> |The current number of Messaging modality  <br/> |
|Active Panoramic Video Modality Count  <br/> |The current number of Panoramic Video modality  <br/> |
|Active Pending Get Count  <br/> |The number of currently active pending gets; long-held connections to the server  <br/> |
|Active Session Count  <br/> |The current number of endpoints registered in UCWA per application and total  <br/> |
|Active User Instance Count  <br/> |The current number of user instances  <br/> |
|Active User Instances without Application  <br/> |The current number of user instances without application  <br/> |
|Active Video Modality Count  <br/> |The current number of Video modality  <br/> |
|Application Creation Requests Received/Second  <br/> |The per second rate of received application creation requests  <br/> |
|AS MCU Join Failures  <br/> |The number of AS MCU Join Failures  <br/> |
|AV MCU Join Failures  <br/> |The number of AV MCU Join Failures  <br/> |
|Average Application Startup Time (ms)  <br/> |The average application startup time in Milliseconds  <br/> |
|Average Lifetime for Session (ms)  <br/> |The average lifetime for a session in milliseconds  <br/> |
|Data MCU Join Failures  <br/> |The number of Data MCU Join Failures  <br/> |
|Exchange Contact Search Latency (ms)  <br/> |This counter shows the average time (in milliseconds) to search contact in Exchange  <br/> |
|Exchange HD Photo Get Latency (ms)  <br/> |This counter shows the average time (in milliseconds) to retrieve a photo from Exchange  <br/> |
|HTTP 4xx Responses/Second  <br/> |The per second rate of responses with HTTP 4xx code  <br/> |
|HTTP 5xx Responses/Second  <br/> |The per second rate of responses with HTTP 5xx code  <br/> |
|IM MCU Join Failures  <br/> |The number of IM MCU Join Failures  <br/> |
|Number of Active Directory Photo Get Failures  <br/> |The total number of failures to retrieve photos from Active Directory  <br/> |
|Number of Contact Search failures  <br/> |The total number of failures to search contacts in Exchange  <br/> |
|Number of Deserialization Failures  <br/> |The total number of deserialization failures  <br/> |
|Number of HD Photo Get Failures  <br/> |The total number of failures to retrieve HD photos from Exchange  <br/> |
|Over The Maximum Subscriptions Per Application  <br/> |The number of Subscription requests over the maximum allowed per application  <br/> |
|Over The Maximum Subscriptions Per Batch  <br/> |The number of Subscription requests over the maximum allowed per batch  <br/> |
|Presence Subscription Failures  <br/> |The number of failures to subscribe presence  <br/> |
|Registering Endpoint Failures  <br/> |The number of failures to register endpoints  <br/> |
|Requests Received/Second  <br/> |The per second rate of received requests  <br/> |
|Requests Succeeded/Second  <br/> |The per second rate of successful requests (HTTP 2xx/3xx response codes)  <br/> |
|Succeeded Create Application Requests/Second  <br/> |The per second rate of successful application creation requests  <br/> |
|Timed Out Pending Get Count  <br/> |The number of pending gets that timed out  <br/> |
|Total Application Creation Requests Received  <br/> |The total number of application creation requests received since the service was started  <br/> |
|Total HTTP 4xx Responses  <br/> |The total number of HTTP 4xx responses  <br/> |
|Total HTTP 5xx Responses  <br/> |The total number of HTTP 5xx responses  <br/> |
|Total Requests Received on the Command Channel  <br/> |The total number of requests received on the command channel  <br/> |
|Total Requests Succeeded  <br/> |The total number of requests that succeeded  <br/> |
|Total Sessions Initiated  <br/> |The total number of sessions that were initiated since the service was started  <br/> |
|Total Sessions Terminated Because of Idle Timeout  <br/> |The total number of sessions that were terminated because of user idle timeout  <br/> |
|Total Throttled Applications  <br/> |The number of throttled applications  <br/> |
   
**Performance Counters for Mcx Mobility Service**

|**Counter**|**Description**|
|:-----|:-----|
|Average Lifetime for a Session in Milliseconds  <br/> |The average lifetime for a session in milliseconds  <br/> |
|Current Push Notification Subscriptions  <br/> |The current number of push notification subscriptions. This number, in conjunction with Currently Active Session Count, represents the subset of currently active sessions that are registered for Windows Mobile or iPhone devices.  <br/> |
|Currently Active Network Timeout Poll Count  <br/> |The number of network polls that timed out  <br/> |
|Currently Active Poll Count  <br/> |The number of currently active polls (long-held connections to the server)  <br/> |
|Currently Active Session Count  <br/> |Current number of endpoints registered in the Mobility Service  <br/> |
|Currently Active Session Count with Active Presence Subscriptions  <br/> |The number of currently active sessions with active presence subscriptions  <br/> |
|Push Notification Requests Failed/Second  <br/> |The per second rate of failed push notifications  <br/> |
|Push Notification Requests Succeeded/Second  <br/> |The per second rate of successful push notifications  <br/> |
|Push Notification Requests Throttled/Second  <br/> |The per second rate of throttled push notifications  <br/> |
|Push Notification Requests/Second  <br/> |The per second rate of sent push notifications  <br/> |
|Requests Failed/Second  <br/> |The per second rate of failed requests  <br/> |
|Requests Received/Second  <br/> |The per second rate of received requests  <br/> |
|Requests Rejected/Second  <br/> |The per second rate of rejected requests  <br/> |
|Requests Succeeded/Second  <br/> |The per second rate of successful requests  <br/> |
|Succeeded Initiate Session Requests/Second  <br/> |The per second rate of successful Get Location requests. Requests to initiate a session consume the most CPU on the server. Peak supported load is 12/second. Sustainability depends on other loads on the server. Initiate a session typically means a sign-in for a user that has been signed out for an extended period of time.  <br/> |
|Total Declined Inbound Voice Calls  <br/> |The total number of inbound voice calls that were declined  <br/> |
|Total Failed Inbound Voice Calls  <br/> |The total number of inbound voice calls that failed  <br/> |
|Total Failed Outbound Voice Calls  <br/> |The total number of outbound voice calls that failed  <br/> |
|Total number of sessions terminated by user  <br/> |The total number of sessions terminated by users  <br/> |
|Total Push Notification Requests  <br/> |The total number of push notification requests  <br/> |
|Total Push Notification Requests Failed  <br/> |The total number of push notification requests that failed  <br/> |
|Total Push Notification Requests Succeeded  <br/> |The total number of push notification requests that were successful  <br/> |
|Total Push Notification Requests Throttled  <br/> |The total number of push notification requests that were throttled  <br/> |
|Total Requests Failed  <br/> |The total number of requests that failed  <br/> |
|Total Requests received on the Command Channel  <br/> |The total number of requests received on the command channel  <br/> |
|Total Requests Rejected  <br/> |The total number of requests that were rejected  <br/> |
|Total Requests Succeeded  <br/> |The total number of requests made to the Mobility Service that succeeded  <br/> |
|Total Session Initiated Count  <br/> |The total number of sessions that were initiated since the Mobility Service was started  <br/> |
|Total Sessions Terminated Because of User Idle Timeout  <br/> |The total number of sessions that were terminated because of user idle timeout  <br/> |
|Total Successful Inbound Voice Calls  <br/> |The total number of inbound voice calls that were successful  <br/> |
|Total Successful Outbound Voice Calls  <br/> |The total number of outbound voice calls that were successful  <br/> |
   
> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
