---
title: Microsoft Teams resources for Education admins
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Licensing walkthrough for Microsoft Teams for EDU.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Assign Microsoft Teams licenses for EDU

Microsoft Teams is a digital hub that brings conversations, content, and apps together in one place. Because it's built on Office 365, schools benefit from integration with their familiar Office apps and services. Your institution can use Microsoft Teams to create collaborative classrooms, connect in professional learning communities, and communicate with school staff all from a single experience in Office 365 for Education.

To get started, IT administrators need to use the Microsoft 365 Admin Center to [enable Microsoft Teams for your school](https://docs.microsoft.com/microsoft-365/education/intune-edu-trial/enable-microsoft-teams).
Once complete, you must assign licenses to user accounts so your faculty, staff, and students can access Office 365 services, such as Microsoft Teams.

You can assign licenses to user accounts either individually or automatically through group membership. To assign Office 365 licenses to individual, or a small set of user accounts via the Microsoft 365 admin center, follow this article. To assign licenses automatically through group membership, see one of our supporting articles:

- [Office 365 Powershell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)
- [Group-based Licensing in Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign)

You can assign licenses to users on either the **Active users** page, or on the **Licenses** page. Which method you use depends on whether you want to assign product licenses to specific users, or assign users licenses to specific products.

> [!NOTE]
> If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.

## Assign licenses to users on the Licenses page

> [!NOTE]
> You must be a Global admin, Billing admin, License admin, or User management admin. For more information, see [About Office 365 admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

When you use the **Licenses** page to assign licenses, you assign licenses for a specific product to up to 20 users. On the **Licenses** page, you see a list of all the products you have subscriptions for, together with the total number of licenses for each product, how many licenses are assigned, and how many are available.

1. In the admin center, go to the **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264) page.
1. Select a product for which you want to assign licenses. Microsoft Teams is part of the free Office 365 A1 for Students SKU.
1. Select **Assign licenses**.
1. In the **Assign licenses to users** pane, begin typing a name, which should generate a list of names. Choose the name you're looking for from the results to add it to the list. You can add up to 20 users at a time.
1. Select **Turn apps and services on or off** to assign or remove access to specific items, such as Microsoft Teams. Ensure **Microsoft Teams** and **Office for the web (Education)** are selected.
1. When you're finished, select **Assign**, then select **Close**.

To change the apps and services a user has access to:
