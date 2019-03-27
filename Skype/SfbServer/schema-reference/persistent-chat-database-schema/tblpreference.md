---
title: "tblPreference"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f94eb128-f782-42ff-a568-ed3529573bc8
description: "tblPreference contains the users' client preferences. This is generally used by clients previous to Lync 2013."
---

# tblPreference

tblPreference contains the users' client preferences. This is generally used by clients previous to Lync 2013.

**Columns**


| **Column**            | **Type**                        | **Description**                                                 |
|:----------------------|:--------------------------------|:----------------------------------------------------------------|
| prefLabel  <br/>      | nvarchar (255), not null  <br/> | Label with a format such as: \<user sip uri\>                   |
| prefSeqID  <br/>      | int, not null  <br/>            | A sequential number (per label) for versioning purposes.  <br/> |
| prefContent  <br/>    | nvarchar (max)  <br/>           | Encoded content.  <br/>                                         |
| lastModifiedBy  <br/> | int, not null  <br/>            | ID of the principal that updated the preference.  <br/>         |

**Key**

|**Column**|**Description**|
|:-----|:-----|
|\<prefLabel, prefSeqID\>  <br/> |Primary key.  <br/> |


