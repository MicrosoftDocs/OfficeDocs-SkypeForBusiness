---
title: "List of CDR tables in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 031843fd-c7ff-4534-9b02-8847aad70807
description: "The call detail recording (CDR) database schema consists of the following tables."
---

# List of CDR tables in Skype for Business Server 2015
 
The call detail recording (CDR) database schema consists of the following tables. 
  
## Static Tables

|**Table**|**Description**|
|:-----|:-----|
|[CallPriorities table in Skype for Business Server 2015](callpriorities.md) <br/> |Stores the list of possible call priorities, such as emergency, urgent, normal, non-urgent, and more.  <br/> |
|[ConferenceJoinTimeThresholds table in Skype for Business Server 2015](conferencejointimethresholds.md) <br/> |Stores the classification boundaries used by the Conference Join Time Summary Report.  <br/> |
|[DeRegisterType table in Skype for Business Server 2015](deregistertype.md) <br/> |Stores the list of possible user de-register reasons, such as "client initiated," "registration expired," "client crash," and more.  <br/> |
|[MediaList table](medialist.md) <br/> |Stores the list of media types that can generate entries in the database (for example, IM, audio, video, and file transfer).  <br/> |
|[PurgeSettings table](purgesettings.md) <br/> |Stores information that specifies if (and when) outdated call detail records will automatically be deleted from the CDR database.  <br/> |
|[Roles table](roles.md) <br/> |Stores the list of possible conference roles (for example, attendee and presenter).  <br/> |
|[SIPResponseMetaData table](sipresponsemetadata.md) <br/> |Stores a list of SIP response codes and the classification and definition of each of those codes.  <br/> |
   
## Supporting Tables

|**Table**|**Description**|
|:-----|:-----|
|[ClientVersions table in Skype for Business Server 2015](clientversions.md) <br/> |Stores the clients (both client type and version number) of each client involved in a call with information captured in this database.  <br/> |
|[ConferenceUris table in Skype for Business Server 2015](conferenceuris.md) <br/> |Stores a list of ConferenceURIs that are used in conference related calls.  <br/> |
|[ContentTypes table in Skype for Business Server 2015](contenttypes.md) <br/> |Stores a list of Session Initiation Protocol (SIP) content types that are used in both peer-to-peer calls and conference calls.  <br/> |
|[Devices table in Skype for Business Server 2015](devices.md) <br/> |Stores a list of devices, including their manufacturer, hardware version, and MAC address.  <br/> |
|[Dialogs table in Skype for Business Server 2015](dialogs.md) <br/> |Stores information about the Dialog ID for each session in the database.  <br/> |
|[EdgeServers table in Skype for Business Server 2015](edgeservers.md) <br/> |Stores a list of Edge Servers that are used for external calls.  <br/> |
|[Gateways table in Skype for Business Server 2015](gateways.md) <br/> |Stores a list of Gateways that are used for Voice over Internet Protocol (VoIP) calls.  <br/> |
|[HardwareVersions table in Skype for Business Server 2015](hardwareversions.md) <br/> |Stores a list of hardware versions of devices (desk phone).  <br/> |
|[Manufacturers table in Skype for Business Server 2015](manufacturers.md) <br/> |Stores a list of manufacturers of devices (desk phone).  <br/> |
|[Mcus table in Skype for Business Server 2015](mcus.md) <br/> |Stores information about the various A/V Conferencing Servers and their URIs.  <br/> |
|[MediationServers table](mediationservers.md) <br/> |Stores a list of Mediation Servers that are used for VoIP calls.  <br/> |
|[Phones table](phones.md) <br/> |Stores all the phone numbers used in VoIP calls that were archived or whose call details were recorded.  <br/> |
|[Pools table](pools.md) <br/> |Stores the names of the pool on which IM messages are captured.  <br/> |
|[Servers table](servers.md) <br/> |Stores the name of servers involved in calls.  <br/> |
|[Tenants table](tenants.md) <br/> |Stores the tenants supported by current deployment. There some build-in tenants for Enterprise user, Federated User, public IM connectivity user, and Anonymous users.  <br/> |
|[UserAgentDef table](useragentdef.md) <br/> |Maps user agent identifiers to the agent's descriptive names.  <br/> |
|[Users table](users.md) <br/> |Stores the user URIs of users who have participated in sessions recorded or archived in this database.  <br/> |
|[UserStatistics table](userstatistics.md) <br/> |Stores information about an individual user's usage of the system.  <br/> |
   
## Tables Specific to Conference CDR Records

|**Table**|**Description**|
|:-----|:-----|
|[Conferences table in Skype for Business Server 2015](conferences.md) <br/> |Stores information about all conferences that were archived or whose details were recorded, including ConferenceURI, and start and end time.  <br/> |
|[ConferenceSessionDetails table in Skype for Business Server 2015](conferencesessiondetails-0.md) <br/> |Stores information about every SIP-based conference session, including start and end time, user ID, response code, and diagnostic ID for each session.  <br/> |
|[FocusJoinsAndLeaves table in Skype for Business Server 2015](focusjoinsandleaves.md) <br/> |Stores information about conference joins and leaves, including users' role and client version.  <br/> |
|[McuJoinsAndLeaves table in Skype for Business Server 2015](mcujoinsandleaves.md) <br/> |Stores information about the A/V Conferencing Servers that are involved in a conference and the user join and leave times.  <br/> |
   
## Tables for Messages in IM Conferences

|**Table**|**Description**|
|:-----|:-----|
|[ConferenceMessageCount table in Skype for Business Server 2015](conferencemessagecount.md) <br/> |For each IM conference, stores the number of messages that were sent by each user.  <br/> |
|[IMReportSummary table in Skype for Business Server 2015](imreportsummary.md) <br/> |Provides an overall report on the instant messaging sessions held in an organization.  <br/> |
   
## Tables for Peer-to-Peer Sessions

|**Table**|**Description**|
|:-----|:-----|
|[SessionDetails table](sessiondetails.md) <br/> |Stores information about every peer-to-peer session, including start and end time, user ID, response code, and message count for each user.  <br/> |
|[FileTransfers table in Skype for Business Server 2015](filetransfers-0.md) <br/> |Stores information about file transfer sessions, including file name and result (accepted, rejected, or canceled).  <br/> |
|[Media table](media.md) <br/> |Stores information about the different media types involved in peer-to-peer sessions.  <br/> |
   
## Table for VoIP Call Details

|**Table**|**Description**|
|:-----|:-----|
|[VoipDetails table](voipdetails-0.md) <br/> |For each two-party VoIP/PSTN call, stores information about the call, such as the phone ID of VoIP phone, gateway used, and which party disconnected. Refers to the [SessionDetails table](sessiondetails.md) for call start/end times and response code. <br/> |
   
> [!NOTE]
> If one party on a call is a VoIP user or if a Mediation Server was involved in the call, a record will be created in this table. Information about VoIP/VoIP calls not involving a public switched telephone network (PSTN) phone is captured in the [SessionDetails table](sessiondetails.md). 
  
## Table for E9-1-1 Call Auditing

|**Table**|**Description**|
|:-----|:-----|
|[Locations table in Skype for Business Server 2015](locations.md) <br/> |For each emergency call, such as an Enhanced 9-1-1 (E9-1-1) call, stores location information about the call. Refers to the [SessionDetails table](sessiondetails.md) for call start/end times and response code. <br/> |
   
> [!NOTE]
> This table only contains the location blob for the E9-1-1 call. Refers to the SessionDetails table for other detailed information about the call. 
  
## Tables for Troubleshooting

|**Table**|**Description**|
|:-----|:-----|
|[Application table in Skype for Business Server 2015](application.md) <br/> |Stores information about various processes within Skype for Business Server 2015 that are involved in routing and connections.  <br/> |
|[CallType table in Skype for Business Server 2015](calltype.md) <br/> |Stores information about types of the call, such as, "audio", "Instant Messaging", "audio and video" and "application sharing".  <br/> |
|[ErrorCategory table in Skype for Business Server 2015](errorcategory.md) <br/> |Stores the friendly name for each Skype for Business Server 2015 diagnostic classification.  <br/> |
|[ErrorDef table in Skype for Business Server 2015](errordef.md) <br/> |Stores information about types of errors and their definitions.  <br/> |
|[ErrorReport table in Skype for Business Server 2015](errorreport.md) <br/> |Stores information about errors that have occurred.  <br/> |
|[ProgressReport table](progressreport.md) <br/> |Stores information about the progress reports of various steps involved in Skype for Business Server 2015 processes.  <br/> |
   
The tables in the following list are used internally by Skype for Business Server 2015. Their details are not described in this document.
  
## Tables for Internal Use by Lync Server

|**Table**|**Description**|
|:-----|:-----|
|**DbConfigDateTime** <br/> |For internal use only.  <br/> |
|**DbConfigInt** <br/> |For internal use only.  <br/> |
|**DbErrorMessage** <br/> |For internal use only.  <br/> |
|**FrontEnd Table** <br/> |For internal use only.  <br/> |
|**MSMQProcessing Table** <br/> |For internal use only.  <br/> |
|**SummaryTableConfiguration** <br/> |For internal use only.  <br/> |
|**Syndicators Table** <br/> |For internal use only.  <br/> |
|**SyndicatorsTenantMap Table** <br/> |For internal use only.  <br/> |
|**Task Table** <br/> |For internal use only.  <br/> |
|**UserStatistics** <br/> |For internal use only.  <br/> |
|**UsageSummary_UQ** <br/> |For internal use only.  <br/> |
|**UsageSummary** <br/> |For internal use only.  <br/> |
|**DaylightSavingYears** <br/> |For internal use only.  <br/> |
|**TimeZoneConfiguration** <br/> |For internal use only.  <br/> |
|**TimeZones** <br/> |For internal use only.  <br/> |
|**FailureSummary_UQ** <br/> |For internal use only.  <br/> |
|**FailureSummary** <br/> |For internal use only.  <br/> |
|**ServerSummary** <br/> |For internal use only.  <br/> |
|**MsDiagMetaData** <br/> |For internal use only.  <br/> |
   

