---
title: Teams updates
ms.author: mikeplum
author: MikePlumleyMSFT
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
description: In this article, you'll learn about the process behind updating the Microsoft Teams desktop client.
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams update process

Teams web app updates are typically released on the 4th Monday of each month.

Teams desktop client updates are released monthly after rigorous internal testing and validation through our Technology Adoption Program (TAP). Desktop client updates typically start on the 4th Monday of the month and are rolled out gradually to customers throughout the remainder of the week. If a critical update is required, Teams will bypass this schedule and release the update as soon as it’s available.

The desktop client updates itself automatically. Teams checks for updates every few hours behind the scenes, downloads it, and then waits for the computer to be idle before silently installing the update.

Users can also manually download updates by selecting **Check for updates** in the **...** drop-down menu next to your **Profile** icon in the top right of the app. If an update is available, it will be downloaded and silently installed when the computer is idle.

Users need to be signed in for updates to be downloaded.

## What about updates to Microsoft 365 Apps for enterprise?

Teams is installed by default with new installations of Microsoft 365 Apps for enterprise as described in [Deploy Microsoft Teams with Microsoft 365 Apps for enterprise](/DeployOffice/teams-install).

Teams follows its own update process as outlined above. Teams doesn't follow the update process for the other Offices apps, such as Word and Excel. To learn more, read [Overview of update channels for Microsoft 365 Apps](/DeployOffice/overview-update-channels).

## Can admins deploy updates instead of Teams auto-updating?

Teams doesn't give admins the ability to deploy updates through any delivery mechanism.

## Servicing agreement

As a modern online service, the Teams client auto-updates every two weeks. Because Teams is governed by the Modern Lifecycle Policy, it's expected that users remain on the most up-to-date version of the desktop client. Auto-updates ensure that users have the latest capabilities, performance enhancements, security, and service reliability.

To identify when desktop clients fall out of date, an in-app alert will be displayed if the user’s current version is between one and three months old, and if there's a new version available. This in-app messaging encourages users to update to the latest version of Teams or, if necessary, to reach out to their IT admin to do so. Users on Teams desktop clients that are more than three months old will see a blocking page that gives the options to update now, reach out to their IT admin, or continue to Teams on the web.

Teams desktop clients on Government Clouds currently have an exception to this servicing agreement until further notice.

For information on new version releases, check [Message Center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter) or go to **Help** > **What’s new** in the client.

## What about updates to Teams on VDI?

Teams clients on Virtual Desktop Infrastructure (VDI) aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](teams-for-vdi.md). You must uninstall the current version to update to a newer version.
