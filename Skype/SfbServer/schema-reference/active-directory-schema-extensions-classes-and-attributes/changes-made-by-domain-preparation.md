---
title: "Changes made by domain preparation in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9191221e-6166-4c2b-837e-fa73d90fdf80
description: "The following table lists the access control entries (ACEs) that domain preparation creates on the domain root. All ACEs are inherited unless otherwise noted."
---

# Changes made by domain preparation in Skype for Business Server
 
The following table lists the access control entries (ACEs) that domain preparation creates on the domain root. All ACEs are inherited unless otherwise noted.
  
**ACEs Added to Domain Root**

|**ACE**|**RTCUniversal-UserReadOnly-Group**|**RTCUniversal-ServerReadOnly-Group**|**RTCUniversal-UserAdmins**|**RTCHSUniversal-Services**|**Authenticated-Users**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Read Container (not inherited)  <br/> |**Yes** <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |
|Read User PropertySet User-Account-Restrictions  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Read User PropertySet Personal-Information  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Read User PropertySet General-Information  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Read User PropertySet Public-Information  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Read User PropertySet RTCUserSearchProperty-Set  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |**Yes** <br/> |
|Read User PropertySet RTCPropertySet  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Write User Property Proxy-Addresses  <br/> |No  <br/> |No  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |
|Write User PropertySet RTCUserSearchProperty-Set  <br/> |No  <br/> |No  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |
|Write User PropertySet RTCPropertySet  <br/> |No  <br/> |No  <br/> |**Yes** <br/> |No  <br/> |No  <br/> |
|Read PropertySet DS-Replication-Get-Changes of all Active Directory objects  <br/> |No  <br/> |No  <br/> |No  <br/> |**Yes** <br/> |No  <br/> |
   
The following table lists the ACEs that domain preparation creates in the three built-in containers: Users, Computers, and Domain Controllers. All ACEs are inherited unless otherwise noted.
**ACEs Added to Built-in Containers**

|**ACE**|**RTCUniversal-UserReadOnly-Group**|**RTCUniversal-ServerReadOnly-Group**|
|:-----|:-----|:-----|
|Read Container (not inherited)  <br/> |**Yes** <br/> |**Yes** <br/> |
   

