---
title: "Registration view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8a42bc7d-3d4f-43c1-9e15-89b2ee419ade
description: "The Registration view stores information about user registration. This view was introduced in Lync Server 2013."
---

# Registration view
 
The Registration view stores information about user registration. This view was introduced in Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**RegisterTime** <br/> |datetime  <br/> |Time at which registration occurred.  <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> |URI of the user who registered.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who registered. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who registered. See the [Tenants table](tenants.md) for more information. <br/> |
|**EndpointId** <br/> |uniqueidentifier  <br/> |Unique identifier of the endpoint of the user registered with.  <br/> |
|**EndpointEra** <br/> |uniqueidentifier  <br/> |Unique identifier used to differentiate registrations that involve the same user and the same endpoint.  <br/> |
|**DeRegisterType** <br/> |datetime  <br/> |Time at which deregistration occurred.  <br/> |
|**DeRegisterReason** <br/> |nvarchar(256)  <br/> |Reason for deregistration.  <br/> |
|**ClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user who registered.  <br/> |
|**ClientType** <br/> |int  <br/> |Client used by the user who registered. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**ClientCategory** <br/> |nvarchar(64)  <br/> |Category of the client used by the user who registered.  <br/> |
|**IpAddress** <br/> |nvarchar(256)  <br/> |IP Address the user registered with. This may be an IPv4 or IPv6 address.  <br/> |
|**DialogId** <br/> |varstring(775)  <br/> |SIP dialog ID. The format of the is:  <br/> dialog;from-tag;to-tag  <br/> |
|**ResponseCode** <br/> |int  <br/> |SIP response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> |Diagnostic ID captured from SIP header.  <br/> |
|**Registrar** <br/> |nvarchar(256)  <br/> |FQDN of the Registrar.  <br/> |
|**Pool** <br/> |nvarchar(256)  <br/> |FQDN of the pool that captured the data for the session.  <br/> |
|**EdgeServer** <br/> |nvarchar(256)  <br/> |FQDN of the Edge Server used by the user who registered.  <br/> |
|**IsInternal** <br/> |bit  <br/> |Indicates whether the user logged on from the internal network.  <br/> |
|**IsUserServiceAvailable** <br/> |bit  <br/> |Indicates whether the UserService was available at registration time.  <br/> |
|**IsPrimaryRegistrar** <br/> |bit  <br/> |Indicates whether registration was with the primary Registrar.  <br/> |
|**DeviceMacAddress** <br/> |bigint  <br/> |MAC Address of device registered.  <br/> |
|**DeviceManufacturer** <br/> |nvarchar(256)  <br/> |Manufacturer of the device registered. See the [Manufacturers table in Skype for Business Server 2015](manufacturers.md) for more information. <br/> |
|**DeviceHardwareVersion** <br/> |nvarchar(256)  <br/> |Hardware version of the device registered. See the [HardwareVersions table in Skype for Business Server 2015](hardwareversions.md) for more information. <br/> |
   

