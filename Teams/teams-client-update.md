---
title: Teams updates
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: 
ms.date: 06/28/2024
search.appverid: MET150
f1.keywords: 
  - NOCSH
description: This article outlines the process behind updating the classic Microsoft Teams desktop client.
ms.localizationpriority: Medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Classic Teams update process

Teams web app updates are typically released on the fourth Monday of each month.

Teams desktop client updates are released monthly after rigorous internal testing and validation through our Technology Adoption Program (TAP). Desktop client updates typically start on the fourth Monday of the month and are rolled out gradually to customers throughout the remainder of the week. If a critical update is required, Teams bypasses this schedule and releases the update as soon as it’s available.

The desktop client updates itself automatically. Teams checks for updates every few hours behind the scenes, downloads it, and then waits for the computer to be idle before silently installing the update.

Users can also manually download updates by selecting **Check for updates** in the **...** drop-down menu next to your **Profile** icon in the top right of the app. If an update is available, it's downloaded and silently installed when the computer is idle.

## What can I do if classic Teams desktop client remains outdated?

These are a few reasons your classic Teams client remain outdated (major version below 1.7):
  - The update packages can't be downloaded. To address this, make sure the following domains can be accessed from the user's machine:
    - statics.teams.microsoft.com
    - statics.teams.cdn.office.net
  - Multiple users are sharing the machine and new users are logging in frequently (eg., a Kiosk machine)
  - Classic Teams is installed into a non-updatable location such as ProgramData or Program Files

If you're an admin and multiple users in your organization have remained on an older version of classic Teams client, your users aren't able to automatically move to new Teams. To resolve this, you can use the admin-provision tool TeamsBootstrapper.exe to remove classic Teams as well as to provision the new client. Please see next section to learn more.

## Can admins deploy updates instead of Teams auto-updating?

Admins can quickly move users to new Teams via the provision tool <b>TeamsBootstrapper.exe</b> with the -u argument. To learn more, please see the following article: [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md).

You can use the [Microsoft Teams new client usage report](new-teams-usage-report.md) to find out if the users in your organization are using an outdated classic Teams client.

## What about updates to Microsoft 365 Apps for enterprise?
Teams can be installed with new installations of Microsoft 365 Apps for enterprise as described in [Deploy Microsoft Teams with Microsoft 365 Apps for enterprise](/DeployOffice/teams-install).

Teams follows its own update process as outlined earlier in this article. Teams doesn't follow the update process for the other Offices apps, such as Word and Excel.

## Servicing agreement

As part of a modern online service, the Teams client is updated once per month. The client automatically installs updates when they become available to that client. Because we stagger the availability of updates worldwide, some clients in your organization might receive new updates before others. Because Teams is governed by the Modern Lifecycle Policy, it's expected that users remain on the most up-to-date version of the desktop client. Auto-updates ensure that users have the latest capabilities, performance enhancements, security, and service reliability.

To identify when desktop clients fall out of date, an in-app alert is displayed if the user’s current version is between one and three months old, and if there's a new version available. This in-app messaging encourages users to update to the latest version of Teams or, if necessary, to reach out to their IT admin to do so. Users on Teams desktop clients that are more than three months old will see a blocking page. This page gives the options to update now, reach out to their IT admin, or continue to Teams on the web.

Teams desktop clients on Government Clouds currently have an exception to this servicing agreement until further notice.

For information on new version releases, check [Message Center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter) or go to **Help** > **What’s new** in the client.

## What about updates to Teams on VDI?

Teams clients on Virtual Desktop Infrastructure (VDI) aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](teams-for-vdi.md). You must uninstall the current version to update to a newer version.
