---
title: ErrorReport table in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: ae0287b4-e8ca-4f8c-84ef-502897dcaa2a
---


# ErrorReport table in Skype for Business Server 2015
[]
The ErrorReport table stores information about errors that have occurred. Each record is one error occurrence. The errors are captured either by the CDR agent running on the front-end server or sent from the client.
  
    
    



|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ErrorTime** <br/> |datetime  <br/> |Primary  <br/> |Date and time the error occurred.  <br/> |
|**ErrorReportSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the error report. Used in conjunction with **ErrorTime** to uniquely identify an error report. <br/> |
|**ErrorId** <br/> |int  <br/> |Foreign  <br/> |Unique ID of the error type. See the  [ErrorDef table in Skype for Business Server 2015](errordef-table-in-skype-for-business-server-2015.md) for more information. <br/> |
|**FromUserId** <br/> |int  <br/> |Foreign  <br/> |User who originated the request that caused the error. See the  [Users table](users-table.md) for more information. <br/> |
|**ToUserId** <br/> |int  <br/> |Foreign  <br/> |Destination user for the request that caused the error. See the  [Users table](users-table.md) for more information. <br/> |
|**ConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Conference URI related to the error. See the  [ConferenceUris table in Skype for Business Server 2015](conferenceuris-table-in-skype-for-business-server-2015.md) for more information. Typically, if ConferenceUriId is not null, then either FromUserId or ToUserId will be null. <br/> |
|**SessionIdTime** <br/> |datetime  <br/> |Foreign  <br/> |Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs-table-in-skype-for-business-server-2015.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs-table-in-skype-for-business-server-2015.md) for more information. <br/> |
|**SourceId** <br/> |int  <br/> |Foreign  <br/> |Server that sent the error report (if the report is being sent from a server component). See the  [Servers table](servers-table.md) for more information. <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**ApplicationId** <br/> |int  <br/> |Foreign  <br/> |Server that sent the error report (if the report is being sent from a server component). See the  [Application table in Skype for Business Server 2015](application-table-in-skype-for-business-server-2015.md) for more information. <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**MsDiagHeader** <br/> |image  <br/> | <br/> |More information about the error.  <br/> This data can be converted to text format by using this syntax:  <br/>  `cast(cast(Detail as varbinary(max)) as varchar(max))` <br/> |
|**ClientVersionId** <br/> |int  <br/> |Foreign  <br/> |The client version of endpoint that sends the error report. See the  [ClientVersions table in Skype for Business Server 2015](clientversions-table-in-skype-for-business-server-2015.md) for more information. <br/> |
|**IsCapturedByServer** <br/> |bit  <br/> ||Is the error report captured by the CDR agent running on the front-end server, or sent by the client.  <br/> |
|**Flag** <br/> |smallint  <br/> ||Reserved for future use.  <br/> |
|**TelemetryId** <br/> |uniqueIdentifier  <br/> ||Unique identifier correlating join time information for the different components involved in a conference.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**SessionSetupTime** <br/> |int  <br/> ||Time (in milliseconds) required for a specific component to join a conference.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**ServerId** <br/> |int  <br/> |Foreign  <br/> |Represents the fully qualified domain name of the server that generated the error report.  <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |Represents the fully qualified domain name of the pool where the error report was generated.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

