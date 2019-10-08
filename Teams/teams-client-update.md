---
title: Teams updates
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: annaray
search.appverid: MET150
description: Learn how the Teams desktop client is updated.
appliesto: 
- Microsoft Teams
---

# Teams update process

The Teams web app is updated weekly.

Teams desktop client updates are released every two weeks after rigorous internal testing and validation through our Technology Adoption Program (TAP). This usually takes place on a Tuesday. If a critical update is required, Teams will bypass this schedule and release the update as soon as it’s available.

The desktop client updates itself automatically. Teams checks for updates every few hours behind the scenes, downloads it, and then waits for the computer to be idle before silently installing the update.

Users can also manually download updates by clicking **Check for updates** on the **Profile** drop-down menu on the top right of the app. If an update is available, it will be downloaded and silently installed when the computer is idle.

Users need to be signed in for updates to be downloaded. 

Starting July 31, 2019, Teams client updates use significantly lower network bandwidth during the update. This is turned on by default and requires no action from admins or users.

## What about updates to Office 365 ProPlus?

Teams is installed by default with new installations of Office 365 ProPlus as described in [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/teams-install). 

Teams follows its own update process as outlined above, and not the update process for the other Offices apps, such as Word and Excel. To learn more, read [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)

## What about updates to Teams on VDI?

Teams clients on Virtual Desktop Infrastructure (VDI) aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](https://docs.microsoft.com/microsoftteams/teams-for-vdi#install-teams-on-vdi). You must uninstall the current version to update to a newer version.

## Can admins deploy updates instead of Teams auto-updating?

Teams does not give admins the ability to deploy updates through any delivery mechanism.

## Servicing agreement

As a modern online service, the Teams client auto-updates every two weeks. To ensure users have the latest capabilities, performance enhancements, and service reliability, Teams offers support to desktop clients up to two versions old.

Users on Teams desktop clients that are more than six versions old will encounter a blocking page and are asked to update to the latest version of Teams from [https://teams.microsoft.com/download](https://teams.microsoft.com/download).

Unsupported desktop client versions upon the first install and/or first run of Teams have a 28-day grace period before the above-mentioned servicing information takes effect. This includes users using the Teams desktop client as part of the Office 365 ProPlus bundle

Teams desktop clients on Government Clouds currently have an exception to this servicing agreement until further notice.

### What versions are currently supported?

When Teams releases an update of the desktop client, the minimum supported version changes. Teams desktop clients that earlier than the following version numbers are not supported:

- Windows: 1.2.00.1758
- Mac: 1.2.00.1761

Teams desktop clients that are earlier than the following version numbers are blocked:

- Windows: 1.2.00.1758
- Mac: 1.2.00.1761

To avoid any disruption to your users' service, update to the latest version of the Teams desktop client.