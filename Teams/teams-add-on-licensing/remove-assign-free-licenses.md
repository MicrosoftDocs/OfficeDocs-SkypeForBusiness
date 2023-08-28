---
title: Retire Microsoft Teams Free (classic) for your organization
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: 
ms.date: 08/28/2023
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
  - tier1
  - ContentEnagagementFY24
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom:
  - Licensing
  - admindeeplinkMAC
description: Learn how to remove the Teams free (classic) licenses and assign paid Teams licenses for your organization's users.
---

# Retire Microsoft Teams Free (classic) for your organization

This article is for IT admins who need to retire their users' **Teams Free (Classic)** licenses and assign them paid Teams licenses.

In mid-April 2023, Microsoft retired the **Microsoft Teams Free (classic)** license.

If you didn't move your users' free Teams licenses to paid Teams licenses by mid-April 2023, your users lost access to Teams.

To complete this process, you can choose one of two methods:

- [Use the Microsoft 365 admin center.](#use-microsoft-365-admin-center-to-replace-licenses)
- [Use Microsoft PowerShell.](#use-microsoft-powershell-to-replace-licenses)

If your organization decides not to migrate to a paid Teams license, you can export your organization's content from Teams. For instructions on how to export Teams content, see [Export content with Microsoft Teams Export APIs](/microsoftteams/export-teams-content).

## Use Microsoft 365 admin center to replace licenses

If your organization has few users assigned the **Teams Free (classic)** license, we recommend using the Microsoft 365 admin center for removing and assigning licenses.

### Check users' current Teams licensing

1. Sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. On the left-side menu, go to **Users** > and select [**Active users**](https://go.microsoft.com/fwlink/p/?linkid=834822) to view licenses assigned to users.
    1. The **License** column will show **Microsoft Teams Free (classic)** next to the users assigned that license.
1. On the left-side menu, go to **Billing** > and select [**Licenses**](https://go.microsoft.com/fwlink/p/?linkid=842264) to see if you have available paid Teams licenses.
    1. If your organization has available licenses, skip to [Assign paid Teams licenses](#assign-paid-teams-licenses) to assign those licenses to the users with **Teams Free (classic)** licenses.
1. Determine the number of paid Teams licenses you need to buy, if any.

### Purchase paid Teams licenses

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > and select **Purchase services**.
1. Select **View products** to view all available licenses.
1. Select the **Communication and collaboration** category filter to see Teams licenses.
1. Choose the paid Teams license you would like to replace **Teams Free (classic)**.
    1. We recommend the [**Teams Essentials** license](https://admin.microsoft.com/adminportal/home#/catalog/offer-details/microsoft-teams-essentials-aad-identity-/2D7C59AC-F814-43E0-8E8E-E4EA91A09CAF), which is available up to 300 seats.
    1. If you need more than 300 seats, we recommend purchasing [Microsoft 365 E1 licenses](https://admin.microsoft.com/Adminportal/Home#/catalog/offer-details/office-365-e1/CF4A479A-2119-4EF2-83D1-37CF8460EADA).
1. Enter in the number of licenses you would like to purchase, and then choose a billing frequency.
1. Select the **Buy** button to complete the purchasing process.

#### Purchase licenses in the admin center Marketplace

Some tenants have access to the Microsoft 365 admin center Marketplace. For these tenants, you will purchase licenses in the Marketplace.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), select **Marketplace** from the left-side menu.
1. Select the **All products** tab.
1. Select the **Communication and collaboration** category filter to see Teams licenses.
1. Choose the paid Teams license you would like to replace **Teams Free (classic)**.
1. Enter in the number of licenses you would like to purchase, and then choose a billing frequency.
1. Select the **Buy** button to complete the purchasing process.

### Assign paid Teams licenses

1. When you're ready to replace the **Teams Free (classic)** licenses, in the Microsoft 365 admin center, go to **Users** > [**Active users**](https://admin.microsoft.com/adminportal/home#/users).
1. Select all users with the **Teams Free (classic)** license listed in the **Licenses** column.
1. At the top of the admin center, select the **Manage product licenses** option.
1. In the right-side pane, select **Replace**.
    1. Selecting the **Replace** option requires you to reselect all licenses you wish those users to be assigned. If you only select the new paid Teams license, the other licenses those users were assigned will be removed from the users and replaced with the Teams license.
    1. If your users have different licensing needs, complete this process in batches to prevent incorrectly licensing users.
1. In the ride-side pane, choose the new paid Teams license and any other licenses the users should be assigned, and then select the **Save changes** button.

## Use Microsoft PowerShell to replace licenses

If your organization has a large number of users assigned the **Teams Free (classic)** license, we recommend using PowerShell to bulk unassign and assign licenses to users.

Before you can complete this process, you'll need paid Teams licenses for users assigned the **Teams Free (classic)** license. To purchase licenses for those users, see [Purchase paid Teams licenses](#purchase-paid-teams-licenses).

1. Connect your Microsoft 365 tenant to the [Microsoft Graph PowerShell SDK](/powershell/microsoftgraph/get-started).
1. Open the Microsoft PowerShell desktop app.
1. [Set user and organization permissions for Graph API](/microsoft-365/enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell#use-the-microsoft-graph-powershell-sdk).
1. [Remove **Teams Free (classic)** licenses from users accounts](/microsoft-365/enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell#removing-licenses-from-user-accounts).
1. [Assign paid Teams licenses to users](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell#assigning-licenses-to-user-accounts).

For more information on the Graph PowerShell SDK process, see [Use the Microsoft Graph PowerShell SDK](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell).

