---
title: "Peer-to-Peer Session Detail Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6be1d676-68f7-4a53-a72a-de73296c5571
description: "Summary: Learn about the Peer-to-Peer Session Detail Report in Skype for Business Server."
---

# Peer-to-Peer Session Detail Report in Skype for Business Server
 
**Summary:** Learn about the Peer-to-Peer Session Detail Report in Skype for Business Server.
  
The Peer-to-Peer Session Detail Report returns detailed information about a peer-to-peer session. For example, if you select an instant messaging session, the report will tell you the number of messages sent by each of the two users in the session.
  
## Accessing the Peer-to-Peer Session Detail Report

The Peer-to-Peer Session Detail Report can be accessed from any of the following reports (all of which can be accessed from the Monitoring Reports home page):
  
- IP Phone Inventory Report
    
- User Activity Report
    
- Call Admission Control Report
    
- Failure List Report 
    
From within the Peer-to-Peer Session Detail Report you can access the [Diagnostic Report in Skype for Business Server](diagnostic-report.md) by clicking the Diagnostic Report (Details) metric. You can also access the Top Failures Report by clicking either of these two metrics:
  
- Response
    
- Diagnostic ID
    
## Making the Best Use of the Peer-to-Peer session Detail Report

The Peer-to-Peer Session Detail Report includes a large number of metrics, many of which might not be familiar to system administrators. Often-times, however, you can view a tooltip that offers a brief description of that metric simply by holding your mouse over the metric label.
  
Note that the actual metrics shown on a given report will depend on the type of peer-to-peer session you selected. An audio/video session will report a different set of metrics than an instant messaging session.
  
You can also hold your mouse over the Response code and Diagnostic ID metrics in order to obtain a description of those values:
  
## Filters

None. You cannot filter the Peer-to-Peer Session Detail Report.
  
## Session Information Metrics

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each session.
  
**Session Information Metrics**

|**Name**|**Description**|
|:-----|:-----|
|**Pool FQDN** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server involved in the session.  <br/> |
|**Invite time** <br/> |Date and time the session invitation was originally sent.  <br/> |
|**Response time** <br/> |Date and time that the invitation acceptance was received.  <br/> |
|**From user** <br/> |SIP address of the user who initiated the session.  <br/> |
|**From user agent** <br/> |Software used by the endpoint of the user who initiated the session.  <br/> |
|**Is From user internal** <br/> |Indicates whether the user who initiated the session was logged on to the internal network.  <br/> |
|**Is From user integrated with desk phone** <br/> |Indicates whether the endpoint used by the user who initiated the session is integrated with his or her desktop phone.  <br/> |
|**Session Priority** <br/> |Priority assigned to the session. Valid priorities are: Unknown; Non-Urgent; Normal; Urgent; and Emergency.  <br/> |
|**Response code** <br/> |SIP response code sent when the session failed.  <br/> |
|**Front end** <br/> |Name of the Front End Server used in the conference.  <br/> |
|**Capture time** <br/> |Date and time that the session information was recorded.  <br/> |
|**End time** <br/> |Date and time the session ended.  <br/> |
|**To user** <br/> |SIP address of the user who was invited to the session.  <br/> |
|**To user agent** <br/> |Software used by the endpoint of the user who was invited to the session.  <br/> |
|**Is To user internal** <br/> |Indicates whether the user who was invited to the session was logged on to the internal network.  <br/> |
|**Is To user integrated with desk phone** <br/> |Indicates whether the endpoint used by the user who was invited to the session is integrated with his or her desktop phone.  <br/> |
|**Is retried session** <br/> |Indicates whether the session is an attempt to retry a session that previously failed.  <br/> |
|**Diagnostic ID** <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Hold the mouse over the ID number to view additional information about that ID.  <br/> |
   
## Metrics for Modalities

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each session modality.
  
**Metrics for Modalities**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Modalities** <br/> |No  <br/> |Modalities used in the session. For example, instant messaging (IM) or file transfer.  <br/> |
|**From user messages** <br/> |No  <br/> |Number of messages sent by the user who initiated the session.  <br/> |
|**To user messages** <br/> |No  <br/> |Number of messages sent by the user who was invited to join the session.  <br/> |
   
## Metrics for Diagnostic Reports

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each diagnostic report.
  
**Metrics for Diagnostic Reports**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Detail** <br/> |No  <br/> |When you click this item, the report shows the Diagnostic Report for the session.  <br/> |
|**Report time** <br/> |No  <br/> |Date and time the report was recorded.  <br/> |
|**Request** <br/> |No  <br/> |SIP request type. For example, INVITE or BYE.  <br/> |
|**Diagnostic ID** <br/> |No  <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.  <br/> |
|**Content type** <br/> |No  <br/> |Type of media content used in the conference. For example, a common content type is Application/sdp. Session Description Protocol (SDP) is a standard Internet protocol used for session announcements, session invitations, and other forms of multimedia session initiation.  <br/> |
|**Reported by** <br/> |No  <br/> |Computer (that is, client or server) that reported the problem.  <br/> |
   

