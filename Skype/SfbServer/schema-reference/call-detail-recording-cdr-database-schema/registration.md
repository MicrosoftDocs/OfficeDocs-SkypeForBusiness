---
title: "Registration table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 05ff9dd3-1aaa-4af0-bd69-8789fb8eaeb3
description: "Each record represents one user registration event."
---

# Registration table
 
Each record represents one user registration event.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used with **SessionIdSeq** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used with **SessionIdTime** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |The user ID. For more information, see the [Users table](users.md). <br/> |
|**EndpointId** <br/> |uniqueidentifier  <br/> ||A GUID to identify a registration endpoint. Usually the register event from the same computer of the same user has the same endpoint ID. Different machines have a different endpoint ID.  <br/> |
|**EndpointEra** <br/> |uniqueIdentifier  <br/> ||ID used to differentiate registrations that involve the same user and the same endpoint.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**ClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version of current user. For more information, see the [ClientVersions table in Skype for Business Server 2015](clientversions.md). <br/> |
|**RegistrarId** <br/> |int  <br/> |Foreign  <br/> |ID of the Registrar Server used for registration. For more information, see the [Servers table](servers.md). <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID of the pool in which the session was captured. For more information, see the [Pools table](pools.md). <br/> |
|**EdgeServerId** <br/> |int  <br/> |Foreign  <br/> |Edge Server the registration is going through. For more information, see the [EdgeServers table in Skype for Business Server 2015](edgeservers.md). <br/> |
|**IsInternal** <br/> |Bit  <br/> ||Whether the user is logged on from internal or not.  <br/> |
|**IsUserServiceAvailable** <br/> |bit  <br/> ||Whether the UserService is available or not.  <br/> |
|**IsPrimaryRegistrar** <br/> |bit  <br/> ||Whether register to the primary Registrar or not.  <br/> |
|**IsPrimaryRegistrarCentral** <br/> |bit  <br/> ||Indicates whether or not the user is registered with a survivable branch appliance.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**RegisterTime** <br/> |datetime  <br/> ||Registration time.  <br/> |
|**DeRegisterTime** <br/> |datetime  <br/> ||De-Registration time.  <br/> |
|**ResponseCode** <br/> |int  <br/> ||Response code of the register request.  <br/> |
|**DiagnosticId** <br/> |int  <br/> ||Diagnostic ID of the register request. This indicates that diagnostic information type.  <br/> |
|**DeviceId** <br/> |int  <br/> |Foreign  <br/> |The device that the register request is coming from. For more information, see the [Devices table in Skype for Business Server 2015](devices.md). <br/> |
|**DeRegisterTypeId** <br/> |tinyint  <br/> |Foreign  <br/> |The reason of deregister, such as 'user initiated,' 'registration expired,' 'client fail,' and more. For more information, see the [DeRegisterType table in Skype for Business Server 2015](deregistertype.md). <br/> |
|**IPAddress** <br/> |nvarchar(256)  <br/> ||IP address of the endpoint the user registered with. This can be an IPv4 address or an IPv6 address.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

