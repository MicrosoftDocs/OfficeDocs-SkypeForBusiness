---
title: Install Microsoft Teams using MSI
author: Lester-Hewett
ms.author: lehewe
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Admins can use the Teams MSI to bulk deploy Microsoft Teams to select users or computers.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto: 
- Microsoft Teams
---

Install Microsoft Teams using MSI
=================================

> [!Tip]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

To use System Center Configuration Manager, or Group Policy, or any third-party distribution mechanisms for broad deployment, Microsoft has provided MSI files (both [32-bit](https://aka.ms/teams32bitmsi) and [64-bit](https://aka.ms/teams64bitmsi)) that admins can use for bulk deployment of Teams to select users or computers. Admins can use these files to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign in on that machine. (You can disable auto launch after installing the app. [See below](#disable-auto-lanuch-for-the-msi-installer).)
We recommend that you deploy the package to the computer, so all new users of the machine will also benefit from this deployment. 
 
> [!Note] 
> To learn more about SCCM, see [Introduction to System Center Configuration Manager](https://docs.microsoft.com/sccm/core/understand/introduction).

## Deployment procedure (recommended)
1. Retrieve the latest package.
2. Use the defaults prepopulated by the MSI.
3. Deploy to computers when possible.

## How the Microsoft Teams MSI package works

The Teams MSI will place an installer in Program Files. Whenever a user signs into a new Windows User Profile, the installer will be launched and a copy of the Teams application will be installed in that user's appdata folder. If a user already has the Teams app installed in the appdata folder, the MSI installer will skip the process for that user.

Do not use the MSI to deploy updates, because the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update when possible for the user. If a very old version gets deployed, the MSI will trigger an application update before the user is able to use Teams. 

> [!Important] 
> We don't recommended that you change the default install locations, as this could break the update flow. Having too old a version will eventually block users from accessing the service. 


## Target computer requirements

- .NET framework 4.5 or later
- Windows 7 or later
- 3 GB of disk space for each user profile (recommended)

## Clean up and redeployment procedure
If a user uninstalls Teams from their User Profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that User Profile. To redeploy Teams for this user on a particular computer where it was uninstalled, do the following:

1. Uninstall Teams App installed for every user profile. 
2. After uninstall, delete directory recursively under %localappdata%\Microsoft\Teams\. 
3. Redeploy the MSI package to that particular computer.

> [!TIP] 
> You can use our [Microsoft Teams deployment clean up](scripts/Powershell-script-teams-deployment-clean-up.md) script to accomplish steps 1 and 2 via SCCM. 	
					
## Disable auto launch for the MSI installer

If you want to disable auto launch, enter the following command prompt:

```
msiexec /i Teams_windows.msi OPTIONS="noAutoStart=true"
```

