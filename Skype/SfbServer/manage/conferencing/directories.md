---
ms.date: 03/17/2018
title: "Create conference directories in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: b124b229-7df5-4b7e-8c11-6661c8c8c051
description: "Summary: Learn how to create conference directories in Skype for Business Server."
---

# Create conference directories in Skype for Business Server
 
**Summary:** Learn how to create conference directories in Skype for Business Server.
  
Conference directories maintain a mapping between the alphanumeric meeting ID that a participant uses to join a conference when using Skype for Business, and the numeric-only conference ID that a dial-in conferencing participant uses to join the conference. 
  
## Create a conference directory

Creating multiple conference directories ensure that conference IDs stay short until a significant number of conferences are created. 
  
In an organization with a typical number of conferences per user, we recommend that you create one conference directory for every 999 users in the pool. Using this guideline, the conference IDs can generally be kept small. However, once the number of conference directories (across the pools) exceeds nine, the Conference ID length grows to support additional conferences.
  
The format of a conference ID is as follows: 
  
```console
  <housekeeping digit (1 digit)><conference directory (usually 1-2 digits> 
  <conference number (variable number of digits><check digit (1 digit)>
```

To create a conference directory, use the **New-CsConferenceDirectory** cmdlet. For example, the following command creates a conference directory with the identity 42, hosted on the pool atl-cs-001.litwareinc.com:
  
```PowerShell
New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"
```

For more information, see [New-CsConferenceDirectory](/powershell/module/skype/new-csconferencedirectory?view=skype-ps).

