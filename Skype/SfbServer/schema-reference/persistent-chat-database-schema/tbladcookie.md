---
title: "tblADCookie"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0a9102c4-47aa-40ea-8a0d-20e72ab09848
description: "tblADCookie contains the current Lightweight Directory Access Protocol (LDAP) Sync cookies."
---

# tblADCookie
 
tblADCookie contains the current Lightweight Directory Access Protocol (LDAP) Sync cookies.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinGuid  <br/> |GUID, not null  <br/> |Principal GUID of the domain being monitored.  <br/> |
|prinDCHost  <br/> |nvarchar (255)  <br/> |Fully qualified domain name (FQDN) of the current domain controller used for Active Directory Domain Services Sync. Has informational value.  <br/> |
|adcContent  <br/> |image (binary)  <br/> |Active Directory Sync cookie.  <br/> |
|lastUpdated  <br/> |datetime  <br/> |Time stamp with the row update time.  <br/> |
|lockedUntil  <br/> |datetime  <br/> |Time until the row is locked for changes. This is part of a software interlock mechanism that ensures that only one of the chat services does the Active Directory Sync at a time.  <br/> |
   
**Keys**

|**Column(s)**|**Description**|
|:-----|:-----|
|prinGuid  <br/> |Primary key.  <br/> |
|prinGuid  <br/> |Foreign key with lookup in Principal.prinGuid table.  <br/> |
   

