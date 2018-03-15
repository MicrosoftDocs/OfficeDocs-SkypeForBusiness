---
title: "List of CDR tables in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 031843fd-c7ff-4534-9b02-8847aad70807

description: "In this articleStatic TablesSupporting TablesTables Specific to Conference CDR RecordsTables for Messages in IM ConferencesTables for Peer-to-Peer SessionsTable for VoIP Call DetailsTable for E9-1-1 Call AuditingTables for TroubleshootingTables for Internal Use by Lync Server"
---

# List of CDR tables in Lync Server 2013
[]
 **In this article**
  
[Static Tables](#sectionSection0)
  
[Supporting Tables](#sectionSection1)
  
[Tables Specific to Conference CDR Records](#sectionSection2)
  
[Tables for Messages in IM Conferences](#sectionSection3)
  
[Tables for Peer-to-Peer Sessions](#sectionSection4)
  
[Table for VoIP Call Details](#sectionSection5)
  
[Table for E9-1-1 Call Auditing](#sectionSection6)
  
[Tables for Troubleshooting](#sectionSection7)
  
[Tables for Internal Use by Lync Server](#sectionSection8)
  
The call detail recording (CDR) database schema consists of the following tables. 
  
## Static Tables
<a name="sectionSection0"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[CallPriorities table in Lync Server 2013](callpriorities-table.md) <br/> |Stores the list of possible call priorities, such as emergency, urgent, normal, non-urgent, and more.  <br/> |
|[ConferenceJoinTimeThresholds table in Lync Server 2013](conferencejointimethresholds-table.md) <br/> |Stores the classification boundaries used by the Conference Join Time Summary Report.  <br/> |
|[DeRegisterType table in Lync Server 2013](deregistertype-table.md) <br/> |Stores the list of possible user de-register reasons, such as "client initiated," "registration expired," "client crash," and more.  <br/> |
|[MediaList table in Lync Server 2013](medialist-table.md) <br/> |Stores the list of media types that can generate entries in the database (for example, IM, audio, video, and file transfer).  <br/> |
|[PurgeSettings table in Lync Server 2013](purgesettings-table.md) <br/> |Stores information that specifies if (and when) outdated call detail records will automatically be deleted from the CDR database.  <br/> |
|[Roles table in Lync Server 2013](roles-table.md) <br/> |Stores the list of possible conference roles (for example, attendee and presenter).  <br/> |
|[SIPResponseMetaData table in Lync Server 2013](sipresponsemetadata-table.md) <br/> |Stores a list of SIP response codes and the classification and definition of each of those codes.  <br/> |
   
## Supporting Tables
<a name="sectionSection1"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[ClientVersions table in Lync Server 2013](clientversions-table.md) <br/> |Stores the clients (both client type and version number) of each client involved in a call with information captured in this database.  <br/> |
|[ConferenceUris table in Lync Server 2013](conferenceuris-table.md) <br/> |Stores a list of ConferenceURIs that are used in conference related calls.  <br/> |
|[ContentTypes table in Lync Server 2013](contenttypes-table.md) <br/> |Stores a list of Session Initiation Protocol (SIP) content types that are used in both peer-to-peer calls and conference calls.  <br/> |
|[Devices table in Lync Server 2013](devices-table.md) <br/> |Stores a list of devices, including their manufacturer, hardware version, and MAC address.  <br/> |
|[Dialogs table in Lync Server 2013](dialogs-table.md) <br/> |Stores information about the Dialog ID for each session in the database.  <br/> |
|[EdgeServers table in Lync Server 2013](edgeservers-table.md) <br/> |Stores a list of Edge Servers that are used for external calls.  <br/> |
|[Gateways table in Lync Server 2013](gateways-table.md) <br/> |Stores a list of Gateways that are used for Voice over Internet Protocol (VoIP) calls.  <br/> |
|[HardwareVersions table in Lync Server 2013](hardwareversions-table.md) <br/> |Stores a list of hardware versions of devices (desk phone).  <br/> |
|[Manufacturers table in Lync Server 2013](manufacturers-table.md) <br/> |Stores a list of manufacturers of devices (desk phone).  <br/> |
|[Mcus table in Lync Server 2013](mcus-table.md) <br/> |Stores information about the various A/V Conferencing Servers and their URIs.  <br/> |
|[MediationServers table in Lync Server 2013](mediationservers-table.md) <br/> |Stores a list of Mediation Servers that are used for VoIP calls.  <br/> |
|[Phones table in Lync Server 2013](phones-table.md) <br/> |Stores all the phone numbers used in VoIP calls that were archived or whose call details were recorded.  <br/> |
|[Pools table in Lync Server 2013](pools-table.md) <br/> |Stores the names of the pool on which IM messages are captured.  <br/> |
|[Servers table in Lync Server 2013](servers-table.md) <br/> |Stores the name of servers involved in calls.  <br/> |
|[Tenants table in Lync Server 2013](tenants-table.md) <br/> |Stores the tenants supported by current deployment. There some build-in tenants for Enterprise user, Federated User, public IM connectivity user, and Anonymous users.  <br/> |
|[UserAgentDef table in Lync Server 2013](useragentdef-table.md) <br/> |Maps user agent identifiers to the agent's descriptive names.  <br/> |
|[Users table in Lync Server 2013](users-table.md) <br/> |Stores the user URIs of users who have participated in sessions recorded or archived in this database.  <br/> |
|[UserStatistics table in Lync Server 2013](userstatistics-table.md) <br/> |Stores information about an individual user's usage of the system.  <br/> |
   
## Tables Specific to Conference CDR Records
<a name="sectionSection2"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[Conferences table in Lync Server 2013](conferences-table.md) <br/> |Stores information about all conferences that were archived or whose details were recorded, including ConferenceURI, and start and end time.  <br/> |
|[ConferenceSessionDetails table in Lync Server 2013](conferencesessiondetails-table.md) <br/> |Stores information about every SIP-based conference session, including start and end time, user ID, response code, and diagnostic ID for each session.  <br/> |
|[FocusJoinsAndLeaves table in Lync Server 2013](focusjoinsandleaves-table.md) <br/> |Stores information about conference joins and leaves, including users' role and client version.  <br/> |
|[McuJoinsAndLeaves table in Lync Server 2013](mcujoinsandleaves-table.md) <br/> |Stores information about the A/V Conferencing Servers that are involved in a conference and the user join and leave times.  <br/> |
   
## Tables for Messages in IM Conferences
<a name="sectionSection3"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[ConferenceMessageCount table in Lync Server 2013](conferencemessagecount-table.md) <br/> |For each IM conference, stores the number of messages that were sent by each user.  <br/> |
|[IMReportSummary table in Lync Server 2013](imreportsummary-table.md) <br/> |Provides an overall report on the instant messaging sessions held in an organization.  <br/> |
   
## Tables for Peer-to-Peer Sessions
<a name="sectionSection4"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[SessionDetails table in Lync Server 2013](sessiondetails-table.md) <br/> |Stores information about every peer-to-peer session, including start and end time, user ID, response code, and message count for each user.  <br/> |
|[FileTransfers table in Lync Server 2013](filetransfers-table.md) <br/> |Stores information about file transfer sessions, including file name and result (accepted, rejected, or canceled).  <br/> |
|[Media table in Lync Server 2013](media-table.md) <br/> |Stores information about the different media types involved in peer-to-peer sessions.  <br/> |
   
## Table for VoIP Call Details
<a name="sectionSection5"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[VoipDetails table in Lync Server 2013](voipdetails-table.md) <br/> |For each two-party VoIP/PSTN call, stores information about the call, such as the phone ID of VoIP phone, gateway used, and which party disconnected. Refers to the [SessionDetails table in Lync Server 2013](sessiondetails-table.md) for call start/end times and response code.  <br/> > [!NOTE]> If one party on a call is a VoIP user or if a Mediation Server was involved in the call, a record will be created in this table. Information about VoIP/VoIP calls not involving a public switched telephone network (PSTN) phone is captured in the [SessionDetails table in Lync Server 2013](sessiondetails-table.md).           |
   
## Table for E9-1-1 Call Auditing
<a name="sectionSection6"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[Locations table in Lync Server 2013](locations-table.md) <br/> |For each emergency call, such as an Enhanced 9-1-1 (E9-1-1) call, stores location information about the call. Refers to the [SessionDetails table in Lync Server 2013](sessiondetails-table.md) for call start/end times and response code.  <br/> > [!NOTE]> This table only contains the location blob for the E9-1-1 call. Refers to the SessionDetails table for other detailed information about the call.           |
   
## Tables for Troubleshooting
<a name="sectionSection7"> </a>

|**Table**|**Description**|
|:-----|:-----|
|[Application table in Lync Server 2013](application-table.md) <br/> |Stores information about various processes within Lync Server 2013 that are involved in routing and connections.  <br/> |
|[CallType table in Lync Server 2013](calltype-table.md) <br/> |Stores information about types of the call, such as, "audio", "Instant Messaging", "audio and video" and "application sharing".  <br/> |
|[ErrorCategory table in Lync Server 2013](errorcategory-table.md) <br/> |Stores the friendly name for each Microsoft Lync Server 2013 diagnostic classification.  <br/> |
|[ErrorDef table in Lync Server 2013](errordef-table.md) <br/> |Stores information about types of errors and their definitions.  <br/> |
|[ErrorReport table in Lync Server 2013](errorreport-table.md) <br/> |Stores information about errors that have occurred.  <br/> |
|[ProgressReport table in Lync Server 2013](progressreport-table.md) <br/> |Stores information about the progress reports of various steps involved in Lync Server 2013 processes.  <br/> |
   
The tables in the following list are used internally by Lync Server. Their details are not described in this document.
  
## Tables for Internal Use by Lync Server
<a name="sectionSection8"> </a>

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
   

