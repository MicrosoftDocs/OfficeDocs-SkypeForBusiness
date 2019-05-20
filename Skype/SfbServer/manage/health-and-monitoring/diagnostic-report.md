---
title: "Diagnostic Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b389dbd9-f2e8-4184-93d0-2e504796ac16
description: "Summary: Learn about the Diagnostic Report in Skype for Business Server."
---

# Diagnostic Report in Skype for Business Server
 
**Summary:** Learn about the Diagnostic Report in Skype for Business Server.
  
The Diagnostic Report provides diagnostic and troubleshooting information for a failed session. This information includes both the Diagnostic ID and the Diagnostic header that were reported when the session failed. The Diagnostic ID is a unique identifier (in the form of an ms-diagnostics header) that gets attached to a SIP message, while the Diagnostic header provides an accompanying description for the Diagnostic ID. The report might also contain valuable troubleshooting details that are known by the reporting component. For example:
  
- The cause code provided by the PSTN gateway that generated the failure. When an outgoing call fails on the PSTN network, an ISDN User Part (ISUP) cause code is automatically generated. For example, a PSTN gateway might send cause code 34 to indicate that no circuit or channel was available for completing the call.
    
- Peer FQDN, port, and Winsock errors for connectivity failures.
    
- Names being looked up for DNS resolution failures. DNS resolution takes place any time a client contacts a name server and requests the IP address that corresponds to specified device name.
    
## Accessing the Diagnostic Report

The Diagnostic Report can be accessed by clicking the Diagnostic Report (Detail) metric on either the [Peer-to-Peer Session Detail Report in Skype for Business Server](peer-to-peer-session-detail-report.md) or the Conference Detail Report.
  
## Filters

None. You cannot filter the Diagnostic Report.
  
## Metrics

The following table lists the information provided in the Diagnostic Report for each session.
  
**Diagnostic Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Report time** <br/> |No  <br/> |Date and time that the report was recorded.  <br/> |
|**Response code** <br/> |No  <br/> |SIP response code sent when the session failed.  <br/> |
|**Request type** <br/> |No  <br/> |SIP request type that failed. For example, INVITE, BYE, or SERVICE.  <br/> |
|**Source** <br/> |No  <br/> |Source of the error.  <br/> |
|**From user URI** <br/> |No  <br/> |SIP address of the user who initiated the session.  <br/> |
|**From user agent** <br/> |No  <br/> |Software used by the endpoint of the user who initiated the session.  <br/> |
|**Diagnostic ID** <br/> |No  <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.  <br/> |
|**Content type** <br/> |No  <br/> |Type of media content that failed. For example, a common content type is Application/sdp. Session Description Protocol (SDP) is a standard Internet protocol used for session announcements, session invitations, and other forms of multimedia session initiation.  <br/> |
|**Application** <br/> |No  <br/> |Application involved in the error.  <br/> |
|**To user URI** <br/> |No  <br/> |SIP address of the user who was invited to the session.  <br/> |
|**Conference join times (ms)** <br/> |No  <br/> |Amount of time (in milliseconds) it took for the user to join the conference.  <br/> |
|**Diagnostic header** <br/> |No  <br/> |Diagnostic ID description.  <br/> |
   
A list of diagnostic errors can be found on the [Ms-Diagnostics Header page](https://msdn.microsoft.com/en-us/library/gg132446%28v=office.12%29.aspx).
  

