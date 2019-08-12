---
title: "Schema changes in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d760cb93-77d4-4d64-adb7-416b808f36f8
description: "Before you deploy and operate Skype for Business Server, you must prepare Active Directory Domain Services by extending the schema. The schema extensions add the classes and attributes that are required by Skype for Business Server."
---

# Schema changes in Skype for Business Server
 
Before you deploy and operate Skype for Business Server, you must prepare Active Directory Domain Services by extending the schema. The schema extensions add the classes and attributes that are required by Skype for Business Server.

> [!NOTE]
> If you are upgrading from Lync Server 2013 to Skype for Business Server 2015, no schema changes are made and therefore this article does not apply.
  
Skype for Business Server requires several new classes and attributes and modifies some existing classes and attributes. In addition, much configuration information for Skype for Business Server is stored in the Central Management store instead of in AD DS as in previous versions. The following information is still stored in AD DS in Skype for Business Server:
  
- **Schema extensions**:
    
  - User object extensions
    
  - Extensions for classes to maintain backward compatibility with supported previous versions of Lync Server.
    
- **Data** (stored in Skype for Business Server extended schema and in existing schema classes):
    
  - User SIP Uniform Resource Identifier (URI) and other user settings
    
  - Contact objects for applications such as Response Group and Conferencing Attendant
    
  - A pointer to the Central Management store
    
  - Kerberos Authentication Account (an optional computer object)
    
This topic describes the Active Directory schema changes required by Skype for Business Server. It does not describe schema changes that were introduced by previous versions of Office Communications Server. For a list of classes and their descriptions, see [Schema classes and descriptions in Skype for Business Server](schema-classes-and-descriptions.md). For a list of attributes and their descriptions, see [Schema attributes and descriptions in Skype for Business Server](schema-attributes-and-descriptions.md). For a list of classes with the attributes they may contain, see [Schema attributes by class in Skype for Business Server](schema-attributes-by-class.md).
  
The msRTCSIP prefix identifies classes and attributes that are specific to Skype for Business Server.
  
## New Active Directory Attributes

The following table describes the Active Directory attributes that are added by Skype for Business Server.
  
**Attributes Added by Skype for Business Server**

|**Attribute**|**Description**|
|:-----|:-----|
|msExchUserHoldPolicies  <br/> |This multi-value attribute holds identifiers for hold policies that apply to the user. Hold policies preserve mailbox items for the user for the duration of the hold. This attribute is shared with Exchange 2013.  <br/> |
|msRTCSIP-UserRoutingGroupId  <br/> |This is the SIP routing group ID. Users in the same group will register to the same Front End Server.  <br/> |
|msRTCSIP-MirrorBackEndServer  <br/> |This attribute is used to store the mirrored SQL Server backend used by the Front End pool.  <br/> |
   
## Modified Active Directory Classes

The following table describes the Active Directory classes that are modified by Skype for Business Server.
  
**Classes Modified by Skype for Business Server**

|**Class**|**Change**|**Class or Attribute**|
|:-----|:-----|:-----|
|User  <br/> |add: mayContain  <br/> add: mayContain  <br/> |ProxyAddresses  <br/> msRTCSIP-UserRoutingGroupId  <br/> |
|Contact  <br/> |add: mayContain  <br/> add: mayContain  <br/> |ProxyAddresses  <br/> msRTCSIP-UserRoutingGroupId  <br/> |
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchUserHoldPolicies  <br/> |
|msRTCSIP-GlobalTopologySetting  <br/> |add: mayContain  <br/> |msRTCSIP-MirrorBackEndServer  <br/> |
   

