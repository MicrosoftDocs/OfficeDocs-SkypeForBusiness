---
title: 'Assign Microsoft Teams licenses for education'
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Learn how to assign licenses for Microsoft Teams for Education.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: 
  - admindeeplinkMAC
---

# Assign Microsoft Teams licenses for education

This article is for IT admins in education who need to assign Team licenses to their faculty, staff, and students.

To get your users ready for Teams, you'll need to:

1. [Enable Microsoft Teams for your school in the Microsoft 365 admin center](/microsoft-365/education/intune-edu-trial/enable-microsoft-teams).
2. Assign licenses to user accounts for access to Microsoft 365 services, including Teams.

## Ways to assign Teams licenses

You can assign licenses to user accounts either:

- Individually or to a small group of users in the Microsoft 365 admin center.
- Automatically through group membership using [PowerShell](/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell) or [Active Directory group-based licensing](/azure/active-directory/users-groups-roles/licensing-groups-assign).

This article will walk you through how to assign licenses in the Microsoft 365 admin center.

In the Microsoft 365 admin center, you can assign licenses to users on either:

- The **Licenses** page to assign product licenses to specific users.
- The **Active Users** page to assign users' licenses to specific products.

> [!NOTE]
> You must be a Global admin, Billing admin, License admin, or User management admin. For more information, see [About Office 365 admin roles](/microsoft-365/admin/add-users/about-admin-roles).

## Assign licenses to users on the Licenses page

On the **Licenses** page, you see a list of all the products you have subscriptions for, the total number of licenses for each product, how many licenses are assigned, and how many are available.

1. In the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264) page.

2. Select a product for which you want to assign licenses. Microsoft Teams is part of the free Microsoft 365 A1 for Students SKU.

3. Select **Assign licenses**.

4. In the **Assign licenses to users** pane, begin typing a name, which should generate a list of names.

5. Choose the name you're looking for from the results to add it to the list. You can add up to 20 users at a time.

6. Select **Turn apps and services on or off** to assign or remove access to specific items, such as Microsoft Teams. Ensure **Microsoft Teams** and **Office for the web (Education)** are selected.

7. When you're finished, select **Assign**, then select **Close**.

### Change the apps and services a user has access to

1. Select the row that contains the user.

2. In the right pane, select or deselect the apps and services that you want to give access to, or remove access from.

3. When you're finished, select **Save**, then select **Close**.

## Assign licenses to users on the Active users page

1. In the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Users** > [Active users](https://go.microsoft.com/fwlink/p/?linkid=834822) page.

2. Select the circles next to the name(s) of the user(s) you want to assign license(s) to.

3. At the top, select **Manage product licenses**.

4. In the **Manage product licenses** pane, select **Add to existing product license assignments** > **Next**.

5. In the **Add to existing products** pane, switch the toggle to the **On** position for the license that you want the selected users to have. Ensure **Microsoft Teams** and **Office for the web (Education)** are selected.

   By default, all services associated with those license(s) are automatically assigned to the user(s). You can limit which services are available to the users. Switch the toggles to the **Off** position for the services that you don't want the users to have.

6. At the bottom of the pane, select **Add** > **Close**.
