---
title: "MediaLine view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 132eca13-8913-4218-9eff-4960ced8c3dc
description: "The MediaLine View stores information about each media line in the database. One audio session typically contains one audio media line. One audio and video (A/V) session typically contains one audio media line and one video media line; however, the session might contain two video media lines if a conferencing device is used or if Gallery View is used. This view was introduced in Microsoft Lync Server 2013."
---

# MediaLine view
 
The MediaLine View stores information about each media line in the database. One audio session typically contains one audio media line. One audio and video (A/V) session typically contains one audio media line and one video media line; however, the session might contain two video media lines if a conferencing device is used or if Gallery View is used. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**details**|
|:-----|:-----|:-----|
|ConferenceDateTime  <br/> |datetime  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|SessionSeq  <br/> |int  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|MediaLineLabel  <br/> |tinyint  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|CallerIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the caller. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|CalleeIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the callee. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|Security  <br/> |tinyint  <br/> |Security profile in use. 0 is NONE, 1 is SRTP, 2 is V1.  <br/> |
|Transport  <br/> |tinyint  <br/> |Transport type. 0 is UDP, 1 is TCP.  <br/> |
|CallerIPAddr  <br/> |var(50)  <br/> |IP address of the caller. This can be either an IPv4 or IPv6 address.  <br/> |
|CallerPort  <br/> |int  <br/> |Port used by the caller.  <br/> |
|CallerInside  <br/> |bit  <br/> |Indicates whether or not the caller is inside the organization network. 1 means that the caller is inside the enterprise network. 0 means that the caller is outside the network.  <br/> |
|CallerMacAddress  <br/> |varchar(256)  <br/> |MAC address of network interface used by caller.  <br/> |
|CallerRelayIPAddr  <br/> |var(50)  <br/> |IP Address of the A/V Edge service used by the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CalleeRelayPort  <br/> |int  <br/> |Port used on the A/V Edge service used by the caller.  <br/> |
|CallerReflexiveIPAddr  <br/> |var(50)  <br/> |Caller's IP address as reported by the A/V Edge service. This address may be different that the CallerIPAddr if the client is located behind a NAT for example.  <br/> |
|CallerCaptureDev  <br/> |varchar(256)  <br/> |Caller's capture device name.  <br/> |
|CallerRenderDev  <br/> |varchar(256)  <br/> |Caller's render device name.  <br/> |
|CallerCaptureDevDriver  <br/> |varchar(256)  <br/> |Caller's capture device driver name.  <br/> |
|CallerRenderDevDriver  <br/> |varchar(256)  <br/> |Caller's render device driver name.  <br/> |
|CallerWifiDriverDeviceDesc  <br/> |varchar(256  <br/> |Caller's Wifi driver description.  <br/> |
|CallerWifiDriverVersion  <br/> |varchar(256)  <br/> |Caller's Wifi driver version.  <br/> |
|CalleeNetworkConnectionDetail  <br/> |varchar(256)  <br/> |Details of caller's network connection. See the [NetworkConnectionDetail table](networkconnectiondetail.md) for more information. <br/> |
|CallerBssid  <br/> |varchar(256)  <br/> |Basic Service Set Identifier used by callers WiFi connection.  <br/> |
|CallerVPN  <br/> |bit  <br/> |Indicates whether the caller connected over a virtual private network. 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|CalleeIPAddr  <br/> |var(50)  <br/> |IP address of the callee. This can be either an IPv4 or IPv6 address.  <br/> |
|CalleePort  <br/> |int  <br/> |Port used by the callee.  <br/> |
|CalleeInside  <br/> |bit  <br/> |Indicates whether the callee is inside the enterprise network. 1 means callee is inside the enterprise network, 0 means the callee is outside the network.  <br/> |
|CalleeMacAddress  <br/> |varchar(256)  <br/> |MAC address of network interface used by callee.  <br/> |
|CalleeRelayIPAddr  <br/> |var(50)  <br/> |IP Address of the A/V Edge service used by the callee. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CalleeRelayPort  <br/> |int  <br/> |Port used on the A/V Edge service used by the callee.  <br/> |
|CalleeReflexiveIPAddr  <br/> |var(50)  <br/> |Callee's IP address as reported by the A/V Edge service. This address may be different that the CalleeIPAddr if the client is located behind a NAT for example.  <br/> |
|CalleeCaptureDev  <br/> |var(50)  <br/> |Callee's capture device name.  <br/> |
|CalleeRenderDev  <br/> |varchar(256)  <br/> |Callee's render device name.  <br/> |
|CalleeCaptureDevDriver  <br/> |varchar(256)  <br/> |Callee's capture device driver name.  <br/> |
|CalleeRenderDevDriver  <br/> |varchar(256)  <br/> |Callee's render device driver name.  <br/> |
|CalleeWifiDriverDeviceDesc  <br/> |varchar(256)  <br/> |Callee's Wifi driver description.  <br/> |
|CalleeWifiDriverVersion  <br/> |varchar(256  <br/> |Callee's Wifi driver version.  <br/> |
|CalleeNetworkConnectionDetail  <br/> |varchar(256)  <br/> |Details of callee's network connection. See the [NetworkConnectionDetail table](networkconnectiondetail.md) for more information. <br/> |
|CalleeBssid  <br/> |varchar(256)  <br/> |Basic Service Set Identifier used by callee's WiFi connection.  <br/> |
|CalleeVPN  <br/> |bit  <br/> |Indicates whether the callee connected over a virtual private network. 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|ConversationalMOS  <br/> |decimal(3,2)  <br/> |Narrowband Conversational MOS of the audio sessions (based on both audio streams).  <br/> |
|AppliedBandwidthLimit  <br/> |int  <br/> |This is the actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, etc.). This should not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate.  <br/> |
|AppliedBandwidthSource  <br/> |varchar(256)  <br/> |Source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (for example, "Policy Server", "TURN Server", or "Modality").  <br/> |
|Caller  <br/> |bit  <br/> |Indicates whether metrics from the caller were received; 1 is yes, 0 is no.  <br/> |
|Callee  <br/> |bit  <br/> |Indicates whether metrics from the call receiver were received; 1 is yes, 0 is no.  <br/> |
|MidCallReport  <br/> |bit  <br/> |Indicates whether the report is for a portion of the call or for the complete call.  <br/> |
|ClassifiedPoorCall  <br/> |bit  <br/> |Indicates whether a call was classified as a poor call (1) or as a good call (0).  <br/> |
|CallerConnectivityICE  <br/> |tinyint  <br/> |Indicates whether the caller connected to the network using the ICE protocol (Internet Connectivity Establishment).  <br/> |
|CalleeConnectivityICE  <br/> |tinyint  <br/> |Indicates whether the user called connected to the network using the ICE protocol (Internet Connectivity Establishment).  <br/> |
   

