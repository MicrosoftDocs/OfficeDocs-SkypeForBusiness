---
title: Force Public Preview  
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Learn how to easily preview and evaluate pre-release Teams features.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Force Public Preview  

Teams Public Preview channel allow customers to easily preview and evaluate pre-release Teams features. There are no program requirements or commitments. This is an opt-in channel controlled via IT admin policy (`AllowPublicPreview`). Public preview is enabled on a per-user basis.  

IT admins have three options to configure their users' public preview setting: 

 - **Follow Office Preview** (default): This default option will automatically enable Teams Public Preview features for any user enrolled in Office Current Channel (Preview). There are no more actions required by the end user. 

 - **Enabled**: This option enables Teams Public Preview regardless of whether a user is enrolled in Office Current Channel (Preview). The end user must also opt-in to Teams public preview in their Teams app. 

 - **Not enabled**: Teams Public Preview features will not be available to end users. 
 
IT admins can update this policy from Teams admin center (as shown below) or via PowerShell cmdlet (`CsTeamsUpdateManagementPolicy`). 

 ![force public preview policy update](media/force-preview.png)

Here is an example cmdlet to set the Teams global policy to Enabled:  

```
Set-CsTeamsUpdateManagementPolicy -Identity Global -AllowPublicPreview "Enabled" 
```

