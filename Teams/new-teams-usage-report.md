---
title:  Usage report for new Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 01/31/2024
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: daro
search.appverid: MET150
f1.keywords:
- NOCSH
description: Information about the new Teams client usage report, what it does and how to make the best use of it.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Microsoft Teams new client usage report

The Microsoft Teams desktop client usage report gives you an overview of the Teams desktop clients in use within your organization. It highlights platform, version, and user type to help you better understand the current state of your user’s desktop clients.

## How to get to the Microsoft Teams desktop client usage report

1. In the Teams admin center, go to the **Analytics & Reports** > **Usage Reports** page.
1. From the Usage Reports page, choose the **Teams desktop client usage report**, choose a date range selection, and select **Run report**.

## Interpret the Microsoft Teams device usage report

The graph in the Teams desktop client usage report shows the usage of classic Teams and new Teams as a percentage within your tenant. These numbers are directly related – if one number increases the other will decrease. Take note of these important characteristics of this data:

- This data only represents Windows or Mac Teams desktop clients. It does not show any data about other client types, such as web, mobile, or any hardware devices.
- This data is dependent on a user’s Teams desktop client being actively used. If a user isn't active on their desktop client or their data can't be reported in for any reason, their data will be empty for the period in which there was no data available. This missing information can result in fluctuations in the data, for example during weekends or when users go on vacation.
- A user’s data originates from their most recent usage when the snapshot is taken. If a user has multiple machines they use regularly, whichever machine they used last will be represented for that day. For most users that have multiple machines, they usually have a primary device that gets most of their usage.

The data in the table columns below the graph allow a more granular look at individual users and the state of their Teams desktop client. This data can be exported using the Export to Excel function in the top right corner, and columns can be shown or hidden using the Edit columns function also in the top right corner.

|Column                   |Description                                                                        |
|-------------------------|-----------------------------------------------------------------------------------|
|Username                 |UPN of the user.                                                                   |
|Display name             |Display name of the user.                                                          |
|Classic or new (Windows) |Whether or not a Windows user is using the classic Teams or new Teams application. |
|App version (Windows)    |The version number of the Windows Teams application for the user.                  |
|Classic or new (Mac)     |Whether a Mac user is using the classic Teams or new Teams application.            |
|App version (Mac)        |The version number of the Mac Teams application for the user.                      |
|User type                |The representation of what deployment ring a user is assigned to. Differences between users in this column can explain why they may have different versions of the Teams application. The potential values that may display are: <br> - **TAP Admin**: Administrators who participate in the Microsoft Teams TAP program. Sometimes referred to as R1.5. <br> - **Developer Preview**: Developers who've opted into early preview of developer focused functionality for Teams app development. Sometimes referred to as R1.6. <br> - **TAP**: Users who participate in the Microsoft Teams TAP program. Sometimes referred to as R3. <br> - **Public Preview**: Users who participate in the [Public Preview](public-preview-doc-updates.md) program. Sometimes referred to as R3.6. <br> Production: Regular users who do not have access to early preview functionality. Sometimes referred to as R4. <br> - **GCC Production**: Regular GCC users who do not have access to early preview functionality. |

## Example Scenarios for the Teams desktop client usage report

- While your organization is moving from classic Teams to new Teams, this report will allow you to monitor progress along the way. You may have given your users the ability to toggle back and forth between classic and new Teams, or you may be moving groups of users to new Teams on a set schedule. In either case, this report will allow you to see and confirm the transition as you proceed.
- If your organization allows users to toggle back and forth between classic and new Teams ahead of the [automatic update coming on March 31 2024](new-teams-automatic-upgrade-announced.md), this report will allow you to identify users who've chosen to remain on classic Teams so you can perform any relevant communication or change management campaigns to help those users make the switch.
- Using the export capability of the report, you can identify any Teams desktop clients within your organization that have somehow ended up stuck on an older version and are not automatically updating as they should. This is often a result of some sort of network or machine issue or a configuration change. Identifying these users with this report will allow you to proactively identify and engage with these users to investigate and resolve the issue.

## Related topics

- [The new Microsoft Teams](new-teams-desktop-admin.md)
- [New Teams for Mac - Overview and prerequisites](new-teams-mac-install-prerequisites.md)
- [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md)
- [Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md)
