---
title: Teams updates
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.reviewer: annaray
search.appverid: MET150
f1.keywords:
- NOCSH
description: In this article, you will learn about the process behind updating the Microsoft Teams desktop client.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams update process

The Teams web app is updated weekly.

Teams desktop client updates are released every two weeks after rigorous internal testing and validation through our Technology Adoption Program (TAP). This usually takes place on a Tuesday. If a critical update is required, Teams will bypass this schedule and release the update as soon as it’s available.

The desktop client updates itself automatically. Teams checks for updates every few hours behind the scenes, downloads it, and then waits for the computer to be idle before silently installing the update.

Users can also manually download updates by clicking **Check for updates** on the **Profile** drop-down menu on the top right of the app. If an update is available, it will be downloaded and silently installed when the computer is idle.

Users need to be signed in for updates to be downloaded. 

Starting July 31, 2019, Teams client updates use significantly lower network bandwidth during the update. This is turned on by default and requires no action from admins or users.

## What about updates to Microsoft 365 Apps for enterprise?

Teams is installed by default with new installations of Microsoft 365 Apps for enterprise as described in [Deploy Microsoft Teams with Microsoft 365 Apps for enterprise](https://docs.microsoft.com/DeployOffice/teams-install). 

Teams follows its own update process as outlined above, and not the update process for the other Offices apps, such as Word and Excel. To learn more, read [Overview of update channels for Microsoft 365 Apps for enterprise](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)

## What about updates to Teams on VDI?

Teams clients on Virtual Desktop Infrastructure (VDI) aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](https://docs.microsoft.com/microsoftteams/teams-for-vdi#install-teams-on-vdi). You must uninstall the current version to update to a newer version.

## Can admins deploy updates instead of Teams auto-updating?

Teams does not give admins the ability to deploy updates through any delivery mechanism.

## Servicing agreement

As a modern online service, the Teams client auto-updates every two weeks. Because Teams is governed by the Modern Lifecycle Policy, it's expected that users remain on the most up-to-date version of the desktop client. This ensures that users have the latest capabilities, performance enhancements, security, and service reliability.

To begin assisting in identifying when desktop clients fall out of date, an in-app alert will be displayed if the user’s current version is between one and three months old, and if there's a new version available. This in-app messaging encourages users to update to the latest version of Teams or, if necessary, to reach out to their IT admin to do so. Users on Teams desktop clients that are more than three months old will see a blocking page that gives the options to update now, reach out to their IT admin, or continue to Teams on the web.

Desktop client versions that are more than three months old upon first install and/or first run of Teams have a 28-day grace period before encountering the above-mentioned servicing information. During this period, the auto-update process will update the Teams client. If not updated, users will see an in-app alert encouraging them to manually update to the latest version of Teams or, if necessary, to reach out to their IT admin to do so. This includes users using the Teams desktop client as part of the Microsoft 365 Apps for enterprise bundle.

Teams desktop clients on Government Clouds currently have an exception to this servicing agreement until further notice.

For information on new version releases, check [Message Center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter) or go to **Help** > **What’s new** in the client.
