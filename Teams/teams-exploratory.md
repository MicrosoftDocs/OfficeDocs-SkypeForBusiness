---
title: Manage the Microsoft Teams Exploratory experience
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: reference
audience: Admin
ms.reviewer: janebo
ms.date: 04/23/2024
ms.service: msteams
search.appverid: MET150
ms.localizationpriority: high
description: Microsoft 365 or Office 365 users who aren't licensed for Microsoft Teams can initiate an Exploratory Teams license.
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

# Manage the Microsoft Teams Exploratory license

The Microsoft Teams Exploratory experience lets users in your organization who have Microsoft Entra ID and aren't licensed for Teams initiate an exploratory experience of Teams. Admins can switch this feature on or off for users in their organization.

## What's in the Teams Exploratory experience

The service plans that an admin sees as part of the Teams Exploratory experience are:

- Exchange Online (Plan 1)
- Power Automate
- Microsoft Viva Insights
- Microsoft Forms (Plan E1)
- Microsoft Planner
- Microsoft Search
- Microsoft Stream for Microsoft 365 and Office 365 E1 SKUs <sup>1</1>
- Microsoft Teams
- Mobile Device Management for Microsoft 365 or Office 365
- Office Mobile Apps for Office 365
- Office Online
- Power Apps for Microsoft 365 or Office 365
- SharePoint Online (Plan 1)
- Sway
- To-Do (Plan 1)
- Whiteboard (Plan 1)
- Viva Engage

## Who's eligible

Users fit the criteria for a Teams Exploratory experience if they:

- Have a managed Microsoft Entra domain email address.
- Belong to a tenant with a paid subscription.
- Don't have an active Teams license.
- Aren't in a tenant where a license assignment policy was created.

Admins must allow users to sign up for apps and trials in the Microsoft 365 admin center. For more information, see [Manage the Teams Exploratory experience](#manage-the-teams-exploratory-experience), later in this article.

## Who isn't eligible

Users don't fit the criteria if they:

- Currently have Teams from a paid license or trial license, or previously had trial license.
- Are in a tenant that used/received at least one special COVID offer.

Your organization isn't eligible for this offer if you're a Syndication Partner Customer or a GCC, GCC High, DoD, or EDU customer.

## How users sign up for the Teams Exploratory experience

Eligible users can sign up for the Teams Exploratory experience by signing into Teams from the desktop or web at [teams.microsoft.com](https://teams.microsoft.com). At this time, enabling Teams Exploratory through mobile isn't supported. When they sign up, they'll be assigned this license automatically, and the tenant admin will receive an email notification the first time someone in your org starts the Teams Exploratory experience.

## Manage the Teams Exploratory experience

> [!NOTE]
> There are two possible experiences of Teams Exploratory: **organizational** or **self-service**. Starting late April 2023, users in organizations that don't have the organizational trial will be eligible for the self-service trial. Some of the instructions in this article will depend on which experience of Teams Exploratory your users have access to.
>
> To see if you have users with a Teams Exploratory license, you can go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) > **Billing** > **Licenses** > and scroll to see if **Microsoft Teams Exploratory** is listed. If it is listed, you have users with a Teams Exploratory license.
>
> From this Microsoft 365 admin center page, you can also check if your Teams Exploratory licenses are a tenant-based or self-service trial. Select the **Filter** icon, scroll to **Account type**, and choose either **Organizational** or **Self-service**. If the **Microsoft Teams Exploratory** license appears with the **Organizational** filter, your Teams Exploratory trial is tenant-based. If the license appears with the **Self-service** filter, it's self-service.

The Teams Exploratory experience is meant to be initiated by individual end users. You can't initiate this offer on behalf of end-user employees.

Admins can turn off the ability for end users to run the Teams Exploratory experience within their organization. For more information, see [Prevent users from installing trial apps and services](#prevent-users-from-installing-trial-apps-and-services).

### Service plan assignment

The Teams Exploratory experience comes with an Exchange Online license, but it won't be assigned to the user until the admin assigns it.

- If the user doesn't have an Exchange license already, and the admin has yet to assign the Exchange Online license, the user won't be able to schedule meetings in Teams and might be missing other Teams functionality.

- If the user already has an Exchange Online license assigned to them, and then signs up for the Teams Exploratory license, their Exchange Online plan will be turned off. The admin will need to turn the plan back on in the Microsoft 365 admin center.
  1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
  1. Select **Billing** from the left-side navigation.
  1. Select **Licenses** from the menu.
  1. On the **Licenses** page, find and select the user(s).
  1. Select **Manage apps & services** on the actions bar.
  1. On the **Manage apps & services** pane, turn on **Exchange Online** by selecting the checkbox.
  1. Select **Save**.

### Prevent users from installing trial apps and services

You can turn off a user's ability to install trial apps and services, which would prevent the user from running the Teams Exploratory experience.

#### If your users have the self-service Teams Exploratory trial

If your tenant has users with the self-service Teams Exploratory trial, you need to use PowerShell to turn off a user's ability to install trial apps and services, even if trials were previously turned off.

For instructions on how to turn off and on users' ability to install trial apps and services, see [Use AllowSelfServicePurchase for the MSCommerce PowerShell module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell), which allows you to manage your end-user settings in the admin center, or you can use the MSCommerce Powershell script.

### Manage availability for a user with a license that includes Teams

A user who is assigned a license that includes Teams isn't eligible for the Teams Exploratory experience. When the Teams service plan is turned on, the user can sign in and use Teams. If the service plan is turned off, the user can't sign in, and the Teams Exploratory experience isn't available. You must have admin privileges.

To turn off access to Teams:

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), select **Users** > **Active users**.
1. Find and select the user.
1. In the user pane, select the **Licenses and apps** tab.
1. Unselect the checkbox for the **Microsoft Teams** license.
1. Select **Save changes**.

### Manage Teams availability for users who are already using the Teams Exploratory experience

If a user is running the Teams Exploratory experience, you can turn it off by removing the license or service plan. You must have admin privileges, and users must be on the tenant-based trial license.

To turn off the Teams Exploratory experience license:

1. In the Microsoft 365 admin center, select **Users** > **Active users**.
1. Find and select the user.
1. In the user pane, select the **Licenses and apps** tab.
1. Unselect the checkbox for the Teams Exploratory license.
    1. The Teams Exploratory box will appear after the first user in the organization launches the Teams Exploratory experience.
1. Select **Save changes**.

### Manage Teams for users who have the Teams Exploratory license

You can manage users who have the Teams Exploratory license just like you manage users who have a regular paid license. For more information, see [Manage Teams settings for your organization](enable-features-office-365.md).

### Upgrade users from Teams Exploratory

You must have admin privileges to move users from a Teams Exploratory license to a paid Teams license. For more information, see [Upgrade users from the Teams Exploratory trial](upgrade-from-teams-exploratory.md).

If you have tenant-based organizational Teams Exploratory licenses, you can cancel users' Teams Exploratory licenses. For more information, see [Remove a Teams Exploratory license](#remove-a-teams-exploratory-license).

> [!NOTE]
> If the Teams Exploratory license ends and a user isn't immediately moved to a subscription that includes Teams, they lose access to Teams, OneDrive, and Sharepoint after a 30-day grace period. After another 30 days, the associated Teams, OneDrive, and SharePoint data is deleted. The user still exists in Microsoft Entra ID.
>
> Once a new license is assigned to the user to enable Teams functionality again, all content will still exist if the user is added within the grace period time frame.

### Remove a Teams Exploratory license

You can only remove users' Teams Exploratory licenses if they are tenant-based organizational licenses. For more information about managing self-service trials, see [Manage self-service purchases and trials (for admins)](/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins#view-who-has-licenses-for-a-purchase-or-trial-subscription).

- If you would like to remove this license by using PowerShell, see [Remove licenses from user accounts with Office 365 PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

- If you would like to remove this license through the admin portal, see [Delete a user from your organization](/microsoft-365/admin/add-users/delete-a-user).

## What is the data retention policy

To learn about Microsoft's data retention policy, see [Microsoft 365 subscription information](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires).

## How long does the Teams Exploratory experience last

Teams Exploratory lasts depending on which Teams Exploratory experience your users have access to.

### Self-service Teams Exploratory trial

For users with the **self-service Teams Exploratory trial**, there are two different trial periods:

- For Enterprise Agreement (EA) customers: 6-month trial period
- For non-Enterprise Agreement customers: 3-month trial period

The **self-service trial** period begins when a user signs up for Teams Exploratory. The expiry date is determined per-user. Each user will have a unique expiry date depending on the length of trial period they qualify for and when they sign up.

### Tenant-based organizational Teams Exploratory trial

For users with the **tenant-based organizational trial**, they will have a 12-month trial period.

The **tenant-based trial** starts when the first user in an organization signs up for Teams Exploratory. The expiry date will apply to all users in the same tenant as the trial period begins on the first user's sign-up date.

> [!NOTE]
> The end date for the experience is configured at an organization level, meaning it will apply to all users in the same organization. For example, User 1 signs up for the subscription on January 1, 2021. This initiates a subscription end-date of December 31, 2021. Another user, User 2, signs up for the subscription on October 1, 2021. User 2 can use Teams Exploratory for three months, as their end-date will be December 31, 2021 because they're under the same organization's subscription as User 1.

### What should administrators do at the end of the trial Teams Exploratory experience

At the end of the trial period, administrators should convert all Teams Exploratory users to a paid license that includes Teams. It's vital to ensure this action is completed before the Teams Exploratory subscription expires to avoid any disruption to users' experience.

> [!NOTE]
> Customers will be disabled and blocked from starting a new Exploratory trial licenses for 3 months past the expiration of their previous Exploratory trial license.

For more information, see [Upgrade users from Teams Exploratory](#upgrade-users-from-teams-exploratory), above in this article.
