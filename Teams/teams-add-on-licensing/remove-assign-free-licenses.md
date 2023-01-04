---
title: Retire Microsoft Teams Free (Classic) for your organization
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer:
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
  - Licensing
  - admindeeplinkMAC
description: Learn how to remove the Teams free (classic) licenses and assign paid Teams licenses
---

# Retire Microsoft Teams Free (Classic) for your organization

On March 12, 2023, Microsoft will retire the **Microsoft Teams Free (Classic)** license.

This article provides IT admins instructions on how to retire their organization's **Microsoft Teams Free (Classic)** licenses and move to paid Teams licenses.

If you don't move your users' free Teams licenses to paid Teams licenses by March 12, 2023, your users will lose access to Teams.

To complete this process, you can choose one of two methods:

- [Use the Microsoft 365 admin center.](#use-microsoft-365-admin-center-to-replace-licenses)
- [Use PowerShell.]()

If your organization decides not migrate to a paid Teams license, you can export your organization's content from Teams. For instructions on how to export Teams content, see [Export content with Microsoft Teams Export APIs](/microsoftteams/export-teams-content).

## Use Microsoft 365 admin center to replace licenses

1. Sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. On the left-side menu, go to **Users** > and select [**Active users**](https://go.microsoft.com/fwlink/p/?linkid=834822) to view licenses assigned to users.
    1. The **License** column will show **Microsoft Teams Free (Classic)**.
1. On the left-side menu, go to **Billing** > and select [**Licenses**](https://go.microsoft.com/fwlink/p/?linkid=842264) to see if you have available purchased licenses.
    1. If your organization has available licenses, skip to Step #4 to assign those licenses to the users with **Teams Free (Classic)** licenses.
    2. If you need to purchase licenses, we recommend [**Teams Essentials**](https://admin.microsoft.com/adminportal/home#/catalog/offer-details/microsoft-teams-essentials-aad-identity-/2D7C59AC-F814-43E0-8E8E-E4EA91A09CAF), which is available up to 300 seats.
    3. If you need more than 300 seats, use <add E1 purchase link – ensure we have one>.
1. If you would like to purchase licenses, go to **Billing** > and select **Purchase services**.
1. When you're ready to replace the **Teams Free (Classic)** licenses, go to **Users** > [**Active users**](https://admin.microsoft.com/adminportal/home#/users).
1. Select all users with only the **Teams Free (Classic)** license listed in the **Licenses** column.
1. At the top of the admin center, select the **Manage product licenses** option.
1. Select **Replace**.
    1. Selecting the **Replace** option requires you to reselect all licenses you wish those users to be assigned. If you only select the new paid Teams license, the other licenses those users were assigned will be removed from the users and replaced with the Teams license.
    1. If your users have different license
1. Choose the new license, and then **Save changes**.

## Use Microsoft PowerShell to replace licenses

1. Open the Microsoft PowerShell desktop app.
