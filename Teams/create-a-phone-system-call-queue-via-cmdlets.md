---
title: "Create a call queue via cmdlets"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
  - seo-marvel-apr2020
description: Learn how to set up call queues for large organizations in Microsoft Teams, which provides a greeting message, hold music, call redirecting, and other features.
---
# Create a call queue via cmdlets

## Assumptions
1)	Powershell is installed on your computer
a.	Set up your computer for [Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell.md)

b.	MSTeams Module Installed (Install-Module -Name MicrosoftTeams -Force -AllowClobber)
c.	MSOnline module installed (Install-Module -Name MSOnline -Force -AllowClobber)
2)	You have tenant administration rights
3)	You have purchased Microsoft Teams Phone
4)	The agents and distribution lists have already been created
5)	The phone numbers have already been acquired and are available for use within the tenant

