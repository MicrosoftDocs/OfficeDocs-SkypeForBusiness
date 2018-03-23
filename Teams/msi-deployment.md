---
title: Install Microsoft Teams using MSI
author: ninadara
ms.author: ninadara
manager: serdars
ms.date: 03/21/2018
ms.topic: article
ms.service: msteams
ms.reviewer: ninadara
description: Admins can use the Teams MSI to bulk deploy Microsoft Teams to select users or computers.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Install Microsoft Teams using MSI
===========================================

To leverage System Center Configuration Manager, or Group Policy, or any 3rd party distribution mechanisms for broad deployment, Microsoft has provided MSI files (both [32-bit](http://aka.ms/teams32bitmsi) and [64-bit](http://aka.ms/teams64bitmsi)) for admins to leverage during bulk deployment of Microsoft Teams to select users or machines. Admins can use these files to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign-in on that machine. It is recommended that you deploy the package to the machine, so all new users to the machines will also benefit from this deployment. 
 
> [!Note] 
> To learn more about SCCM, see. [Introduction to System Center Configuration Manager](https://docs.microsoft.com/sccm/core/understand/introduction)

## Deployment Procedure (Recommendations)
1. Retrieve the latest package
2. Use the defaults prepopulated by the MSI
3. Deploy to machines when possible

## How the Microsoft Teams MSI package works

The Teams MSI will place an installer in Program Files. Whenever a user signs into a new Windows User Profile, the installer will be launched and a copy of Teams application will be installed in that user's appdata folder. If a user already has the Teams app installed in the appdata folder, the MSI installer will skip the process for that user.

Do not leverage the MSI to deploy updates, the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update when possible for the user. If a very old version gets deployed, the MSI will trigger an application update before the user is able to use Teams. 

> [!Important] 
> It's not recommended you change any install locations as this could break the update flow. Which then will eventually block users from accessing the service. 


## Target machine requirements:

1. .NET framework 4.5 or later
2. Windows 7 or later
2. 32GB of disk space for each user profile (recommended)

## Clean up\redeployment Procedure
If a user uninstalls Teams from for their User Profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that User Profile. To redeploy Teams for this user on a particular machine where it was uninstalled you will need to:

1. Uninstall Teams App installed for every user profile 
2. After uninstall, delete directory recursively under %localappdata%\Microsoft\Teams\ 
3. Redeploy the MSI package to that particular machine

> [!TIP] 
> You can leverage our [Microsoft Teams deployment clean up](.\scripts\Powershell-script-teams-deployment-clean-up.md) script to accomplish this steps 1 and 2 via SCCM. 								

