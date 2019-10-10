---
title: Teams files and folders to exclude from antivirus scanning
author: msdmaguire
ms.author: dmaguire
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: ramesa
audience: admin
description: Improve Teams performance by excluding certain files and folders from regular antivirus scanning.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_PracticalGuidance
appliesto: 
- Microsoft Teams
---

Teams files and folders to exclude from antivirus scanning
=================================

You can improve the overall performance of your Teams deployment by preventing your anitvirus programs from scanning certain Teams files and folders. Otherwise, you'll be using system resources to scan files and folders that don't need to be scanned. 

## Files and folders to add to your antivirus safe lists


Do not use the MSI to deploy updates, because the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update (except in VDI environments) when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams. 

> [!Important] 
> We don't recommended that you change the default install locations, as this could break the update flow. Having too old a version will eventually block users from accessing the service. 
