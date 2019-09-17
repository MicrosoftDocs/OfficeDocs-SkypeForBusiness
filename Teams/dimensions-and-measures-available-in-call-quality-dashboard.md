---
title: "Dimensions and measurements available in Call Quality Dashboard"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: siunies, williamlooney, gageames
ms.topic: conceptual
ms.assetid: e97aeeee-9e43-416f-b433-9cdd63d8874b
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
audience: Admin
appliesto:
- Skype for Business
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom: Reporting
description: "Get detailed information about the dimensions and measurements used by the Call Quality Dashboard for Microsoft Teams and Skype for Business Online."
---

# Dimensions and measurements available in Call Quality Dashboard

The Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business Online allows you to better understand call quality of calls made using these services. This topic provides detailed information about the dimensions and measurements visible through CQD. To learn more about CQD and how to enable it, see [Turning on and using Call Quality Dashboard for Microsoft Teams and Skype for Business Online](turning-on-and-using-call-quality-dashboard.md).

## First and Second endpoint classification

Many of the dimensions and measurements in CQD are labeled as first or second. The following logic determines which endpoint involved in the stream or call is labeled as first:

- A Server endpoint (AV MCU, Mediation Server, and so on) is considered First if a Server is involved in the stream or call.
- A Client endpoint is considered Second unless the stream is between two Server endpoints.
- If both endpoints are the same type, the order for which is first vs. second is based on internal ordering of the user agent category. This ensures that the ordering is consistent.

For example, here each row represents a pair of User Agents involved in a stream:

|User Agent Category of Caller |User Agent Category of Callee |First Endpoint |Second Endpoint|First Is Caller
|:--- |:--- |:--- |:--- |:--- |
|AV-MCU |OC (Skype for Business client) |AV-MCU |OC (Skype for Business client) |TRUE |
|OC (Skype for Business client) |AV-MCU |AV-MCU |OC (Skype for Business client) |FALSE |
|OC (Skype for Business client) |OC (Skype for Business client) |OC (Skype for Business client) |OC (Skype for Business client) |FALSE |
|AV-MCU |Mediation Server |Mediation Server |AV-MCU ||
|Mediation Server |AV-MCU |Mediation Server |AV-MCU |TRUE |
|OC (Skype for Business client) |OC Phone (Skype for Business IP Phone) |OC (Skype for Business client) |OC Phone (Skype for Business IP Phone) |TRUE |
|OC Phone (Skype for Business IP Phone) |OC (Skype for Business client) |OC (Skype for Business client) |OC Phone (Skype for Business IP Phone) |FALSE |

> [!NOTE]
> That First and Second classification is separate from which endpoint is the caller or callee. The First Is Caller dimension can be used to help identify which endpoint was the caller or callee.

## Dimensions

Information in the dimensions is based in part on data uploaded to the CQD portal at the time of the call. Many Dimension values can also be used as filters. The following table lists the dimensions currently available in CQD, in the order listed in the query editor used to create new reports:

| Name | Data type  | Description | Possible Reasons for blank values |
|:---  |:---        |:---         |:--- |
|**Endpoint**|||
| First CPU Name  | String  | Name of the CPU used by the first endpoint. <br/> **Example value:** Contoso CPU X11 @ 1.80GHz | <br/>&bull; This data was not reported by the endpoint   |
| Second CPU Name  | String  | Name of the CPU used by the second endpoint. <br/> **Example value:** Contoso CPU X11 @ 1.80GHz | <br/>&bull; This data was not reported by the endpoint     |
| First CPU Number Of Cores  | Number of cores  | Number of CPU cores available on the first endpoint. <br/> **Example value:** 8  | <br/>&bull; This data was not reported by the endpoint    |
| Second CPU Number Of Cores  | Number of cores  | Number of CPU cores available on the second endpoint. <br/> **Example value:** 8  | <br/>&bull; This data was not reported by the endpoint     |
| First CPU Processor Speed  | CPU speed in MHz  | Speed in MHz of the CPU used by the first endpoint. <br/> **Example value:** 1800  | <br/>&bull; This data was not reported by the endpoint   |
| Second CPU Processor Speed  | CPU speed in MHz  | Speed in MHz of the CPU used by the second endpoint. <br/> **Example value:** 1800 | <br/>&bull; This data was not reported by the endpoint     |
| First Endpoint  | String  | Machine name reported by the first endpoint if the endpoint is a server or a cloud service client. <br/> **Example value:** MACHINENAME  | <br/>&bull; This data was not reported by the endpoint    |
| Second Endpoint  | String  | Machine name reported by the second endpoint if the endpoint is a server or a cloud service client. <br/> **Example value:** MACHINENAME | <br/>&bull; This data was not reported by the endpoint     |
| First OS  | String  | Full Operating System and architecture string reported by the first endpoint. <br/> **Example value:** Windows 10.0.14996 SP: 0.0 Type: 1(Workstation) Suite: 256 Arch: x64 WOW64: True | <br/>&bull; This data was not reported by the endpoint |
| Second OS  | String  | Full Operating System and architecture string reported by the second endpoint. <br/> **Example value:** Windows 10.0.14996 SP: 0.0 Type: 1(Workstation) Suite: 256 Arch: x64 WOW64: True  | <br/>&bull; This data was not reported by the endpoint |
| First OS Filtered  | String  | Operating System name and major and minor version reported by the first endpoint. There may be cases where this string contains more than the OS name and version. <br/> **Example value:** Windows 10  | <br/>&bull; The endpoint does not report this information <br/>&bull; The report from this endpoint was not received.  |
| Second OS Filtered  | String  | Operating System name and major and minor version reported by the second endpoint. There may be cases where this string contains more than the OS name and version. <br/> **Example value:** Windows 10  | <br/>&bull; The endpoint does not report this information <br/>&bull; The report from this endpoint was not received |
| First OS Architecture  | String  | Hardware architecture reported by the first endpoint. <br/> **Example value:** x64  | &bull; The endpoint does not report this information <br/>&bull; The report from this endpoint was not received <br/>&bull; The format of the architecture wasn't recognized |
| Second OS Architecture  | String  | Hardware architecture reported by the second endpoint. <br/> **Example value:** x64  | &bull; The endpoint does not report this information <br/>&bull; The report from this endpoint was not received <br/>&bull; The format of the architecture wasn't recognized  |
| First Virtualization Flag  | Enumeration <br/>**Possible values:** <br/> "0x00" = None " <br/> "0x01" = HyperV <br/> "0x02" = VMWare <br/> "0x04" = Virtual PC <br/> "0x08" = Xen PC | Flag indicating the type of virtualization environment reported by the first endpoint. | <br/>&bull; Data was not reported by the endpoint |
| Second Virtualization Flag  | Enumeration <br/>**Possible values:** <br/> "0x00" = None " <br/> "0x01" = HyperV <br/> "0x02" = VMWare <br/> "0x04" = Virtual PC <br/> "0x08" = Xen PC | Flag indicating the type of virtualization environment reported by the second endpoint.  | <br/>&bull; Data was not reported by the endpoint |
|First Endpoint Make | | | <!-- gap here. presume these all correspond to endpoint data provided in uploaded files -->
| First Endpoint Model |||
| First Endpoint Type|||
| First Endpoint Label 1|||
| First Endpoint Label 2|||
| First Endpoint Label 3|||
| Second Endpoint Make|||
| Second Endpoint Model|||
| Second Endpoint Type|||
| Second Endpoint Label 1|||
| Second Endpoint Label 2|||
| Second Endpoint Label 3|||
|**Building**| | |
| First Network | String | Subnet used for media stream by the first endpoint if the subnet exists in subnet to tenant building data. <br/> **Example value:** 10.0.1.12.0 | &bull; Network data was not reported by the endpoint <BR/>&bull; Network is not defined in subnet-mapping data.  |
| First Network Name  | String  | Name of network used for media stream by first endpoint.  Based on mapping subnet to tenant building data. <br/> **Example value:** USA/WA/REDMOND | &bull; Network data was not reported by the endpoint <br/>&bull; Network is not defined in subnet-mapping data  |
| First Network Range  | String  | Network prefix/range of subnet used for media stream by first endpoint based on mapping subnet to tenant building data. <br/> **Example value:** 24 | &bull; Network data was not reported by the endpoint <br/>&bull; Network is not defined in subnet-mapping data |
| First Building Name  | String  | Name of the building where the first endpoint was located based on mapping subnet to tenant building data.  <br/> **Example value:** Main  | &bull; Network data was not reported by the endpoint <br/>&bull; Network is not defined in subnet-mapping data   |
| First Ownership Type  | String  | Ownership type of the building where the first endpoint was located. Based on mapping subnet to tenant building data. <br/> **Example value:** Contoso-IT  | &bull; Network data was not reported by the endpoint <br/>&bull; Network is not within the corporate network or network  ownership  is not defined in subnet-mapping data  |
| First Building Type   | String  | Type of building where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Open Office | &bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have building type defined in subnet-mapping data  |
| First Building Office Type  | String  | Type of building where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Open Office | &bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have building type defined in subnet-mapping data  |
| First City  | String  | City where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Redmond | &bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have city defined in subnet-mapping data   |
| First Zip Code  | String  | Zip/Postal code where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** 98052 | &bull; Network data not reported by the endpoint or, network  is not within corporate network <br/>&bull; Network does not have zip code defined in subnet-mapping data   |
| First Country  | String  | Country where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** USA | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have country defined in subnet-mapping data |
| First State  | String  | State where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** WA | <br/>&bull; Network data was not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have State defined in subnet-mapping data.   |
| First Region  | String  | Region where the first endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** North America | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have region defined in subnet-mapping data. |
| First Express Route  <!-- UI correction? spelling -->| Boolean  | True if the subnet used for media stream by first endpoint is enabled for ExpressRoute based on mapping subnet to tenant building data.   |  &bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have ExpressRoute flag set in subnet-mapping data.   | <!-- UI change? -->
| Second Network  | String  | Subnet used for media stream by second endpoint if subnet exists in subnet to tenant building data. <br/> **Example value:** 10.0.1.12.0  | &bull; Network data not reported by the endpoint <br/>&bull; Network is not defined in subnet-mapping data  |
| Second Network Name  | String  | Name of network used for media stream by second endpoint based on mapping subnet to tenant building data. <br/> **Example value:** USA/ WA/ REDMOND  | &bull; Network data not reported by the endpoint <br/>&bull; Network does not have network name defined in subnet-mapping data  |
| Second Network Range  | String  | Network prefix/range of subnet used for media stream by second endpoint based on mapping subnet to tenant building data. <br/> **Example value:** 24  | &bull; Network data not reported by the endpoint <br/>&bull; Network does not have network range defined in subnet-mapping data  |
| Second Building Name  | String  | Name of the building where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Main | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; network does not have building name defined in subnet-mapping data |
| Second Ownership Type  | String  | Ownership type of building where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Contoso - IT | &bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have ownership defined in subnet-mapping data |
| Second Building Type  | String  | Type of building where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Open Office | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have building type defined in subnet-mapping data   |
| Second Building Office Type  | String  | Office building type where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Office  | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have building office type defined in subnet-mapping data.  |
| Second City  | String  | City where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** Redmond |  <br/>&bull; Network data not reported by the endpoint  <br/>&bull; Network is not within corporate network  <br/>&bull; Network does not have city defined in subnet-mapping data   |
| Second Zip Code  | String  | Zip/Postal code where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** 98052  | <br/>&bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have zip code defined in subnet-mapping data |
| Second Country  | String  | Country where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** USA  | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have country defined in subnet-mapping data  |
| Second State  | String  | State where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** WA  | <br/>&bull; Network data not reported by the endpoint<br/>&bull; Network is not within corporate network <br/>&bull; Network does not have state defined in subnet-mapping data  |
| Second Region  | String  | Region where the second endpoint was located based on mapping subnet to tenant building data. <br/> **Example value:** North America  | <br/>&bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have region defined in subnet-mapping data. |
| Second Express Route  | Boolean  | True if the subnet used for media stream by second endpoint is enabled for ExpressRoute based on mapping subnet to tenant building data.    | <br/>&bull; Network data not reported by the endpoint <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have ExpressRoute flag set in subnet-mapping data   | <!-- UI change? ExpressRoute misspelled in UI-->
| First Inside Corp  | Enumeration <br/>**Possible values:** <br/> Inside, Outside  | Indicates if first endpoint was located on subnet within the corporate network based on mapping subnet to tenant building data. By default, the endpoint is considered Outside. <br/> **Example value:** Inside | |
| Second Inside Corp  | Enumeration <br/> **Possible values:** <br/> Inside, Outside | Indicates if second endpoint was located on subnet within the corporate network based on mapping subnet to tenant building data. By default, the endpoint is considered Outside.  **Example value:** Inside  |  |
|**Deployment**| | | |
| First Tenant Id  | String  | Office 365 Tenant ID for the first endpoint. <br/> **Example value:** 00000000 - 0000 -0000 - 0000 - 000000000000  | <br/>&bull; Tenant id for the first endpoint could not be determined. This may indicate the endpoint was signed in to an on-premise Skype for Business Server deployment.  |
| Second Tenant Id  | String  | Office 365 Tenant ID for the second endpoint. <br/> **Example value:** 00000000 - 0000 - 0000 - 0000 - 000000000000  |  <br/>&bull; Tenant id for the second endpoint could not be determined. This may indicate the endpoint was signed in to an on-premise Skype for Business Server deployment.  |
| First Pool  | String  | Skype for Business Online pool FQDN assigned to the first endpoint. <br/> **Example value:** pool1<span></span>.lync<span></span>.com  | <br/>&bull; Skype for Business Online pool could not be determined for the first endpoint. This may indicate the endpoint was signed in to an on-premise Skype for Business Server deployment.  |
| Second Pool  | String  | Skype for Business Online pool FQDN assigned to the second endpoint. <br/> **Example value:** pool1<span></span>.lync<span></span>.com   | &bull; Skype for Business Online pool could not be determined for the second endpoint. This may indicate the endpoint was signed in to an on-premise Skype for Business Server deployment.  |
| Is Federated  | Boolean  | True if streams were between two federated tenants, False otherwise.   | <br/>&bull; It could not be determined if this was a federated stream, <br/>&bull; Some signaling data was not collected.   |
|Region | String <!-- guesswork, was missing --> | Region where the deployment was located based on mapping subnet to deployment data. <br/> **Example value:** North America | <br/>&bull; Network data not reported <br/>&bull; Network is not within corporate network <br/>&bull; Network does not have region defined in subnet-mapping data. |
|**Stream**| | | |
| QoE Record Available  | Boolean  | True if at least one Quality of Experience report was available for call/session. Many dimensions and measurements are available only if a QoE record was available. If the call does not establish successfully, a QoE record will not be available.    |   |
| CDR Record Available  | Boolean  | True if at least one Call Detail Records was available for call/session.     | |
| Media Line Label  | Integer  | Label in SDP for media line. Use Media Type to determine if label is used for video, audio, app sharing, or video based screen sharing. <br/> **Example value:** 0  | &bull; This data was not reported by the endpoint.  |
| Media Type  | String  | Type of media (video, audio, app sharing, or video based screen sharing). <br/> **Example value:** Audio |  |
|Media Line Label Text | String | <!-- Gage Ames info needed--> | |
| First Is Server  | Enumeration <br/>**Possible values:** <br/>&bull; Client <br/>&bull; Server  | Indicates if the first endpoint is a server endpoint such as a conferencing server (AVMCU, ASMCU) or other media servers (Mediation Server), or is a client endpoint.  **Example value:** Client | |
| Second Is Server  | Enumeration <br/>**Possible values:** <br/>&bull; Client <br/>&bull; Server   | Indicates if the second endpoint is a server endpoint such as a conferencing server (AVMCU, ASMCU) or other media servers (Mediation Server), or is a client endpoint.   **Example value:** Client | |
| First Is Caller  | Boolean  | True if the first endpoint was the caller (initiated the session establishment).   | |
| First Network Connection Detail  | Enumeration <br>**Possible values:** <br/>&bull; Wired <br/>&bull; Wifi <br/>&bull; MobileBB <br/>&bull; Tunnel <br/>&bull; Other | Type of network used by the first endpoint.  <br/> **Example value:** Wired  | &bull; Data was not reported by the endpoint  |
| Second Network Connection Detail  | Enumeration <br/>**Possible values:** <br/>&bull; Wired <br/>&bull; Wifi <br/>&bull; MobileBB <br/>&bull; Tunnel <br/>&bull; Other | Type of network used by the second endpoint.  <br/> **Example value:** Wired  | &bull; Data was not reported by the endpoint  |
| Stream Direction  | Enumeration <br/>**Possible values:** <br/>&bull; First-to-Second <br/>&bull; Second-to-First <br/> | Indicates the direction of a stream between the endpoints.  **Example value:** First-to-Second | &bull; No data was reported to indicate the direction of the stream |
| Payload Description  | String  | Name of last codec used in the stream. <br/> **Example value:** SILKWide | &bull; No data is available |
| Audio and Video Call  | Boolean  | True if call had both audio and video streams, False otherwise    | &bull; No data was reported to indicate the media types of the stream. |
| Duration 5 seconds or less  | Boolean  | True if stream had duration of 5 seconds or less, False otherwise.   ||
| Duration 60 seconds or more  | Boolean  | True if stream had duration of 60 seconds of more, False otherwise.   | |
| Is Teams  | Boolean  | True indicates that the first or second user agent for the stream is a Microsoft Teams endpoint. <br/> False indicates the user agents are Skype for Business endpoints. |  |
| Duration (Minutes)  | Range (minutes)  | Duration of stream in minutes. Values grouped by range. <br/> **Example value:** 065: [3 - 4) ||
| Duration (Seconds)  | Range (seconds) | Duration of stream in seconds. Values grouped by range. <br/> **Example value:** 062: [1 -2)||
|**Date**|||
|End Time|<!--gap -->||
| Year  | Integer  | Year of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 2018 | |
| Month  | Integer  | Month of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 2 | |
| Day  | Integer  | Day of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 1 | |
| Date  | String  | Date the stream ended. Values are reported in the UTC time zone. <br/> **Example value:** 2018-06-01 | |
| Hour  | Integer  | Hour of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 1  ||
| Minute  | Integer  | Minute of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 30 | |
| Second  | Integer  | Second of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 12 | |
| Day Of Year  | Integer  | Day of year of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 32 | |
| Day Of Week  | String  | Day of week of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** Wednesday | |
| Day Number Of Week  | Integer  | Day number of week of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 3 | |
|Week|<!--gap -->||
| Month Year  | String  | Month and year of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 2017-02 | |
| Full Month  | Date time  | Full Month of the end of the stream. Values are reported in the UTC time zone. <br/> **Example value:** 2017-02-01T00:00:00 | |
|Start time|<!--gap -->||
|**UserAgent** | | |
| First Domain  | String  | Domain of the user using the first endpoint. If the first endpoint is a conference server, it is the domain of the organizer of the meeting. May also be the domain of service accounts used in scenario.  <br/> **Example value:** contoso<span></span>.com | |
| Second Domain  | String  | Domain of the user using the second endpoint. If the second endpoint is a conference server, it is the domain of the organizer of the meeting. May also be the domain of service accounts used in scenario. <br/> **Example value:** contoso<span></span>.com  | |
| First User Agent Category  | String  | Category of the user agent of the first endpoint. <br/> **Example value:** OC | &bull; A user agent  such as a 3rd party user agent does not currently have a mapping    |
| Second User Agent Category  | String  | Category of the user agent of the second endpoint. <br/> **Example value:** OC | &bull; A user agent such as a 3rd party user agent does not currently have a mapping    |
| First User Agent  | String  | User agent string of the first endpoint. <br/> **Example value:** UCCAPI/16.0.7766.5281 OC/16.0.7766.2047 (Skype for Business) | &bull; No user agent reported by first endpoint   |
| Second User Agent  | String  | User agent string of the second endpoint. <br/> **Example value:** UCCAPI/16.0.7766.5281 OC/16.0.7766.2047 (Skype for Business) | &bull; No user agent was reported by second endpoint   |
| Conference Type  | Enumeration <br/>**Possible values:** <br/>&bull; conf:applicationsharing <br/>&bull; conf:audio-video <br/>&bull; conf:focus | Type of conference URI.  <br/> **Example value:** conf:audio-video | &bull; Non-conference scenario.   |
| Conference Id  | String  | Conference ID associated with the streams. Note this dimension may have too many rows to be used as dimension in a report. It can be used a filter instead.  <br/> **Example value:** 0001P6GK  | &bull; Non-conference scenario. |
| First Client App Version  | String  | Version of the application used for the first endpoint. Data is parsed from the user agent string. <br/> **Example value:** 16.0.7766.2047 | &bull; The version string could not be parsed <br/>&bull; The value was not reported.   |
| Second Client App Version  | String  | Version of the application used for the second endpoint. Data is parsed from the user agent string. <br/> **Example value:** 16.0.7766.2047 | &bull; The version string could not be parsed <br/>&bull; The value was not reported. |
|Meeting Id|<!-- gap -->||
|**Network**||| 
| Transport  | Enumeration <br/>**Possible values:** <br/>&bull; UDP <br/>&bull; TCP <br/>&bull; Unrecognized  | Network transport type used by stream.  Unrecognized indicates that the system could not determine if the transport type was TCP or UDP.  | &bull; Transport type was not reported <br/>&bull; The media path was not established  |
| First Connectivity Ice  | Enumeration <br/>**Possible values:** <br/>&bull; DIRECT= Direct network path <br/>&bull; RELAY = through relay <br/>&bull; HTTP = through HTTP proxy <br/>&bull; FAILED = connectivity failed | ICE connectivity type used by the first endpoint.  |&bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Connectivity Ice  | Enumeration <br/>**Possible values:** <br/>&bull; DIRECT= Direct network path <br/>&bull; RELAY = through relay <br/>&bull; HTTP = through HTTP proxy <br/>&bull; FAILED = connectivity failed  | ICE connectivity type used by the second endpoint.    | &bull; Transport type was not reported <br/>&bull; The media path was not established    |
| First IP Address  | String  | IP address for first endpoint. Note this dimension may have too many rows to be used as dimension in a report. It can be used as a filter instead. <br/> **Example value:** 10.0.0.10  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second IP Address  | String  | IP address for second endpoint. <br/> **Note:** This dimension may have too many rows to be used as dimension in a report. It can be used as a filter instead. <br/> **Example value:** 10.0.0.10  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| First Link Speed   |Integer  | Link speed in bits per second reported by the network adapter used by the first endpoint. <br/> **Example value:** 10000000  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Link Speed   |Integer  | Link speed in bits per second reported by the network adapter used by the second endpoint. <br/> **Example value:** 10000000 | &bull; Transport type was not reported <br/>&bull; The media path was not established    |
| First Port  | Port number  | Network port number used by first endpoint for media. <br/> **Example value:** 50018  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Port  | Port number  | Network port number used by second endpoint for media. <br/> **Example value:** 50018 | &bull; Transport type was not reported <br/>&bull; The media path was not established    |
| First Reflexive Local IP  | String  | IP address of first endpoint as seen by the media relay server. This is typically the public internet IP address associated to the first endpoint for the stream. <br/> **Example value:** 104.43.195.251  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Reflexive Local IP  | String  | IP address of second endpoint as seen by the media relay server. This is typically the public internet IP address associated to the second endpoint for the stream. <br/> **Example value:** 104.43.195.251  | &bull; Transport type was not reported <br/>&bull; The media path was not established  |
| First Relay IP  | String  | IP address of the media relay server allocated by the first endpoint. <br/> **Example value:** 104.43.195.251  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Relay IP  | String  | IP address of the media relay server allocated by the second endpoint. <br/> **Example value:** 104.43.195.251 | &bull; Transport type was not reported <br/>&bull; The media path was not established|
| First Relay Port  | Integer  | Media port allocated on the media relay server by the first endpoint. <br/> **Example value:** 3478  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second Relay Port  | Integer  | Media port allocated on the media relay server by the second endpoint. <br/> **Example value:** 3478  | &bull; Transport type was not reported <br/>&bull; The media path was not established|
| First Subnet  | String  | Subnet used for media stream by first endpoint with dashes separating each octet. <br/> **Example value:** 104.43.195.0  | &bull;Data not reported by the endpoint <br/>&bull; Media path was not established <br/>&bull; IPv6 was used|
| Second Subnet  | String  | Subnet used for media stream by second endpoint with dashes separating each octet. <br/> **Example value:** 104.43.195.0 | &bull;Data not reported by the endpoint <br/>&bull; Media path was not established <br/>&bull; IPv6 was used |
| First VPN  | Boolean  | True if the network adapter used by first endpoint indicated it was a VPN connection, False otherwise. Some VPN's do not correctly report this data correctly.   | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second VPN  | Boolean  | True if the network adapter used by second endpoint indicated it was a VPN connection, False otherwise. Some VPN's do not correctly report this data correctly.    | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Applied Bandwidth Source  | Enumeration <br/>**Possible values:** <br/>&bull; Static Max <br/>&bull; API Modality <br/>&bull; API Modality_All <br/>&bull; API SendSide BWLimit <br/>&bull; Preference Value <br/>&bull; TURN <br/>&bull; ReceiveSide TURN <br/>&bull; API SDP Modality <br/>&bull; Remote Recieved <br/>&bull; Side BWLimit <br/>&bull; API ServiceQuality <br/>&bull; API SDP <br/>&bull; Receive SidePDP | Identifies the source of bandwidth applied to the stream. | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Bandwidth Est | Integer Range  | Average estimated bandwidth available between first and second endpoint in bits per second.  <br/> **Example value:** 026: [260000 - 270000)  | &bull; Transport type was not reported <br/>&bull; The media path was not established  |
| Mediation Server Bypass Flag  | Boolean  | True if the media stream bypassed the Mediation Server and went straight between client and PSTN Gateway/PBX, False otherwise.   | &bull; Transport type was not reported <br/>&bull; The media path was not established    |
| First CDR Connectivity Type  | Enumeration <br/>**Possible values:** <br/>&bull; OS <br/>&bull; PeerDerived <br/>&bull; Stun <br/>&bull; Turn  | Identifies the ICE connectivity path selected by the first endpoint for use for this stream. <br/> **Example value:** OS  | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
| Second CDR Connectivity Type  | Enumeration <br/>**Possible values:** <br/>&bull; OS <br/>&bull; PeerDerived <br/>&bull; Stun <br/>&bull; Turn  | Identifies the ICE connectivity path selected by the second endpoint for use for this stream.  <br/> **Example value:** OS   | &bull; Transport type was not reported <br/>&bull; The media path was not established   |
|First BSSID|<!-- gap-->||
| Second BSSID|<!-- gap-->||
|**Device**| |||
| First Capture Dev  | String  | Name of the capture device used by the first endpoint. For: <br/> **Audio streams** = device used for the microphone <br/> **Video streams** = device used for the camera <br/> **Video-based-screen-sharing streams** = screen scraper <br/> **App sharing streams** = blank <br/> **Example value:** Headset Microphone (Microsoft LifeChat LX-6000)  | &bull; The data was not reported by the endpoint <br/>&bull; The media path was not established <br/>&bull; The stream was video-based screen sharing or application sharing.  |
| Second Capture Dev  | String  | Name of the capture device used by the second endpoint.  <br/> **Audio streams** = device used for the microphone <br/> **Video streams** = device used for the camera <br/> **Video-based-screen-sharing streams** = screen scraper <br/> **App sharing streams** = blank <br/> **Example value:** Headset Microphone (Microsoft LifeChat LX-6000) | <br/>&bull; Data was not reported by the endpoint <br/>&bull; Media path was not established <br/>&bull; The stream was video-based screen sharing or application sharing   |
| First Capture Dev Driver  | String  | Name of the capture device driver used by the first endpoint in the form of "manufacturer : version". For: <br/> **Audio streams** = driver used for the microphone <br/> **Video streams** = driver used for the camera <br/> **Video-based-screen-sharing and app sharing streams** = blank  <br/> **Example value:** Microsoft: 10.0.14393.0 | <br/>&bull; Data was not reported by the endpoint <br/>&bull; The media path was not established <br/>&bull; The stream was video-based screen sharing or application sharing.  |
| Second Capture Dev Driver  | String  | Name of the capture device driver used by the second endpoint in the form of "manufacturer : version". For: <br/> **Audio streams** = driver used for the microphone <br/> **Video streams** = driver used for the camera <br/> **Video-based-screen-sharing and app sharing streams** = blank <br/> **Example value:** Microsoft: 10.0.14393.0  | <br/>&bull; Data was not reported by the endpoint <br/>&bull; The media path was not established <br/>&bull; The stream was video-based screen sharing or application sharing.  |
| First Render Dev  | String  | Name of the render device used by the first endpoint. For: <br/> Audio streams - device used for the speaker <br/> Video and video-based-screen-sharing streams - device used for the display <br/> App sharing streams - blank  <br/> **Example value:** Headset Earphone (Microsoft LifeChat LX-6000) | <br/>&bull; This data not reported by the endpoint <br/>&bull; The media path was not established  <br/>&bull; The stream was application sharing    |
| Second Render Dev  | String  | Name of the render device used by the second endpoint. For: <br/> Audio streams - device used for the speaker <br/> Video and video-based-screen-sharing streams - device used for the display <br/> App sharing streams - blank <br/> **Example value:** Headset Earphone (Microsoft LifeChat LX-6000) | <br/>&bull; This data was not reported by the endpoint, <br/>&bull; Media path was not established <br/>&bull; The stream was application sharing     |
| First Render Dev Driver  | String  | Name of the render device driver used by the first endpoint. For: <br/> Audio streams - driver used for the speaker <br/> Video and video-based-screen-sharing streams - driver used for the display <br/> App sharing streams - blank  <br/> **Example value:** Microsoft: 10.0.14393.0 | <br/>&bull; This data was not reported by the endpoint <br/>&bull; Media path was not established <br/>&bull; The stream was application sharing    |
| Second Render Dev Driver  | String  | Name of the render device driver used by the second endpoint. For: <br/> Audio streams - driver used for the speaker <br/> Video and video-based-screen-sharing streams - driver used for the display <br/> App sharing streams - blank <br/> **Example value:** Microsoft: 10.0.14393.0  | <br/>&bull; This data was not reported by the endpoint <br/>&bull; Media path was not established <br/>&bull; The stream was application sharing   |
|**WiFi**|||
| First Wi-Fi Microsoft Driver  | String  | Name of Microsoft WiFi driver used reported by the first endpoint. Value may be localized based on the language used by endpoint. <br/> **Example value:** Microsoft Hosted Network Virtual Adapter  | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported|
| Second Wi-Fi Microsoft Driver  | String  | Name of Microsoft WiFi driver used reported by the second endpoint. Value may be localized based on the language used by endpoint. <br/> **Example value:** Microsoft Hosted Network Virtual Adapter  | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported|
| First Wi-Fi Vendor Driver  | String  | Vendor and name of WiFi driver reported by the first endpoint. <br/> **Example value:** Contoso Dual Band Wireless-AC Driver  | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported |
| Second Wi-Fi Vendor Driver  | String  | Vendor and name of WiFi driver reported by the second endpoint.  <br/> **Example value:** Contoso Dual Band Wireless-AC Driver | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported |
| First Wi-Fi Microsoft Driver Version  | String  | Version of Microsoft WiFi driver reported by the first endpoint. <br/> **Example value:** Microsoft:10.0.14393.0 | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported  |
| Second Wi-Fi Microsoft Driver Version  | String  | Version of Microsoft WiFi driver reported by the second endpoint. <br/> **Example value:** Microsoft:10.0.14393.0 | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported  |
| First Wi-Fi Vendor Driver Version  | String  | Vendor and version of WiFi driver reported by the first endpoint. <br/> **Example value:** Contoso:15.1.1.0 | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported  |
| Second Wi-Fi Vendor Driver Version  | String  | Vendor and version of WiFi driver reported by the second endpoint. <br/> **Example value:** Contoso:15.1.1.0 | <br/>&bull; WiFi wasn't used by the endpoint <br/>&bull; The driver information was not reported  |
| First Wi-Fi Channel  | String  | WiFi channel used by the first endpoint.  <br/> **Example value:** 10| <br/>&bull; WiFi was not used <br/>&bull; The channel was not reported   |
| Second Wi-Fi Channel  | String  | WiFi channel used by the second endpoint. <br/> **Example value:** 10  | <br/>&bull; WiFi was not used <br/>&bull; The channel was not reported  |
| First Wi-Fi Radio Type  | String  | Type of WiFi radio used by the first endpoint. HRDSSS is equivalent to 802.11b. <br/> **Example value:** 802.11ac  | <br/>&bull; WiFi was not used <br/>&bull; The WiFi type was not reported  |
| Second Wi-Fi Radio Type  | String  | Type of WiFi radio used by the second endpoint. HRDSSS is equivalent to 802.11b. <br/> **Example value:** 802.11ac  | <br/>&bull; WiFi was not used <br/>&bull; The WiFi type was not reported  |
| First DNS Suffix  | String  | DNS suffix associated with the network adapter reported by the first endpoint. Note this value may be reported for any type of network adapter. **Example value:** corp<span></span>.contoso<span></span>.com  | <br/>&bull; This value was not reported by the endpoint <br/>  |
| Second DNS Suffix  | String  | DNS suffix associated with the network adapter reported by the second endpoint. Note this value may be reported for any type of network adapter.<br/> **Example value:** corp<span></span>.contoso<span></span>.com   | <br/>&bull; This value was not reported by the endpoint  |
| First Wi-Fi Band  | String  | WiFi band used as reported by the first endpoint. <br/> **Example value:** 5.0 Ghz  | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported  |
| Second Wi-Fi Band  | String  | WiFi band used as reported by the second endpoint. <br/> **Example value:** 5.0 Ghz  | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported  |
| First Wi-Fi Signal Strength  | String  | WiFi signal strength in percentage [0-100] reported by the first endpoint. <br/> **Example value:** 081: [90 - 100)  | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported  |
| Second Wi-Fi Signal Strength  | String  | WiFi signal strength in percentage [0-100] reported by the second endpoint. <br/> **Example value:** 081: [90 - 100)  | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported  |
| First Wi-Fi Battery Charge  | Range (percentage)  | Estimated remaining battery charge in percentage [0-99] reported by the first endpoint. Values grouped by range. 0 indicates that the device was plugged in. <br/> **Example value:** 081: [90 - 100) | &bull; WiFi was not used <br/>&bull; The charge value was not reported   |
| Second Wi-Fi Battery Charge  | Range (percentage)  | Estimated remaining battery charge in percentage [0-99] reported by the second endpoint. Values grouped by range. 0 indicates that the device was plugged in.  <br/> **Example value:** 081: [90 - 100) | &bull; WiFi was not used <br/>&bull; The charge value was not reported  |
|**Metrics**|||
| Audio Degradation Avg  | Range (Mean opinion score 0-5) | Average Network Mean Opinion Score degradation for stream. Represents how much the network loss and jitter have impacted the quality of received audio. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02) | &bull; No network MOS degradation was reported by the endpoint receiving the stream <br/>&bull; The stream is not an audio stream.    |
| Jitter  | Range (millisecond)  | Average jitter for stream in milliseconds. Values grouped by range. <br/> **Example value:** 065: [2 - 3)  | &bull; No jitter data was reported by the endpoint receiving the stream |
| Jitter Max  | Range (millisecond)  | Maximum jitter for stream in milliseconds. Values grouped by range. <br/> **Example value:** 065: [2 - 3) | &bull; No jitter data was reported by the endpoint receiving the stream   |
| Packet Loss Rate  | Range (ratio)  | Average packet loss rate for stream. Values grouped by range. 0.1 indicates 10% packet loss. <br/> **Example value:** 015: [0.01 - 0.02)  | &bull; No packet loss data was reported by the endpoint receiving the stream |
| Packet Loss Rate Max  | Range (ratio)  | Maximum packet loss rate for stream. Values grouped by range. 0.1 indicates 10% packet loss. <br/> **Example value:** 023: [0.09 - 0.1)  | &bull; No packet loss data was reported by the endpoint receiving the stream |
| Overall Avg Network MOS  | Range (MOS)  | Average Network MOS for stream. Values grouped by range. <br/> **Example value:** 076: [4.4 - 4.5) | &bull; No network MOS degradation was reported by the endpoint receiving the stream <br/>&bull; The stream is not an audio stream  |
| Ratio Concealed Samples Avg  | Range (ratio)  | Ratio of the number of audio frames with samples generated by packet loss concealment to the total number of audio frames. Values grouped by range. 0.1 indicates 10% of frames contained concealed samples. <br/> **Example value:** 015: [0.01 - 0.02) | &bull; This value was not reported by the receiver of the stream <br/>&bull; The stream was not an audio stream  |
|Conceal Ratio Max|<!-- gap-->||
| Ratio Stretched Samples Avg  | Range (ratio)  | Ratio of the number of audio frames with samples that have been stretched to compensate for jitter or loss to the total number of audio frames. Values grouped by range. 0.1 indicates 10% audio frames contained stretched samples. <br/> **Example value:** 017: [0.03 - 0.04) | &bull; This value was not reported by the receiver of the stream  <br/>&bull; The stream was not an audio stream   |
|Healer Packet Drop Ratio|<!-- gap-->||
| Healer FEC Packet Used Ratio|||
| Round Trip  | Range (milliseconds)  | Average network propagation round-trip time computed as specified in RFC3550 in milliseconds. Values grouped by range. <br/> **Example value:** 070: [15 - 20)  | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported  |
| Round Trip Max  | Range (milliseconds)  | Maximum network propagation round-trip time computed as specified in RFC3550 in milliseconds. Values grouped by range. <br/> **Example value:** 098: [350 - 375)   | <br/>&bull; The value was not computed by the endpoint <br/>&bull; The value was not reported |
| Packet Utilization |||
| Jitter Buffer Size Avg|||
| Jitter Buffer Size Max|||
| Jitter Buffer Size Min|||
|Relative OneWay Gap Duration|||
| Audio Post FECPLR|||
| Network Jitter Avg  | Range (milliseconds)  | Average of network jitter in milliseconds computed over 20 second windows during the session. Values grouped by range. <br/> **Example value:** 066: [3 - 4)  | <br/>&bull; The stream was not an audio stream <br/>&bull; Data was not reported by the endpoint receiving the stream  |
|Network Jitter Max|||
| Network Jitter Min|||
| Video Post FECPLR  | Range (ratio)  | Packet loss rate after FEC has been applied for aggregated across all video streams and codecs. Values grouped by range. <br/> **Example value:** 014: [0 - 0.01) | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream   |
| Video Local Frame Loss Percentage Avg  | Range (percentage)  | Average percentage of video frames lost as displayed to the user. Values grouped by range. This includes frames recovered from network losses. <br/> **Example value:** 160: [80 - 85) | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream   |
| Recieved Frame Rate Average  | Range (frames per second)  | Average frames per second received for all video streams computed over the duration of the session. Values grouped by range. <br/> **Example value:** 101: [14.5 - 15) | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream   |
| Low Frame Rate Call Percent | Range (percentage)  | Percentage of time of the call where frame rate is less than 7.5 frames per second. Values grouped by range. <br/> **Example value:** 099: [13.5 - 14) | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream   |
| Video Packet Loss Rate  | Range (ratio)  | Average fraction of packets lost, as specified in RFC3550, computed over the duration of the session. Values grouped by range. <br/> **Example value:** 037: [0.75 - 0.8) | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream   |
| Video Frame Rate Avg  | Range (frames per second)  | Average frames per second received for a video stream, computed over the duration of the session. Values grouped by range. <br/> **Example value:** 135: [31.5 - 32)  | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream  |
| Dynamic Capability Percent  | Range (percentage)  | Percentage of time that the client is running < 70% expected video processing capability for this type of CPU grouped by range <br/> **Example value:** 122: [25 - 25.5)  | <br/>&bull; The stream was not a video or video-based-screen-sharing stream  <br/>&bull; Data was not reported by the endpoint receiving the stream  |
| Spoiled Tile Percent Total  | Range (percentage)  | Percentage of tiles which are discarded instead of being sent to a remote peer (for example, from the MCU to a viewer). Values grouped by range. Discarded tiles may be caused by bandwidth restrictions between client and server. <br/> **Example value:** 140: [34 - 34.5)  | <br/>&bull; The stream was not an application sharing stream <br/>&bull; The data was not reported by the endpoint sending the stream  |
| AppSharing Relative OneWay Average  | Range (seconds)  | Average relative one-way delay between the endpoints in seconds for application sharing streams. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02) | <br/>&bull; The stream was not an application sharing stream <br/>&bull; The data was not reported by the endpoint sending the stream   |
| AppSharing RDP Tile Processing Latency Average  | Range (milliseconds)  | Average latency in milliseconds processing tiles on the RDP Stack at the conferencing server. Values grouped by range. <br/> **Example value:** 103: [15.5 - 16) | &bull; The stream was not an application sharing stream in a conference <br/>&bull; The data was not reported by the endpoint sending the stream   | 
| First Network Delay Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the network delay was significant enough to impact the ability to have real-time two-way communication. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint|
| Second Network Delay Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the network delay was significant enough to impact the ability to have real-time two-way communication. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Network Bandwidth Low Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the available bandwidth or bandwidth policy was low enough to cause poor quality of the audio sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint  |
| Second Network Bandwidth Low Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the available bandwidth or bandwidth policy was low enough to cause poor quality of the audio sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Mic Glitch Rate|<!-- gaps-->||
| Second Mic Glitch Rate|||
| First Speaker Glitch Rate|||
| Second Speaker Glitch Rate|||
|**Audio**|||
| Audio FEC Used  | Boolean  | True indicates that audio forward error correction (FEC) was used at some point during the call. False otherwise     | &bull; The stream was not an audio stream <br/>&bull; The data was not reported by the endpoint sending the stream  |
|**Measure**|||
| ClassifiedPoorCall  | Boolean  | True if the stream was classified as poor based on the metrics listed in [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md).   | &bull; The stream did not have sufficient metrics reported to be classified as good or poor   |
| Video Poor Due To VideoPostFecplr  | Boolean  | True if the stream was classified as poor based on the Video Post FEC PLR metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-video streams.   | &bull; The endpoint did not report this data  <br/>&bull; The stream was not a video stream.  |
| Video Poor Due To VideoLocalFrameLossPercentageAvg  | Boolean  | True if the video stream was classified as poor based on the Video Local Frame Loss Percentage Avg metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-video streams.   | &bull; The endpoint did not report this data  <br/>&bull; The stream was not a video stream. |
| Video Poor Due To VideoFrameRateAvg  | Boolean  | True if the video stream was classified as poor based on the Video Frame Rate Avg metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-video streams.    | &bull; The endpoint did not report this data  <br/>&bull; The stream was not a video stream |
| VBSS Poor Due To VideoPostFecplr  | Boolean  | True if the video based-screen-sharing stream was classified as poor based on the Video Post FEC PLR metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-video based-screen-sharing streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not a video-based screen sharing stream  |
| VBSS Poor Due To VideoLocalFrameLossPercentageAvg  | Boolean  | True if the video based-screen-sharing stream was classified as poor based on the Video Local Frame Loss Percentage Avg metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non- video based-screen-sharing streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not a video-based screen sharing stream  |
| VBSS Poor Due To VideoFrameRateAvg  | Boolean  | True if the video based-screen-sharing stream was classified as poor based on the Video Frame Rate Avg metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-video based-screen-sharing streams.   | &bull; The endpoint did not report this data <br/>&bull; The stream was not a video-based screen sharing stream   |
| AppSharing Poor Due To SpoiledTilePercentTotal  | Boolean  | True if the application sharing stream was classified as poor based on the Spoiled Tile Percent Total metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-application sharing streams.   | &bull; The endpoint did not report this data  <br/>&bull; The stream was not an application sharing stream.  |
| AppSharing Poor Due To RelativeOneWayAverage  | Boolean  | True if the application sharing stream was classified as poor based on the Relative One Way Average metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-application sharing streams.    | &bull; The endpoint did not report this data  <br/>&bull; The stream was not an application sharing stream |
| AppSharing Poor Due To RDPTileProcessingLatencyAverage | Boolean  | True if the application sharing stream was classified as poor based on the RDP Tile Processing Latency Average metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-application sharing streams.    | &bull; The endpoint did not report this data  <br/>&bull; The stream was not an application sharing stream |
| Audio Poor Due To Jitter  | Boolean  | True if the audio stream was classified as poor based on the Jitter metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-audio streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not an audio sharing stream |
| Audio Poor Due To RoundTrip  | Boolean  | True if the audio stream was classified as poor based on the Round Trip metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-audio streams.   | &bull; The endpoint did not report this data <br/>&bull; The stream was not an audio sharing stream |
| Audio Poor Due To Packet Loss  | Boolean  | True if the audio stream was classified as poor based on the Packet Loss metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-audio streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not an audio sharing stream |
| Audio Poor Due To Degradation  | Boolean  | True if the audio stream was classified as poor based on the Degradation metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-audio streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not an audio sharing stream |
| Audio Poor Due To Concealed Ratio  | Boolean  | True if the audio stream was classified as poor based on the Concealed Ratio metric threshold listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). Will always be False for non-audio streams.    | &bull; The endpoint did not report this data <br/>&bull; The stream was not an audio sharing stream |
| Poor Reason  | Flags <br/>**Possible values:** <br/>&bull; Concealed Ratio <br/>&bull; Degradation <br/>&bull; Jitter <br/>&bull; Packet Loss <br/>&bull; Round Trip <br/> Video Frame Rate Avg <br/> Video Local Frame Loss Percentage Avg <br/>&bull; Video Post FEC PLR <br/>&bull; RDP Tile Processing Latency Average <br/>&bull; Relative OneWay Average <br/>&bull; Spoiled Tile Percent Total | List of flags that identify why the stream was marked as poor. There may be multiple flags set since there may be multiple reasons why the stream was marked as Poor. Refer to [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md) for details.  | &bull; The stream was not classified as poor |
| Poor  | Boolean  | True if the stream has sufficient data to be classified as good or poor and stream is classified as poor. False otherwise.   |   |
| Good  | Boolean  | True if the stream has sufficient data to be classified as good or poor and stream is classified as good. False otherwise.   |   |
| Unclassified  | Boolean  | False if the stream has sufficient data to be classified as good or poor. True otherwise. <br/>**Example value:** 1 |   |
| OnePercent PacketLoss  | Boolean  | True if packet loss exceeded 1%, False otherwise.  |   |
|**Rating**|||
| First Feedback Rating  | User rating (1-5)  | Rating of the call associated with the stream by the first endpoint on 1-5 scale (5 = excellent). 0 indicates the user was shown the call rating survey but did not rate their experience.  <br/> **Example value:** 5 | &bull; No survey was shown to the first endpoint  |
| Second Feedback Rating  | User rating (1-5)  | Rating of the call associated with the stream by the second endpoint on 1-5 scale (5 = excellent). 0 indicates the user was shown the call rating survey but did not rate their experience. <br/> **Example value:** 5 | &bull; No survey was shown to the second endpoint   |
| First Feedback Tokens  | String  | String containing list of feedback tokens with boolean flag indicating if token was set by the user providing feedback from the first endpoint. <br/> **Example value:** {DistortedSpeech:1; ElectronicFeedback:1; BackgroundNoise:1; MuffledSpeech:1; Echo:1;}  | &bull; No feedback was provided by the user of the first endpoint  |
| Second Feedback Tokens  | String  | String containing list of feedback tokens with boolean flag indicating if token was set by the user providing feedback from the second endpoint. <br/> **Example value:** {DistortedSpeech:1; ElectronicFeedback:1; BackgroundNoise:1; MuffledSpeech:1; Echo:1;}  | &bull; No feedback was provided by the user of the second endpoint  |
| First Feedback Has Audio Issue  | Boolean  | True if feedback tokens from first endpoint indicate stream had an audio issue, false otherwise.   |  |
| Second Feedback Has Audio Issue  | Boolean  | True if feedback tokens from second endpoint indicate stream had an audio issue, False otherwise.    ||
| First Feedback Has Video Issue  | Boolean  | True if feedback tokens from first endpoint indicate stream had a video issue, False otherwise.    | |
| Second Feedback Has Video Issue  | Boolean  | True if feedback tokens from second endpoint indicate stream had a video issue, False otherwise.    | |
| First Feedback Has AppSharing Issue  | Boolean  | True if feedback tokens from first endpoint indicate stream had an  app sharing issue, False otherwise.    | | <!-- UI confirm -->
| Second Feedback Has Appsharing Issue  | Boolean  | True if feedback tokens from second endpoint indicate stream had an app sharing issue, False otherwise.    | |<!-- UI confirm -->
|**Audio Signal**|||
| First Echo Event Causes  | Flags  | Flags that indicate the reasons the DeviceEchoEvent was raised on the first endpoint. There may be multiple flags for a single stream. Flags include: <br/> BAD_TIMESTAMP - audio sample timestamps from capture or render device used were poor quality <br/> POSTAEC_ECHO - high level of echo remained after echo cancellation <br/> MIC_CLIPPING - signal level from capture device had significant instances of maximum signal level <br/> EVENT_ANLP - audio samples from capture contain high noise. <br/> **Example value:** BAD_TIMESTAMP | &bull; This was a non-audio stream <br/>&bull; No event causes were reported by the first endpoint  |
| Second Echo Event Causes  | Flags  | Flags that indicate the reasons the DeviceEchoEvent was raised on the second endpoint. There may be multiple flags for a single stream. Flags include: <br/> BAD_TIMESTAMP - audio sample timestamps from capture or render device used were poor quality <br/> POSTAEC_ECHO - high level of echo remained after echo cancellation <br/> MIC_CLIPPING - signal level from capture device had significant instances of maximum signal level <br/> EVENT_ANLP - audio samples from capture contain high noise. <br/> **Example value:** BAD_TIMESTAMP   | &bull; This was a non-audio stream <br/>&bull; No event causes were reported by the first endpoint |
| First Echo Percent Mic In  | Range (percentage)  | Percentage of time when echo is detected in the audio from the capture or microphone device prior to echo cancellation by the first endpoint. Values grouped by range.  <br/> **Example value:** 068: [5 - 10)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Echo Percent Mic In  | Range (percentage)  | Percentage of time when echo is detected in the audio from the capture or microphone device prior to echo cancellation by the second endpoint. Values grouped by range. <br/> **Example value:** 068: [5 - 10) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by second endpoint |
| First Echo Percent Send  | Range (percentage)  | Percentage of time when echo is detected in the audio from the capture or microphone device after echo cancellation by the first endpoint. Values grouped by range. <br/> **Example value:** 068: [5 - 10)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Echo Percent Send  | Range (percentage)  | Percentage of time when echo is detected in the audio from the capture or microphone device after echo cancellation by the second endpoint. Values grouped by range. <br/> **Example value:** 068: [5 - 10) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Send Signal Level  | Range (dB decibels)  | Average energy level of sent audio for audio classified as mono speech, or left channel of stereo speech by the first endpoint. Values grouped by range. <br/> **Example value:** 055: [-15 - -10) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Send Signal Level  | Range (dB decibels)  | Average energy level of sent audio for audio classified as mono speech, or left channel of stereo speech by the second endpoint. Values grouped by range. <br/> **Example value:** 055: [-15 - -10) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Recieved Signal Level  | Range (dB decibels)  | Average energy level of received audio for audio classified as mono speech, or left channel of stereo speech by the first endpoint. Values grouped by range. <br/> **Example value:** 056: [-10 - -5)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Recieved Signal Level  | Range (dB decibels)  | Average energy level of received audio for audio classified as mono speech, or left channel of stereo speech by the second endpoint. Values grouped by range. <br/> **Example value:** 056: [-10 - -5) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Send Noise Level  | Range (dB decibels)  | Average energy level of sent audio for audio classified as mono noise or left channel of stereo noise by the first endpoint. Values grouped by range. <br/> **Example value:** 048: [-50 - -45)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Send Noise Level  | Range (dB decibels)  | Average energy level of sent audio for audio classified as mono noise or left channel of stereo noise by the second endpoint. Values grouped by range. <br/> **Example value:** 048: [-50 - -45)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Recieved Noise Level  | Range (dB decibels)  | Average energy level of received audio for audio classified as mono noise or left channel of stereo noise by the first endpoint. Values grouped by range. <br/> **Example value:** 048: [-50 - -45)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Recieved Noise Level  | Range (dB decibels)  | Average energy level of received audio for audio classified as mono noise or left channel of stereo noise by the second endpoint. Values grouped by range. <br/> **Example value:** 048: [-50 - -45)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
|First Initial Signal Level RMS |<!-- gaps-->||
| Second Initial Signal Level RMS ||
| First RxAGC Signal Level |||
| Second RxAGC Signal Level |||
| First RxAGC Noise Level|||
| Second RxAGC Noise Level|||
| First Render Loopback Signal Level |||
| Second Render Loopback Signal Level |||
|**Client Event** |||
| First Network Send Quality Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the network was causing poor quality of the audio sent. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02)   | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the first endpoint|
| Second Network Send Quality Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the network was causing poor quality of the audio sent. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Network Receive Quality Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the network was causing poor quality of the audio received. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Network Receive Quality Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the network was causing poor quality of the audio received. Values grouped by range. <br/> **Example value:** 015: [0.01 - 0.02)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First CPU Insufficient Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the CPU resources available were insufficient and caused poor quality of the audio sent and received. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the first endpoint |
| Second CPU Insufficient Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the CPU resources available were insufficient and caused poor quality of the audio sent and received. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Half Duplex AEC Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected issues and operated the acoustic echo canceler in half-duplex mode, which impacted the ability to have real-time two-way communication. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Half Duplex AEC Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected issues and operated the acoustic echo canceler in half-duplex mode, which impacted the ability to have real-time two-way communication. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Render Not Functioning Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the render device was not working properly. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint  |
| Second Device Render Not Functioning Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the render device was not working properly. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Capture Not Functioning Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected the capture device was not working properly. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint  |
| Second Device Capture Not Functioning Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected the capture device was not working properly. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Glitches Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected glitches or gaps in the audio played or captured that caused poor quality of the audio being sent or received. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint  |
| Second Device Glitches Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected glitches or gaps in the audio played or captured that caused poor quality of the audio being sent or received. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Low SNR Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected low speech to noise level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the first endpoint  |
| Second Device Low SNR Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected low speech to noise level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Low Speech Level Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected low speech level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Low Speech Level Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected low speech level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Clipping Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected clipping in the captured audio that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the first endpoint  |
| Second Device Clipping Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected clipping in the captured audio that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Echo Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected echo that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Echo Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected echo that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Near End To Echo Ratio Event Ratio  | Range (ratio)  | Fraction of the call that the first endpoint detected a ratio of the near end signal level to the echo level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint|
| Second Device Near End To Echo Ratio Event Ratio  | Range (ratio)  | Fraction of the call that the second endpoint detected a ratio of the near end signal level to the echo level that caused poor quality of the audio being sent. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Render Zero Volume Event Ratio  | Range (ratio)  | Fraction of the call that first endpoint detected device render volume is set to 0. Values grouped by range.  <br/> **Example value:** 016: [0.02 - 0.03) | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Render Zero Volume Event Ratio  | Range (ratio)  | Fraction of the call that second endpoint detected device render volume is set to 0. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Render Mute Event Ratio  | Range (ratio)  | Fraction of the call that first endpoint detected device render is muted. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)   | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Render Mute Event Ratio  | Range (ratio)  | Fraction of the call that second endpoint detected device render is muted. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03) | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint  |
| First Device Multiple Endpoints Event Count  | Range (ratio)  | Number of times during the call that the first endpoint detected multiple endpoints in the same room or acoustic environment. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Multiple Endpoints Event Count  | Range (ratio)  | Number of times during the call that the second endpoint detected multiple endpoints in the same room or acoustic environment. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
| First Device Howling Event Count  | Range (ratio)  | Number of times during the call that the first endpoint detected two or more endpoints in the same room or acoustic environment that caused poor quality audio in the form of howling or screeching audio. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; This was a non-audio stream <br/>&bull; Data was not reported by first endpoint |
| Second Device Howling Event Count  | Range (ratio)  | Number of times during the call that the second endpoint detected two or more endpoints in the same room or acoustic environment that caused poor quality audio in the form of howling or screeching audio. Values grouped by range. <br/> **Example value:** 016: [0.02 - 0.03)  | &bull; Indicates a non-audio stream <br/>&bull; Data was not reported by the second endpoint |
|**Call Diagnostic**|||
| Error Report Sender  | String  | Indicates which endpoint sent the call error report for the stream. This report contains additional telemetry and may indicate call setup or call drop issue with the call. <br/> **Example value:** First | &bull; Indicates no call error report was sent.  |
| Is Media Error  | String  | Indicates if the call error report for the stream was a media level error or not. This report contains additional telemetry and may indicate call setup or call drop issue with the call.    | &bull; Indicates no call error report was sent. |
| Media Failure Type  | Enumeration <br/>**Possible values:** <br/>&bull; Midcall <br/>&bull;  CallSetup <br/>&bull;  NotMediaFailure. | The type of media failure associated with the stream.   | &bull; Indicates no call error report was sent.   |
| Call Classification|<!-- gaps -->||
| Classification Reason|||
| Test Call Type|||
|**Session**|||
| RTP RTCP Mux  | Boolean  | True indicates that RTP and RTCP were multiplexed on the same ports. False otherwise.    | <br/>&bull; Data was not reported by the endpoint  |
| Stun Version  | Integer  | Version of STUN protocol used for establishing the call.  | <br/>&bull; Data was not reported by the endpoint <br/> **Example value:** 2  |
| Media Relay  | String  | IP address for Media relay(s) used for the session. May report a pair of relay separated by a '+' if the stream. <br/> **Example value:** "13.107.8.2 + 13.107.8.2"  | &bull; This data was not reported by the endpoints  |
| Is Anonymous Join Session  | Boolean  | True if user joining conference was anonymous, False otherwise.   | &bull; No data to determine if user was joined anonymously or not   |
| Has Media Diagnostic Blob  | Boolean  | True if session had media diagnostics data, False otherwise.   | &bull; Some signaling data was not collected for this stream   |
| Call Setup Failure Reason  | Enumeration  | Classification of why media connection could not be established for a call. <br/>**Possible values:** <br/> **Missing FW Deep Packet Inspection Exemption Rule** - indicates that network equipment along the path likely prevented the media path from being established due to deep packet inspection rules. This may be due to proxy or firewall rules not being correctly configured. <br/> **Missing FW IP Block Exemption Rule** - indicates that network equipment along the path likely prevented the media path from being established to the Office 365 network. This may be due to proxy or firewall rules not being correctly configured to allow access to IP addresses and ports used for Skype for Business traffic. <br/> **Other** - indicates the media path for the call could not be established but the root cause could not be classified. <br/> Not Media Failure - indicates no issue was detected with the establishment of the media path.  | &bull; Call set up failed due to an unknown media issue  |
|**DNS**|||
| Used DNS Resolve Cache  | Boolean  | True if endpoint used DNS cache to resolve media relay address, False otherwise.    | <br/>&bull; This data was not reported by the endpoint    |
|**UserData**|||
| First User ObjectId|||
| Second User ObjectId|||
| First MAC Address|||
| Second MAC Address|||
| First Sip Uri|||
| Second Sip Uri|||
| First Phone Number|||
| Second Phone Number|||
| First UPN|||
| Second UPN|||
| First Feedback Text|||
| Second Feedback Text|||
| First Client Endpoint Name|||
| Second Client Endpoint Name|||
| First Endpoint Product Name|||
| Second Endpoint Product Name|||
| First UserType|||
| Second UserType|||
|**Datapair**|||
| Network Connection Detail Pair  | Enumerated pair <br/>**Possible values:** <br/> wifi : wifi <br/> wifi : wired <br/> Wired : wifi <br/> Wired : Wired <br/> MobileBB : MobileBB <br/> MobileBB : Other <br/> MobileBB : Tunnel <br/> MobileBB : wifi <br/> MobileBB : Wired <br/> Other : Other <br/> Other : wifi <br/> Other : Wired <br/> Tunnel : Tunnel <br/> Tunnel : wifi <br/> Tunnel : Wired <br/> : MobileBB <br/> : Other <br/> : Tunnel <br/> : wifi <br/> : Wired <br/> :  | Pair of network connection detail for the first and second endpoint.  | &bull; Endpoint network connectivity type was unknown. This may happen if the call could not be established.   |
| User Agent Category Pair  | Enumerated pair  | Pair of User Agent Category for first and second endpoint. <br/> **Example value:** AV-MCU : OC  | &bull; Endpoint user agent was not a known type  |
| Is Server Pair  | Enumerated pair <br/>**Possible values:** Client : Client <br/> Client : Server <br/> Server : Server  | Pair of identification of first and second endpoints as either Client or Server.  | no Blank values   |
| Connectivity Ice Pair  | Enumerated pair <br/>**Possible values:** <br/> DIRECT : DIRECT <br/> DIRECT : FAILED <br/> DIRECT : HTTP <br/> FAILED : FAILED <br/> FAILED : RELAY <br/> HTTP : RELAY <br/> : <br/> : DIRECT <br/> : FAILED <br/> : HTTP <br/> : RELAY | Pair of type of ICE connectivity used by each endpoint.   | &bull; ICE connectivity used by endpoint was not known or reported   |
| OS Pair  | Enumerated pair  | Pair of the OS name and version for first and second endpoint. <br/> **Example value:** Windows 10 : Windows 10  | &bull; OS name could not be parsed or was not reported by endpoint  |
| Tenant Id Pair  | Enumerated pair  | Pair of the tenant ids for first and second endpoint. <br/> **Example value:** 00000000 - 0000 - 0000 - 0000 - 000000000000 : 00000000 - 0000 - 0000 - 0000 - 000000000000  |  &bull; The tenant identifier could not be determined. This may happen if endpoint is signed in to an on-premise Skype for Business Server deployment.  |
| Building Name Pair  | Enumerated pair  | Pair of the building name for the first and second endpoint.  | &bull; The building name for an endpoint could not be determined. This could be because the endpoint is located outside the corporate network, or is accessing the network from a site without a subnet mapping. <br/> **Example value:** Main Building : Branch Site Building |
| Inside Corp Pair  | Enumerated pair <br/>**Possible values:** <br/> Inside : Inside <br/> Inside : Outside <br/> Outside : Outside | Pair showing if the endpoints were located inside or outside the corporate network based on the subnet mapping.   |   |
| Scenario Pair  | Enumerated pair  | Pair showing if the endpoints were located inside or outside the corporate network based on the subnet mapping and the network connection detail. <br/> **Note:** The pairs are separated by '--'. <br/> **Example value:** Client-Inside--Client-Inside-wifi  | &bull; The network connectivity type was unknown for either or both endpoints.  |
||||

### Notes on dimension data type/units

#### Boolean

Boolean values are always either True or False. In some cases, True can also be represented as 1 and False can be represented as 0.

#### Range

Dimensions that are provided as range or group of values are shown using the following format:

 _\<sort order string\> [\<lower bound inclusive\> - \<upper bound exclusive\>_

For example, the Duration (Minutes) dimension represents the call duration in seconds with the value reported as a range of values.

|Duration (Minutes) |How to interpret |
|:--- |:--- |
|062: [0 - 0) |Stream duration = 0 minutes |
|064: [1 - 2) |1 minute < = stream duration < 2 minutes |
|065: [2 - 3) |2 minutes < = stream duration < 3 minutes |
|066: [3 - 4) |3 minutes < = stream duration < 4 minutes |
|  | |

The \<sort order string> is used to control the sort order when presenting the data and can be used for filtering. For example, a filter on Duration (Minutes) < "065", would show streams with duration less than 2 minutes (The leading '0' is needed for the filter to work as expected).

> [!NOTE]
> The actual value of the sort order string isn't significant.

#### Enumeration strings

Strings used by CQD are often derived from data files, and these can be nearly any combination of character within the allowed length. Some dimensions look like strings, but since they can only be one of a short list of predefined values, they are enumerations and not true strings. Some enumeratipons strings are also used in pairs.

#### Enumeration pair

Dimensions that are provided as an enumeration pair are shown using the following format:

 _\<enumeration value from one end point\> : \<enumeration value from the other endpoint\>_

The ordering of the enumeration values is consistent but doesn't reflect ordering of the first or second endpoints.

For example, the Network Connection Detail Pair shows the Network Connection Detail values for the two endpoints:

|Network Connection Detail Pair |How to interpret |
|:--- |:--- |
|Wired : Wired |First and second endpoints both used wired ethernet connections. |
|Wired : wifi |First endpoint used wired ethernet connection and second endpoint used Wi-Fi connection, or the second endpoint used wired ethernet connection and first endpoint used Wi-Fi connection. |
|: wifi |First endpoint used a WiFi connection and the network connection used by the second endpoint is unknown, or the second endpoint used a WiFi connection and the network connection used by the first endpoint is unknown. |
| | |

#### Blank values

The table above lists possible reasons why a dimension may be blank. Many dimensions and measurements will be blank if the QoE Record Available dimension is false. This typically occurs when the call wasn't successfully established.

## Measurements

Many Measurement values can also be used as filters. The following table lists the measurements currently available in CQD, shown in the order listed in the Query Editor:

|Measure Name |Units |Description |
|:--- |:--- |:--- |
|Total Stream Count |Number of streams |Number media streams regardless of type of media. |
| Total CDR Available Stream Count |<!-- gap -->||
|Total Media Failed Stream Count |Number of streams |Number of streams where either media path could not be established or did not terminate normally. |
|Total Call Setup Failed Stream Count |Number of streams |Number of streams where media path could not be established between the endpoints at the start of the call. |
|Total Call Dropped Stream Count |Number of streams |Number of streams where media path did not terminate normally. |
|Total Media Succeeded Stream Count |Number of streams |Number of streams where media path was established and terminated normally. |
|Total Call Setup Succeeded Stream Count |number of streams |Number of streams where media path could be established between the endpoints at the start of the call.|
|Total Call Setup Failure Percentage |Percentage |Percentage of all streams where media path could not be established between the endpoints at the start of the call. |
|Total Call Dropped Failure Percentage |Percentage |Percentage of successfully established streams where media path did not terminate normally. | Total Short Call Count
|Total Answer Seizure Ratio |Ratio |Ratio of calls with duration less than 5 seconds over the total number of calls. |
|Total Short Call Percentage |Percentage |Percentage of total calls less than 1 minute long. |
|Total Media Failure Percentage |Percentage |Percentage of all streams where either media path could not be established or did not terminate normally. |
|Media Failed Due To Firewall DPI Stream Count |Number of streams |Number of streams that failed to be established due to network equipment blocking access due to deep packet inspection not allowing Skype for Business traffic. These failures typically indicate a proxy, firewall or other network security device is not correctly configured to access the IP address and ports used by Skype for Business in Office 365. |
|Firewall DPI Media Failure Percentage |Percentage |Percentage of streams that failed to be established due to network equipment blocking access due to deep packet inspection not allowing Skype for Business traffic. These failures typically indicate a proxy, firewall or other network security device is not correctly configured to access the IP address and ports used by Skype for Business in Office 365. |
|Media Failed Due To Firewall IP Blocked Stream Count |Number of streams |Number of streams that failed to be established due to network equipment blocking access to Skype for Business servers. These failures typically indicate a proxy, firewall or other network security device is not correctly configured to access the IP address and ports used by Skype for Business in Office 365. |
|Firewall IP Blocked Media Failure Percentage |Percentage |Percentage of streams that failed to be established because network equipment blocked access to Skype for Business servers. These failures typically indicate a proxy, firewall, or other network security device is not correctly configured to access the IP address and ports used by Skype for Business in Office 365. |
| Media Failed Due To Other Stream Count|<!-- gaps -->||
| Other Media Failure Percentage|||
| Total CDR Available Call Count|||
| Total Media Failed Call Count|||
|Audio Stream Count |Number of streams |Number of audio streams. |
|Audio Poor Stream Count |Number of streams |Number of audio streams classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
 |Audio Good Stream Count |Number of streams |Number of audio streams classified as good based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Unclassified Stream Count |Number of streams |Number of audio streams that did not have sufficient data to be classified as good or poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Poor Percentage |Percentage |Percentage of all audio streams that were classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio OnePercent PacketLoss Count |Number of streams |Number of audio streams with packet loss greater than 1%. |
|Audio OnePercent PacketLoss Percentage |Percentage |Percentage of all audio streams with packet loss greater than 1%. |
|Audio Poor Due To Jitter Count |Number of streams |Number of audio streams where the jitter metric exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Poor Due To PacketLoss Count |Number of streams |Number of audio streams where the packet loss metric exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md) |
|Audio Poor Due To Degradation Count |Number of streams |Number of audio streams where the degradation metric exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Poor Due To RoundTrip Count |Number of streams |Number of audio streams where the round trip exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Poor Due To ConcealedRatio Count |Number of streams |Number of audio streams where the concealed ratio exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio SLA Good Call Count |Number of calls |Number of audio calls within scope of the Skype for Business Voice Quality SLA ([Volume Licensing for Microsoft Products and Online Services](https://aka.ms/voicequalitysla)) classified as meeting the network performance targets. |
|Audio SLA Poor Call Count |Number of calls |Number of audio calls within scope of the Skype for Business Voice Quality SLA ([Volume Licensing for Microsoft Products and Online Services](https://aka.ms/voicequalitysla)) classified as not meeting the network performance targets. |
|Audio SLA Call Count |Number of calls |Number of audio calls within scope of the Skype for Business Voice Quality SLA ([Volume Licensing for Microsoft Products and Online Services](https://aka.ms/voicequalitysla)). |
|Audio SLA Good Call Percentage |Percentage |Percentage of audio calls within scope of the Skype for Business Voice Quality SLA ([Volume Licensing for Microsoft Products and Online Services](https://aka.ms/voicequalitysla)) that were classified as meeting the network performance targets. |
|Audio Good Call Stream Count |Number of streams |Number of audio streams where both audio streams in the call (call-leg) are not classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Poor Call Stream Count |Number of streams |Number of audio streams where at least one audio stream in the call (call-leg) was classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Audio Unclassified Call Stream Count |Number of streams |Number of audio streams where both audio streams in the call (call-leg) could not be classified due to missing network metrics. |
|Audio Poor Call Level Percentage |Percentage |Percentage of all audio streams where at least one audio stream in the call (call-leg) was classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
| Audio Call Count |<!-- gaps -->||
| Audio Poor Call Count|||
| Audio Good Call Count |||
| Audio Unclassified Call Count |||
| Audio Poor Call Percentage |||
|AppSharing Stream Count |Number of streams |Number of RDP-based application sharing streams. |
|AppSharing Poor Due To SpoiledTilePercentTotal Count |Number of streams |Number of application sharing streams where the spoiled tile percent total metric exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Poor Due To RelativeOneWayAverage Count |Number of streams |Number of application sharing streams where the spoiled tile percent total metric exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Poor Due To RDPTileProcessingLatencyAverage Count |Number of streams |Number of application sharing streams where the RDP tile processing latency average exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Poor Stream Count |Number of streams |Number of application sharing streams classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Good Stream Count |Number of streams |Number of application sharing streams classified as good based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Unclassified Stream Count |Number of streams |Number of application sharing streams that did not have sufficient data to be classified as good or poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|AppSharing Poor Percentage |Percentage |Percentage of total application sharing streams that were classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Stream Count |Number of streams |Number of video streams. |
|Video Poor Due To VideoPostFecplr Count |Number of streams |Number of video streams where the Video Post Fec plr exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Poor Due To VideoLocalFrameLossPercentageAvg Count |Number of streams |Number of video streams where the Video Local Frame Loss Percentage Avg exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Poor Due To VideoFrameRateAvg Count |Number of streams |Number of Video streams where the Video Frame Rate Avg exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Poor Stream Count |Number of streams |Number of video streams classified as poor based on network metrics listed here [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Good Stream Count |Number of streams |Number of video streams classified as good based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Unclassified Stream Count |Number of streams |Number of video streams that did not have sufficient data to be classified as good or poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Video Poor Percentage|Percentage |Percentage of total video streams that were classified as poor based on network metrics listed here [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Stream Count |Number of streams |Number of video-based-screen sharing streams. |
|VBSS Poor Due To VideoPostFecplr Count |Number of streams |Number of video-based-screen-sharing streams where the Video Post Fec plr exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Poor Due To VideoLocalFrameLossPercentageAvg Count |Number of streams |Number of video-based-screen-sharing streams where the Video Local Frame Loss Percentage Avg exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Poor Due To VideoFrameRateAvg Count |Number of streams |Number of video-based-screen-sharing streams where the Video Frame Rate Avg exceeds thresholds listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Poor Stream Count |Number of streams |Number of video-based-screen-sharing streams classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Good Stream Count |Number of streams |Number of video-based-screen-sharing streams classified as good based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Unclassified Stream Count |Number of streams |Number of video-based-screen-sharing streams that did not have sufficient data to be classified as good or poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|VBSS Poor Percentage |Percentage |Percentage of total video-based-screen-sharing streams that classified as poor based on network metrics listed here: [Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md). |
|Avg Call Duration |Seconds |Average duration of streams in seconds. |
|First Feedback Rating Avg |User rating (1-5) |Average rating of streams reported by the user using the first endpoint. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|Second Feedback Rating Avg |User rating (1-5) |Average rating of streams reported by the user using the second endpoint. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|First Feedback Rating Count |Number of rated streams |Number of streams rated by the user using the first endpoint. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|Second Feedback Rating Count |Number of rated streams |Number of streams rated by the user using the second endpoint. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|First Feedback Rating Poor Count |Number of rated streams |Number of streams rated by the user using the first endpoint as either 1 or 2. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|Second Feedback Rating Poor Count |Number of rated streams |Number of streams rated by the user using the second endpoint as either 1 or 2. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|First Feedback Rating Poor Percentage |Number of rated streams |Percentage of all rated streams that were rated by the user using the first endpoint as either 1 or 2. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|Second Feedback Rating Poor Percentage |Number of rated streams |Percentage of all rated streams that were rated by the user using the second endpoint as either 1 or 2. Calls are rated from 1-5 and the rating is applied to all streams of the call. |
|First Feedback Token Audio Issue Count |Number rated streams |Number of streams where user using the first endpoint indicated an issue with audio. |
|Second Feedback Token Audio Issue Count |Number rated streams |Number of streams where user using the second endpoint indicated an issue with audio. |
|First Feedback Token Video Issue Count |Number of rated streams |Number of streams where user using the first endpoint indicated an issue with video. |
|Second Feedback Token Video Issue Count |Number of rated streams |Number of streams where user using the second endpoint indicated an issue with video. |
|Avg First Echo Percent Mic In |Percentage |Average percentage of time during the stream that the first endpoints detected echo in the audio from the capture or microphone device prior to echo cancellation. |
|Avg Second Echo Percent Mic In |Percentage |Average percentage of time during the stream that the second endpoints detected echo in the audio from the capture or microphone device prior to echo cancellation. |
|Avg First Echo Percent Send |Percentage |Average percentage of time during the stream that the first endpoints detected echo in the audio from the capture or microphone device after echo cancellation. |
|Avg Second Echo Percent Send |Percentage |Average percentage of time during the stream that the second endpoints detected echo in the audio from the capture or microphone device after echo cancellation. |
| Avg First Initial Signal Level RMS|<!-- gaps -->||
| Avg Second Initial Signal Level RMS|||
| Avg First RxAGC Signal Level|||
| Avg Second RxAGC Signal Level|||
| Avg First RxAGC Noise Level|||
| Avg Second RxAGC Noise Level|||
| Avg First Render Loopback Signal Level|||
| Avg Second Render Loopback Signal Level|||
|Avg First Audio Send Signal Level |Decibels |Average energy level of sent audio for audio classified as mono speech, or left channel of stereo speech sent by first endpoints. |
|Avg Second Audio Send Signal Level |Decibels |Average energy level of sent audio for audio classified as mono speech, or left channel of stereo speech sent by second endpoints. |
|Avg First Audio Recieved Signal Level |Decibels |Average energy level of received audio for audio classified as mono speech, or left channel of stereo speech by the first endpoints. |
|Avg Second Audio Recieved Signal Level |Decibels |Average energy level of received audio for audio classified as mono speech, or left channel of stereo speech by the second endpoints. |
|Avg First Audio Send Noise Level |Decibels |Average energy level of sent audio for audio classified as mono noise or left channel of stereo noise by the first endpoints. |
|Avg Second Audio Send Noise Level |Decibels |Average energy level of sent audio for audio classified as mono noise or left channel of stereo noise by the second endpoints. |
|Avg First Audio Recieved Noise Level |Decibels |Average energy level of received audio for audio classified as mono noise or left channel of stereo noise by the first endpoints. |
|Avg Second Audio Recieved Noise Level |Decibels |Average energy level of received audio for audio classified as mono noise or left channel of stereo noise by the second endpoints. |
|First Audio Echo BAD_TIMESTAMP Count |Number of streams |Number of streams where the echo was caused by bad device timestamps from the first endpoints that limited echo cancellation in audio sent. |
|First Audio Echo POSTAEC_ECHO Count |Number of streams |Number of streams where the high echo was detected after echo cancellation for audio sent by the first endpoints. |
|First Audio Echo EVENT_ANLP Count |Number of streams |Number of streams where the first endpoints detected noise in the captured audio that limited echo cancellation in audio sent. |
|First Audio Echo EVENT_DNLP Count |Number of streams |Number of streams where the first endpoints detected noise in the captured audio that limited echo cancellation in audio sent. |
|First Audio Echo MIC_CLIPPING Count |Number of streams |Number of streams where the first endpoints detected clipping in the captured audio that limited echo cancellation in audio sent. |
|First Audio Echo BAD_STATE Count |Number of streams |Number of streams where the first endpoints detected issues with the internal state that limited echo cancellation in audio sent. |
|Second Audio Echo BAD_TIMESTAMP Count |Number of streams |Number of streams where the echo was caused by bad device timestamps from the second endpoints that limited echo cancellation in audio sent. |
|Second Audio Echo POSTAEC_ECHO Count |Number of streams |Number of streams where the high echo was detected after echo cancellation for audio sent by the second endpoints. |
|Second Audio Echo EVENT_ANLP Count |Number of streams |Number of streams where the second endpoints detected noise in the captured audio that limited echo cancellation in audio sent. |
|Second Audio Echo EVENT_DNLP Count |Number of streams |Number of streams where the second endpoints detected noise in the captured audio that limited echo cancellation in audio sent. |
|Second Audio Echo MIC_CLIPPING Count |Number of streams |Number of streams where the second endpoints detected clipping in the captured audio that limited echo cancellation in audio sent. |
|Second Audio Echo BAD_STATE Count |Number of streams |Number of streams where the second endpoints detected issues with the internal state that limited echo cancellation in audio sent. |
|Avg Audio Degradation |Mean Opinion Score (0-5) |Average Network Mean Opinion Score degradation for streams. Represents how much the network loss and jitter have impacted the quality of received audio. |
|Avg Jitter |Milliseconds |Average network jitter for streams in milliseconds. |
|Avg Jitter Max |Milliseconds |Maximum network jitter for streams in milliseconds. |
|Avg Packet Loss Rate |Ratio |Average of average percentage of packets lost computed using 5 second interval for streams. 0.1 indicates 10% packet loss. |
|Avg Packet Loss Rate Max |Ratio |Average of maximum percentage of packets lost during any 5 second interval for streams. 0.1 indicates 10% packet loss. |
| Avg Send Listen MOS |<!-- gaps -->||
|Avg Overall Avg Network MOS |Mean Opinion Score (0-5) |Average or average network Mean Opinion Score for streams. Represents the average predicted quality of received audio factoring in network loss, jitter, and codec. |
|Avg Ratio Concealed Samples |Ratio |Average of average ratio of the number of audio frames with samples generated by packet loss concealment to the total number of audio frames for streams. 0.1 indicates 10% of frames contained concealed samples. |
| Avg Conceal Ratio Max|<!-- gaps -->||
|Avg Ratio Stretched Samples |Ratio |Average of average ratio of the number of audio frames with samples that have been stretched to compensate for jitter or loss to the total number of audio frames for streams. 0.1 indicates 10% audio frames contained stretched samples. |
| Avg Healer Packet Drop Ratio|||
| Avg Healer FEC Packet Used Ratio|||
|Avg Round Trip |Milliseconds |Average of average network propagation round-trip time computed as specified in RFC3550 in milliseconds for streams. |
|Avg Round Trip Max |Milliseconds |Average of maximum network propagation round-trip time computed as specified in RFC3550 in milliseconds for streams. |
 Avg Packet Utilization|||
|Avg Network Jitter |Milliseconds |Average of average network jitter in milliseconds computed over 20 second windows during the session for streams. |
| Avg Network Jitter Max|<!-- gap -->||
| Avg Network Jitter Min|||
| Avg Jitter Buffer Size |||
| Avg Jitter Buffer Size Max|||
| Avg Jitter Buffer Size Min|||
| Avg Relative OneWay |||
| Avg Relative OneWay Gap Occurrences|||
| Avg Relative OneWay Gap Density|||
| Avg Relative OneWay Gap Duration|||
|Avg Audio Post FECPLR |Ratio |Average of packet loss rate after FEC has been applied for aggregated across all audio streams and codecs for streams. |
|Avg Video Post FECPLR |Ratio |Average of packet loss rate after FEC has been applied for aggregated across all video streams and codecs for streams. |
|Avg Video Local Frame Loss Percentage |Percentage |Average percentage of video frames lost as displayed to the user for streams. This includes frames recovered from network losses. |
 |Avg Video Recieved Frame Rate Average |Frames per second |Average of average frames per second received for all video streams computed over the duration of the session for streams. |
 |Avg Video Low Frame Rate Call Percent |Percentage |Average of percentage of time of the call where frame rate is less than 7.5 frames per second for streams. |
|Avg Video Packet Loss Rate |Ratio |Average of average fraction of packets lost, as specified in [RFC3550](https://tools.ietf.org/html/rfc3550), computed over the duration of the session for streams. |
|Avg Video Frame Rate |Frames per second |Average frames per second received for a video stream, computed over the duration of the session. Values grouped by range. |
|Avg Video Dynamic Capability Percent |Milliseconds |Average of percentage of time that the client is running < 70% expected video processing capability for this type of CPU for streams. |
|Avg AppSharing Spoiled Tile Percent Total |Milliseconds |Average of percentage of tiles which are discarded instead of being sent to a remote peer (for example, from the MCU to a viewer) for streams. Discarded tiles may be caused by bandwidth restrictions between client and server. |
|Avg AppSharing Relative OneWay |Seconds |Average of average relative one-way delay between the endpoints in seconds for application sharing streams. |
|Avg AppSharing RDP Tile Processing Latency |Milliseconds |Average of average latency in milliseconds processing tiles on the RDP Stack at the conferencing server for streams. |
|Avg First Device Capture Not Functioning Event Ratio |Ratio |Average of the fraction of the call that the first endpoint detected the capture device was not working properly. |
|Avg Second Device Capture Not Functioning Event Ratio |Ratio |Average of the fraction of the call that the second endpoint detected the capture device was not working properly. |
|Avg First Device Render Not Functioning Event Ratio |Ratio |Average of the fraction of the call that the first endpoint detected the render device was not working properly. |
|Avg Second Device Render Not Functioning Event Ratio |Ratio |Average of the fraction of the call that the second endpoint detected the render device was not working properly. |
|Avg First Mic Glitch Rate|||
| Avg Second Mic Glitch Rate|||
| Avg First Speaker Glitch Rate|||
| Avg Second Speaker Glitch Rate|||
| First User Count|||
| Second User Count|||
| Avg First Device Glitches Event Ratio|||
| Avg Second Device Glitches Event Ratio|||
| First Device Glitches Event Count|||
| Second Device Glitches Event Count|||
||||

## Filters

Many Dimension and Measurement values can also be used as filters. You can use filters in your query to eliminate information in the same way you'd select A Dimension or Measurement to add or include information in the query.

## Related topics

[Set up Skype for Business Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Call Analytics and Call Quality Dashboard](difference-between-call-analytics-and-call-quality-dashboard.md)
