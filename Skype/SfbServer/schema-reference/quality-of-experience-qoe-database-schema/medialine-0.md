---
title: "MediaLine table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 414b1d63-ae97-4c27-bac0-c9ad0f808ff0
description: "Each record represents one media line. (One audio session usually contains one audio media line. One audio and video (A/V) session usually contains one audio media line and one video media line, although the session might contain two video media lines if a conferencing device is used or if Gallery View is used."
---

# MediaLine table
 
Each record represents one media line. (One audio session usually contains one audio media line. One audio and video (A/V) session usually contains one audio media line and one video media line, although the session might contain two video media lines if a conferencing device is used or if Gallery View is used.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [Session table](session.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |Referenced from the [Session table](session.md).  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary  <br/> |0 is main audio, 1 is main video, and 2 is panoramic video, 3 is Application/Desktop Sharing, 16 is Video based Screen Sharing (VbSS). This label must be unique within a single session.  <br/> |
|**ConnectivityIce** <br/> |tinyint  <br/> | <br/> |This column is present but not used in Microsoft Lync Server 2013. Information about the connectivity used for a media line is captured in the CallerConnectivityICE and CalleeConnectivityICE columns.  <br/> |
|**CallerIceWarningFlags** <br/> |int  <br/> | <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags. For details, refer to the  *Quality of Experience Monitoring Server Protocol Specification*  , available for download. <br/> |
|**CalleeIceWarningFlags** <br/> |int  <br/> | <br/> |Same as CallerIceWarningFlags, but on the callee side. For details, refer to the  *Quality of Experience Monitoring Server Protocol Specification*  , available for download. <br/> |
|**Security** <br/> |tinyint  <br/> | <br/> |The security profile in use. 0 is NONE, 1 is SRTP, 2 is V1.  <br/> |
|**Transport** <br/> |tinyint  <br/> | <br/> |0 is UDP, 1 is TCP.  <br/> |
|**CallerIPAddr** <br/> |int  <br/> |Foreign  <br/> |IP Address of the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CallerPort** <br/> |int  <br/> | <br/> | Port used by the caller. <br/> |
|**CallerSubnet** <br/> |int  <br/> | Foreign <br/> |The subnet of the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CallerInside** <br/> |bit  <br/> | <br/> |1 means caller is inside the enterprise network, 0 means the caller is outside the network.  <br/> |
|**CallerMacAddress** <br/> |int  <br/> |Foreign  <br/> |Caller's mac address, referenced from [MacAddress table](macaddress.md).  <br/> |
|**CallerRelayIPAddr** <br/> |int  <br/> |Foreign  <br/> |IP Address of the A/V Edge service used by the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CallerRelayPort** <br/> |int  <br/> | <br/> |Port used on the A/V Edge service by the caller.  <br/> |
|**CallerCaptureDev** <br/> |int  <br/> |Foreign  <br/> |Capture device used by the caller. Referenced from the [Device table](device.md).  <br/> |
|**CallerRenderDev** <br/> |int  <br/> |Foreign  <br/> |Render device used by caller. Referenced from the [Device table](device.md).  <br/> |
|**CallerCaptureDevDriver** <br/> |int  <br/> |Foreign  <br/> |Driver for the caller's capture device, referenced from the [DeviceDriver table](devicedriver.md).  <br/> |
|**CallerRenderDevDriver** <br/> |int  <br/> |Foreign  <br/> |Driver for the caller's render device, referenced from the [DeviceDriver table](devicedriver.md).  <br/> |
|**CallerNetworkConnectionType** <br/> |tinyint  <br/> |Foreign  <br/> |Indicates how the caller connected to the network. Values are obtained from the [NetworkConnectionDetail table](networkconnectiondetail.md). Typical values are 0 for a wired connection' 1 for a WiFi connection; and 3 for an Ethernet connection.  <br/> |
|**CallerBssid** <br/> |int  <br/> |Foreign  <br/> |Caller's BSSID if wireless is used. Referenced from [MacAddress table](macaddress.md).  <br/> |
|**CallerVPN** <br/> |bit  <br/> ||The caller's link. 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|**CallerLinkSpeed** <br/> |decimal(18,0)  <br/> ||The network link speed, in bps, for the caller's endpoint.  <br/> |
|**CalleeIPAddr** <br/> |int  <br/> |Foreign  <br/> |IP Address of the call receiver. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CalleePort** <br/> |bit  <br/> ||Port used by the call receiver.  <br/> |
|**CalleeSubnet** <br/> |int  <br/> |Foreign  <br/> |Subnet of callee. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CalleeInside** <br/> |bit  <br/> | <br/> |1 means call receiver is inside the enterprise network, 0 means the call receiver is outside the network.  <br/> |
|**CalleeMacAddress** <br/> |int  <br/> |Foreign  <br/> |Callee Mac address. Referenced from the [MacAddress table](macaddress.md).  <br/> |
|**CalleeRelayIPAddr** <br/> |int  <br/> |Foreign  <br/> |IP Address of the A/V Edge service used by the call receiver. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|**CalleeRelayPort** <br/> |int  <br/> | <br/> |Port used on the A/V Edge Service by the call receiver.  <br/> |
|**CalleeCaptureDev** <br/> |int  <br/> |foreign  <br/> |Capture device used by the call receiver. Referenced from the [Device table](device.md).  <br/> |
|**CalleeRenderDev** <br/> |int  <br/> |Foreign  <br/> |Render device used by the call receiver. Referenced from the [Device table](device.md).  <br/> |
|**CalleeCaptureDevDriver** <br/> |int  <br/> |Foreign  <br/> |Driver for the call receiver's capture device. Referenced from [DeviceDriver table](devicedriver.md).  <br/> |
|**CalleeRenderDevDriver** <br/> |varchar(256)  <br/> |Foreign  <br/> |Driver for the call receiver's render device. Referenced from [DeviceDriver table](devicedriver.md).  <br/> |
|**CalleeNetworkConnectionType** <br/> |tinyint  <br/> |Foreign  <br/> |Indicates how the callee connected to the network. Values are obtained from the [NetworkConnectionDetail table](networkconnectiondetail.md). Typical values are 0 for a wired connection' 1 for a WiFi connection; and 3 for an Ethernet connection.  <br/> |
|**CalleeBssid** <br/> |int  <br/> |Foreign  <br/> |Callee's BSSID if wireless is used. Referenced from [MacAddress table](macaddress.md).  <br/> |
|**CalleeVPN** <br/> |bit  <br/> | <br/> |The call receiver's link; 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|**CalleeLinkSpeed** <br/> |decimal(18,0)  <br/> | <br/> |The network link speed, in bps, for the call receiver's endpoint.  <br/> |
|**ConversationalMOS** <br/> |decimal(3,2)  <br/> | <br/> |Narrowband Conversational MOS of the audio sessions (based on both audio streams).  <br/> |
|**AppliedBandwidthLimit** <br/> |int  <br/> ||This is the actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, and so on). This is not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate.  <br/> |
|**AppliedBandwidthSourceKey** <br/> |smallint  <br/> ||This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from ("Policy Server", "TURN Server", "Modality", and so on). Referenced from the [AppliedBandwidthSource table](appliedbandwidthsource.md).  <br/> |
|**Caller** <br/> |bit  <br/> | <br/> |Indicates whether metrics from the caller were received; 1 is yes, a null value is no.  <br/> |
|**Callee** <br/> |bit  <br/> | <br/> |Indicates whether metrics from the call receiver were received; 1 is yes, a null value is no.  <br/> |
|**MidCallReport** <br/> |bit  <br/> ||Indicates whether the report is for a portion of the session or for the complete session.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**ClassifiedPoorCall** <br/> |bit  <br/> ||Indicates whether a call was classified as a poor call (value of 1) or as a good call (0).  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CallerConnectivityICE** <br/> |tinyInt  <br/> ||Indicates whether the caller connected to the network using the ICE protocol (Internet Connectivity Establishment).  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CalleeConnectivityICE** <br/> |tinyint  <br/> ||Indicates whether the caller connected to the network using the ICE protocol (Internet Connectivity Establishment).  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CallerReflexiveLocalIPAddr** <br/> |int  <br/> |Foreign  <br/> |Reflexive IP address of the user who placed the call. In organizations that use NAT (network address translation), the reflexive IP address is the IP address of the proxy server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CallerWiFiDriverDevicesDesc** <br/> |int  <br/> |Foreign  <br/> |Device description for the WiFi driver employed by the user who placed the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CallerWiFiDriverVersion** <br/> |int  <br/> |Foreign  <br/> |Version number for the WiFi driver employed by the user who placed the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CalleReflexiveLocalIPAddr** <br/> |int  <br/> |Foreign  <br/> |Reflexive IP address of the user who received the call. In organizations that use NAT (network address translation), the reflexive IP address is the IP address of the proxy server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CalleeWiFiDriverDevicesDesc** <br/> |int  <br/> |Foreign  <br/> |Device description for the WiFi driver employed by the user who received the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**CalleeWiFiDriverVersion** <br/> |int  <br/> |Foreign  <br/> |Version number for the WiFi driver employed by the user who received the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
   

