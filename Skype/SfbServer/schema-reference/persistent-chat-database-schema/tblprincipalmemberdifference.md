---
title: "tblPrincipalMemberDifference"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0b94f555-6888-4fe0-a048-4660a2513276
description: "tblPrincipalMemberDifference contains group membership changes (both added and removed members) that have not yet been processed by the later Active Directory Domain Services Sync steps."
---

# tblPrincipalMemberDifference
 
tblPrincipalMemberDifference contains group membership changes (both added and removed members) that have not yet been processed by the later Active Directory Domain Services Sync steps.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinGuid  <br/> |GUID, not null  <br/> |Principal GUID of the group that changed.  <br/> |
|memberADPath  <br/> |nvarchar (256)  <br/> |Distinguished name of the member.  <br/> |
|memberRemoved  <br/> |bit, not null  <br/> |False if the member was added. True if the member was removed.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|\<prinGuid, memberADPath\>  <br/> |Primary key.  <br/> |
   

