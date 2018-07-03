---
title: "What are the special character restrictions in Teams policies?"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
f1keywords:
- me.teamsadmincenter.policies.naming.error
description: "See what issues there are with special characters in the names of policies and what you can do to fix it."
---

# What are the special character restrictions in Teams policies?

**Although you can use special characters in the names of policies you created in Teams, we strongly recommend that you don't.**

Policy names that you create for meetings, chat and prescense, and other things in Teams can have special characters such as @,#,$. However, if you are wanting to make changes to the name in the Microsoft Teams and Skype for Business admin center, you won't be able to. You must use Windows PowerShell and the correct policy cmdlet to make changes.

For example, if you have a meeting policy with special characters and you want to change the name or remove the special characters from the name, you will need to use the Set-CsMeetingPolicy cmdlet. 

Here is a list of the policy cmdlets that you may need to do this:
1. Set-CsMeetingPolicy
2. Set-CsAppPolicy
3. Set-*


