---
title: "List of QoE tables in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 176194d7-d184-4e23-94bb-cb62b4db47f5
description: "The database schema consists of the following tables."
---

# List of QoE tables in Lync Server 2013
[]
The database schema consists of the following tables. 
  
 **Supporting Tables**
  
|****Table****|****Description****|
|:-----|:-----|
|[AppSharingMetricsThreshold table in Lync Server 2013](appsharingmetricsthreshold-table.md) <br/> |Stores optimal and acceptable values for the Quality of Experience metrics used with application sharing.  <br/> |
|[CodecDescription table in Lync Server 2013](codecdescription-table.md) <br/> |Maps unique codec identifiers to their corresponding codec.  <br/> |
|[IPAddress table in Lync Server 2013](ipaddress-table.md) <br/> |Maps IP addresses to the unique IP address identifiers used elsewhere in the Quality of Experience database.  <br/> |
|[NetworkConnectionDetail table in Lync Server 2013](networkconnectiondetail-table.md) <br/> |Maps network connection types to the network connection identifiers used elsewhere in the Quality of Experience database.  <br/> |
|[PurgeSettings table (QoE) in Lync Server 2013](purgesettings-table-qoe.md) <br/> |Stores information that specifies if (and when) outdated Quality of Experience records will automatically be deleted from the QoE database.  <br/> |
|[TraceRoute table in Lync Server 2013](traceroute-table.md) <br/> |Stores routing information for calls.  <br/> |
|[UserAgentDef table (QoE) in Lync Server 2013](useragentdef-table-qoe.md) <br/> |Maps user agent identifiers to the agent's descriptive names.  <br/> |
|[VideoMetricsThreshold table in Lync Server 2013](videometricsthreshold-table.md) <br/> |Stores optimal and acceptable values for the Quality of Experience metrics used with video calls.  <br/> |
|[UserAgent table in Lync Server 2013](useragent-table.md) <br/> |Stores Session Initiation Protocol (SIP) User Agent (UA) strings and UA types used in audio and video sessions.  <br/> |
|[User table in Lync Server 2013](user-table.md) <br/> |Stores user, conference, and phone URIs used in audio and video sessions.  <br/> |
|[Endpoint table in Lync Server 2013](endpoint-table.md) <br/> |Stores FQDN computer names of endpoints participating in audio and video sessions.  <br/> |
|[Pool table in Lync Server 2013](pool-table.md) <br/> |Stores the names of pools to which metrics data belongs.  <br/> |
|[Device table in Lync Server 2013](device-table.md) <br/> |Stores capture devices and render devices which are used in an audio/video calls.  <br/> |
|[DeviceDriver table in Lync Server 2013](devicedriver-table.md) <br/> |Stores driver for the capture device and the render device which are used in audio/video calls.  <br/> |
|[Conference table in Lync Server 2013](conference-table.md) <br/> |Stores Conference URIs for conference scenarios or DialogID for other scenarios.  <br/> |
|[SessionCorrelation table in Lync Server 2013](sessioncorrelation-table.md) <br/> |Stores CorrelationID for PSTN calls.  <br/> |
|[PayloadDescription table in Lync Server 2013](payloaddescription-table.md) <br/> |Stores the Codec used in audio/video calls.  <br/> |
|[AppliedBandwidthSource table in Lync Server 2013](appliedbandwidthsource-table.md) <br/> |Stores the bandwidth source used in audio/video calls.  <br/> |
|[MacAddress table in Lync Server 2013](macaddress-table.md) <br/> |Stores the MAC address of the endpoints participating in audio and video sessions.  <br/> |
|[Dialog table in Lync Server 2013](dialog-table.md) <br/> |Stores the Dialog ID of audio and video sessions.  <br/> |
|[Region table in Lync Server 2013](region-table.md) <br/> |Stores the network region defined in NCS setting.  <br/> |
|[UserSite table in Lync Server 2013](usersite-table.md) <br/> |Stores the network site defined in NCS setting.  <br/> |
|[Subnet table in Lync Server 2013](subnet-table.md) <br/> |Stores the subnet defined in NCS setting.  <br/> |
|[MonitoredRegionLink table in Lync Server 2013](monitoredregionlink-table.md) <br/> |Stores the region link defined in NCS setting.  <br/> |
|[MonitoredUserSiteLink table](monitoredusersitelink-table.md) <br/> |Stores the network site links defined in NCS setting.  <br/> |
|[EndpointSubnet table in Lync Server 2013](endpointsubnet-table.md) <br/> |Stores the subnet of the endpoint participating in an audio and video session.  <br/> |
|[Server table in Lync Server 2013](server-table.md) <br/> |Stores the FQDN or IP address of the server the media goes through.  <br/> |
   
 **Tables for metrics data**
  
|****Table****|****Description****|
|:-----|:-----|
|[AppSharingStream table in Lync Server 2013](appsharingstream-table.md) <br/> |Stores Quality of Experience metrics for the network streams used for application sharing. Quality of Experience metrics for the network streams used for application sharing.  <br/> |
|[Session table in Lync Server 2013](session-table.md) <br/> |Stores overall information about an audio or audio/video session. A session is defined as an audio or video SIP dialog between two endpoints.  <br/> |
|[MediaLine table in Lync Server 2013](medialine-table.md) <br/> |Stores information about each media line in a session. A media line is a collection of one or more audio and video streams. Typically, a single media line will have two streams, either audio or video.  <br/> |
|[AudioStream table in Lync Server 2013](audiostream-table.md) <br/> |Stores audio media quality metrics for each audio stream in the media line.  <br/> |
|[AudioSignal table in Lync Server 2013](audiosignal-table.md) <br/> |Stores audio media quality metrics in the media line. This includes acoustic echo cancellation (AEC) and automatic gain control (AGC) metrics.  <br/> |
|[VideoStream table in Lync Server 2013](videostream-table.md) <br/> |Stores video media quality metrics for each audio stream in the media line.  <br/> |
|[AudioClientEvent table in Lync Server 2013](audioclientevent-table.md) <br/> |Stores audio media quality metrics collected from the client event.  <br/> |
|[VideoClientEvent table in Lync Server 2013](videoclientevent-table.md) <br/> |Stores video media quality metrics collected from the client event.  <br/> |
|**DiagnosticData Table** <br/> |Stores diagnostic data which is for internal use only.  <br/> |
   
 **Tables for summary data**
  
|****Table****|****Description****|
|:-----|:-----|
|**ServerSummary Table** <br/> |Stores summary data for the servers, these data is used for Quality of Experience (QoE) reporting only.  <br/> |
|**UserSummary Table** <br/> |Stores summary data for users, these data is used for QoE reporting only.  <br/> |
|**CallTypeSummary Table** <br/> |Store summary data for call types, these data is used for QoE reporting only.  <br/> |
   
 **Tables for Internal Use by Monitoring Server**
  
|****Table****|****Description****|
|:-----|:-----|
|**DbConfigDateTime** <br/> |For internal use only.  <br/> |
|**DbConfigInt** <br/> |For internal use only.  <br/> |
|**FrontEnd Table** <br/> |For internal use only.  <br/> |
|**Task Table** <br/> |For internal use only.  <br/> |
|**SummaryTableConfiguration** <br/> |For internal use only.  <br/> |
|**DbErrorMessage** <br/> |For internal use only.  <br/> |
|**MetricsThreshold** <br/> |For internal use only.  <br/> |
|**DaylightSavingYears** <br/> |For internal use only.  <br/> |
|**TimeZoneConfiguration** <br/> |For internal use only.  <br/> |
|**TimeZones** <br/> |For internal use only.  <br/> |
|**CallSummary Table** <br/> |For internal use only.  <br/> |
|**DeviceCallSumary Table** <br/> |For internal use only.  <br/> |
|**Tenant Table** <br/> |For internal use only.  <br/> |
|**VideoCallSummaryTable** <br/> |For internal use only.  <br/> |
|**ASCallSummaryTable** <br/> |For internal use only.  <br/> |
   

