---
title: Teams client update process
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 04/29/2019
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: annaray
search.appverid: MET150
description: Learn how the Teams desktop client is updated.
appliesto: 
- Microsoft Teams
---

# Teams client update process

This article explains how and when the Teams desktop client is updated.

## How often does Teams update?

Desktop client updates are released every two weeks after rigorous internal testing and validation through our Technology Adoption Program (TAP). This usually takes place on a Tuesday. If a critical update is required, Teams will bypass this schedule and release the update as soon as it’s available.

The web app is always up to date with the latest and greatest improvements.

## How does the desktop client update take place?

The desktop client updates itself automatically. Teams checks for an update every few hours behind the scenes, downloads it, and then waits for users to be idle before silently installing the update.

Users can also manually download updates by clicking **Check for updates** on the **Profile** drop-down menu on the top right of the app. If an update is available, it will be downloaded and silently installed when the user is idle.

Users need to be signed in for updates to be downloaded.

## What about updates to Office 365 ProPlus?

Teams is installed by default with new installations of Office 365 ProPlus. Users who have existing installations of Office 365 ProPlus can download and install Teams by going to the [Teams download site](https://teams.microsoft.com/downloads). Or admins can install Teams for their users by following [these instructions](https://docs.microsoft.com/MicrosoftTeams/msi-deployment). For more information about Teams installation with Office 365 ProPlus, go to [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/teams-install).

After Teams is installed, Office 365 ProPlus users can manually update Teams by clicking **Check for updates** on the **Profile** drop-down menu on the top right of the app. If an update is available, it will be downloaded and silently installed when the user is idle.

## What about updates to Teams on VDI?

Teams on Virtual Desktop Infrastructure (VDI) isn't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](https://docs.microsoft.com/microsoftteams/teams-for-vdi#install-teams-on-vdi). You must uninstall the current version to update to a newer version.

## Can admins deploy updates instead of Teams auto-updating?
Teams does not give admins the ability to deploy updates through any delivery mechanism.

## What is the Teams TAP?

The Technology Adoption Program (TAP) at Microsoft provides a consistent experience for customers who partner with Microsoft in obtaining real world customer feedback on Microsoft pre-release products. For more information, see