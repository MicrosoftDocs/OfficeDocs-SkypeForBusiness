---
title: "Registration table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 05ff9dd3-1aaa-4af0-bd69-8789fb8eaeb3
description: "Each record represents one user registration event."
---

# Registration table
 
Each record represents one user registration event.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |The user ID. See the [Users table](users.md) for more information. <br/> |
|**EndpointId** <br/> |uniqueidentifier  <br/> ||A GUID to identify a registration endpoint. Usually the register event from the same computer of the same user will have the same endpoint ID. Different machines have a different endpoint ID.  <br/> |
|**EndpointEra** <br/> |uniqueIdentifier  <br/> ||ID used to differentiate registrations that involve the same user and the same endpoint.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**ClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version of current user. See the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**RegistrarId** <br/> |int  <br/> |Foreign  <br/> |ID of the Registrar Server used for registration. See the [Servers table](servers.md) for more information. <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID of the pool in which the session was captured. See the [Pools table](pools.md) for more information. <br/> |
|**EdgeServerId** <br/> |int  <br/> |Foreign  <br/> |Edge Server the registration is going through. See the [EdgeServers table in Skype for Business Server 2015](edgeservers.md) for more information. <br/> |
|**IsInternal** <br/> |Bit  <br/> ||Whether the user is logged on from internal or not.  <br/> |
|**IsUserServiceAvailable** <br/> |bit  <br/> ||Whether the UserService is available or not.  <br/> |
|**IsPrimaryRegistrar** <br/> |bit  <br/> ||Whether register to the primary Registrar or not.  <br/> |
|**IsPrimaryRegistrarCentral** <br/> |bit  <br/> ||Indicates whether or not the user is registered with a survivable branch appliance.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**RegisterTime** <br/> |datetime  <br/> ||Registration time.  <br/> |
|**DeRegisterTime** <br/> |datetime  <br/> ||De-Registration time.  <br/> |
|**ResponseCode** <br/> |int  <br/> ||Response code of the register request.  <br/> |
|**DiagnosticId** <br/> |int  <br/> ||Diagnostic ID of the register request. This indicates that diagnostic information type.  <br/> |
|**DeviceId** <br/> |int  <br/> |Foreign  <br/> |The device that the register request is coming from. See the [Devices table in Skype for Business Server 2015](devices.md) for more information. <br/> |
|**DeRegisterTypeId** <br/> |tinyint  <br/> |Foreign  <br/> |The reason of de-register, such as 'user initiated', 'registration expired', 'client fail', and more. See the [DeRegisterType table in Skype for Business Server 2015](deregistertype.md) for more information. <br/> |
|**IPAddress** <br/> |nvarchar(256)  <br/> ||IP address of the endpoint the user registered with. This can be an IPv4 address or an IPv6 address.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

