---
title: Upgrade from the Teams Exploratory trial
author: DaniEASmith
ms.author: danismith
manager: pamgreen
ms.topic: reference
audience: Admin
ms.reviewer: 
ms.date: 04/23/2024
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: high
description: Upgrade users from a Teams Exploratory trial to a paid license.
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
  - tier1
ms.custom:
  - admindeeplinkMAC
appliesto: 
  - Microsoft Teams
---

# Upgrade users from the Teams Exploratory trial

This article provides an overview of how to upgrade your users from a Teams Exploratory trial to paid Teams licenses.

- [Step 1: When to upgrade](#step-1-when-to-upgrade)
- [Step 2: Choose an upgrade path](#step-2-choose-an-upgrade-path)
- [Step 3: Assign paid licenses](#step-3-assign-paid-licenses)

> [!NOTE]
> There are two possible experiences of Teams Exploratory: **organizational** or **self-service**. Starting late April 2023, users in organizations that don't have the organizational trial will be eligible for the self-service trial. Some of the instructions in this article will depend on which experience of Teams Exploratory your users have access to.
>
> To see if you have users with a Teams Exploratory license, you can go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) > **Billing** > **Licenses** > and scroll to see if **Microsoft Teams Exploratory** is listed. If it is listed, you have users with a Teams Exploratory license.
>
> From this Microsoft 365 admin center page, you can also check if your Teams Exploratory licenses are a tenant-based or self-service trial. Select the **Filter** icon, scroll to **Account type**, and choose either **Organizational** or **Self-service**. If the **Microsoft Teams Exploratory** license appears with the **Organizational** filter, your Teams Exploratory trial is tenant-based. If the license appears with the **Self-service** filter, it's self-service.

## Step 1: When to upgrade  

To check when your organization’s Teams Exploratory trial is expiring and how many active users it has, sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and go to **Billing** > [**Your products**](https://go.microsoft.com/fwlink/p/?linkid=842054). You’ll also be notified before the Teams Exploratory trial expires.

> [!IMPORTANT]
> You should make a plan to upgrade your users to paid licenses before the expiration date, so users don’t lose access to Teams.
>
> Users will lose access to Teams 30 days after the trial's expiration date. As long as users are assigned a paid license within 60 days of the expiration date, they can regain access to Teams and all content still exists. However, after 60 days, the users’ data is deleted. After a new license is assigned to the users to enable Teams functionality, if they are added within the grace period time frame, all content remains. For more information, see [What happens to my data and access when my subscription ends?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires).

## Step 2: Choose an upgrade path

> [!TIP]
> We recommend Teams Essentials as the primary option for customers looking to upgrade their expiring Teams Exploratory trials. For more information, see [Compare Microsoft Teams Essentials to other plans](get-started-with-teams-essentials.md#how-does-microsoft-teams-essentials-compare-to-other-microsoft-teams-plans).

Depending on the subscriptions your organization currently has, there are several ways to upgrade from a Microsoft Teams Exploratory trial to a paid license:

- **Upgrade an existing Microsoft 365 subscription.** Use this option if your organization has subscriptions to other Office products that don’t include Teams. For more information, see [Upgrade to a different business plan](/microsoft-365/commerce/subscriptions/upgrade-to-different-plan).
  - To see active users for an existing subscription, sign into the [Microsoft admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and go to **Users** > [**Active users**](https://go.microsoft.com/fwlink/p/?linkid=834822).

- **Add users to an existing Microsoft 365 subscription.** Use this option if your organization doesn’t have enough paid Teams licenses to cover the Teams Exploratory users. For more information, see [Buy or remove licenses](/microsoft-365/commerce/licenses/buy-licenses).  
  - To add users to an existing subscription that already has enough available licenses, see [Move users to a different subscription](/microsoft-365/commerce/subscriptions/move-users-different-subscription).
  - To see active users for an existing subscription, sign into the [Microsoft admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and go to **Users** [**Active users**](https://go.microsoft.com/fwlink/p/?linkid=834822).

- **Buy a new Microsoft 365 subscription.** Use this option if your organization doesn’t have any existing subscriptions to Office products, or if your organization wants to buy a subscription that’s different from their existing subscription to cover Teams Exploratory users. For more information, see [Buy a different Microsoft 365 for business subscription](/microsoft-365/commerce/try-or-buy-microsoft-365\#buy-a-different-subscription).

- **Move users to a new license.** This method can only be used by customers who have users with the self-service Teams Exploratory trial.
  - Sign in to the [Microsoft admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and go to **Billing** > **Your products** > **Microsoft Teams Exploratory Trial**. Choose the users you need to move. Select the **Move** button in the actions bar, and then select a subscription to move those users to.

If you’re not sure which Microsoft 365 subscription to upgrade to, see [Microsoft 365 for Business](https://www.microsoft.com/microsoft-365/business#coreui-heading-hiatrep). If you need additional help choosing a subscription, or if your organization needs more than 300 licenses, contact your [Microsoft partner](https://www.microsoft.com/solution-providers/home) or Microsoft account representative.

## Step 3: Assign paid licenses

> [!IMPORTANT]
> Before you unassign any Teams Exploratory licenses, assign the new licenses to all the users you’re upgrading. Otherwise, they lose access to Teams until you assign a paid license.  

To assign your newly acquired licenses, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).  

After you assign the new licenses, unassign the Teams Exploratory licenses. For more information, see [Unassign licenses from users](/microsoft-365/admin/manage/remove-licenses-from-users).

### Auto-claim policies

Next time you upgrade, use auto-claim policies to create policies for your organization to automatically assign licenses from paid subscriptions to new users who haven’t acquired a Teams license. For more information, see [Manage auto-claim policies](/microsoft-365/commerce/licenses/manage-auto-claim-policies).

## Related topics

- [Manage the Microsoft Teams Exploratory license](teams-exploratory.md)
