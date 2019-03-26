---
title: "Changes made by Grant-CsSetupPermission in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c5801f48-14e3-4fdd-8f14-d52e7af07a57
description: "To delegate setup, you can grant permissions to the RTCUniversalServerAdmins universal group for a specific Active Directory organizational unit (OU), enabling members of the RTCUniversalServerAdmins group in that OU to install Skype for Business Server in the specified domain without being members of the Domain Admins group."
---

# Changes made by Grant-CsSetupPermission in Skype for Business Server
 
To delegate setup, you can grant permissions to the RTCUniversalServerAdmins universal group for a specific Active Directory organizational unit (OU), enabling members of the RTCUniversalServerAdmins group in that OU to install Skype for Business Server in the specified domain without being members of the Domain Admins group. 
  
The **Grant-CsSetupPermission** cmdlet grants the RTCUniversalServerAdmins group permissions on an OU, as specified in the following table:
  
**Permissions granted to Objects in the OU**

|**Permissions apply to:**|**Permissions granted are:**|
|:-----|:-----|
|RTCUniversalServerAdmins  <br/> | Special access: <br/>  Read servicePrincipalName <br/>  Write servicePrincipalName <br/>  Delete tree <br/>  Replicating directory changes <br/> |
|Descendant serviceConnectionPoint objects  <br/> | Special access: <br/>  Read permissions <br/>  Write permissions <br/>  Create child <br/>  Delete child <br/>  List contents <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-Server objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-WebComponents objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-MCU objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-MediationServer objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-ApplicationServer objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant msRTCSIP-ConnectionPoint objects  <br/> | Special access: <br/>  Write property <br/>  Read property <br/>  Delete tree <br/> |
|Descendant Computer objects  <br/> | Special access for serviceConnectionPoint: <br/>  Create child objects <br/>  Delete child objects <br/>  Delete tree <br/>  Special access for public information: <br/>  Read property <br/>  Special access for DNS host name: <br/>  Read property <br/> |
   

