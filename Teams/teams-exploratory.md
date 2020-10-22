---
title: Manage the Microsoft Teams Exploratory experience
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: reference
audience: Admin
ms.reviewer: baluc
ms.service: msteams
search.appverid: MET150
localization_priority: Priority
description: "Microsoft 365 or Office 365 users who are not licensed for Microsoft Teams can initiate an Exploratory Teams license."
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
appliesto: 
  - Microsoft Teams
---

Manage the Microsoft Teams Exploratory license
=======================================================

The Microsoft Teams Exploratory experience lets users in your organization who have Azure Active Directory (Azure AD) and aren't licensed for Teams initiate an exploratory experience of Teams. Admins can switch this feature on or off for users in their organization. The earlier [Microsoft Commercial Cloud Trial](iw-trial-teams.md) is now replaced by The Teams Exploratory experience.

## What's in the Teams Exploratory experience

The service plans that an admin will see as part of the Teams Exploratory experience are:

- Exchange Online (Plan 1)
- Flow for Microsoft 365 or Office 365
- Insights by MyAnalytics
- Microsoft Forms (Plan E1)
- Microsoft Planner
- Microsoft Search
- Microsoft StaffHub
- Microsoft Stream for Microsoft 365 and Office 365 E1 SKUs <sup>1</1>
- Microsoft Teams
- Mobile Device Management for Microsoft 365 or Office 365
- Office Mobile Apps for Office 365
- Office Online
- PowerApps for Microsoft 365 or Office 365
- SharePoint Online (Plan 1)
- Sway
- To-Do (Plan 1)
- Whiteboard (Plan 1)
- Yammer Enterprise

  <sup>1</sup> The change from using Microsoft Stream to [OneDrive for Business and SharePoint for meeting recordings](tmr-meeting-recording-change.md) will be a phased approach. At launch you'll be able to opt in to this experience, in November you'll have to opt out if you want to continue using Stream, and some time in early 2021 we'll require all customers to use OneDrive for Business and SharePoint for new meeing recordings.

## Who's eligible

Users fit the criteria for a Teams Exploratory experience if they:

- Have a managed Azure AD domain email address.
- Don't have a Teams license.
- Belong to a tenant with a paid Azure AD.
- Aren't a trial or COVID trial offer user.
- Aren't in a tenant that has at least 1 special COVID trial offer.

Users must be enabled to sign up for apps and trials (in the Microsoft 365 admin center). For more information, see [Manage the Teams Exploratory experience](#manage-the-teams-exploratory-experience), later in this article.

## Who isn't eligible

Your organization isn't eligible for this offer if you're a Syndication Partner Customer or a GCC, GCC High, DoD, or EDU customer.

## How users sign up for the Teams Exploratory experience

Eligible users can sign up for the Teams Exploratory experience by signing in to Teams ([teams.microsoft.com](https://teams.microsoft.com)). They'll be assigned this license automatically and the tenant admin will receive an email notification the first time someone in your org starts the Teams Exploratory experience.

## Manage the Teams Exploratory experience

The Teams Exploratory experience is meant to be initiated by individual end users, and you can't initiate this offer on behalf of end-user employees.

The Teams Exploratory experience comes with an Exchange Online license but it won't be assigned to the user until the admin assigns it. If the user doesn't have an Exchange license already and the admin has yet to assign the Exchange Online license, the user won't be able to schedule meetings in Teams and might be missing other Teams functionality.

Admins can disable the ability for end users to run the Teams Exploratory experience within their organization by using the **Trial apps and services** switch.

### Prevent users from installing trial apps and services

You can turn off a user's ability to install trial apps and services, which would prevent the user from running the Teams Exploratory experience.

1. From the Microsoft 365 admin center, go to **Settings** > **Org settings**, select **Services**, and then select **User owned apps and services**.

    ![the Services page in the admin center](media/iw-trial-services.png)

2. Clear the **Let users install trial apps and services** check box.

    ![the User owned apps and services page in admin center](media/iw-trial-user-owned-apps-services.png)

    > [!NOTE]
    > If your organization is ineligible for the Teams Exploratory experience, you won't see the **Let users install trial apps and services** option.

### Manage availability for a user with a license that includes Teams

A user who is assigned a license that includes Teams isn't eligible for the Teams Exploratory experience. When the Teams service plan is turned on, the user can sign in and use Teams. If the service plan is disabled, the user can't sign in and the Teams Exploratory experience isn't available. You must have admin privileges.

To turn off access to Teams:

1. In the Microsoft 365 admin center, select **Users** > **Active users**.

2. Select the box next to the name of the user.

3. In the **Product licenses** row, choose **Edit**.

4. In the **Product licenses** pane, switch the toggle to **Off**.

    ![the Product licenses page in the admin center.](media/iw-trial-enable-3.png)

### Manage Teams availability for users who are already using the Teams Exploratory experience

If a user is running the Teams Exploratory experience, you can turn it off by removing the license or service plan. You must have admin privileges.

To turn off the Teams Exploratory experience license:

1. In the Microsoft 365 admin center, select **Users** > **Active users**.

2. Select the box next to the name of the user.

3. In the **Product licenses** row, choose **Edit**.

4. In the **Product licenses** pane, switch the toggle for this exploratory license to **Off**.

    >[!Note]
    >The Teams Exploratory toggle switch will appear after the first user in the organization launches the Teams Exploratory experience.

### Manage Teams for users who have the Teams Exploratory license

You can manage users who have the Teams Exploratory license just like you manage users who have a regular paid license. For more information, see [Manage Teams settings for your organization](enable-features-office-365.md).

### Upgrade users from the Teams Exploratory license

To upgrade users from the Teams Exploratory license (you must have admin privileges), do the following:

1. Purchase a subscription that includes Teams.

2. Remove the Teams Exploratory subscription from the user.

3. Assign the newly purchased license.

For more information, see [Microsoft Teams service description](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description).

> [!NOTE]
> If the Teams Exploratory license ends and a user isn't immediately upgraded to a subscription that includes Teams, the user data is not removed. The user still exists in Azure Active Directory and all data within Teams still remains. Once a new license is assigned to the user to enable Teams functionality again, all content will still exist.

## What happens to legacy Microsoft Teams Commercial Cloud Trial licenses

As of February, 2020, eligible users can begin using the latest Microsoft Teams Exploratory experience. All legacy Teams Commercial Cloud Trial licenses will be automatically converted to the new offer before their trial expires.

When users sign in to their expired Teams Commercial Cloud Trial for the first time, we automatically assign a Teams Exploratory experience license to those users. Users aren't converted until they sign in.

### Remove a Teams Exploratory license

- If you would like to remove this license by using PowerShell, see:
[Remove licenses from user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell)

- If you would like to remove this license through the admin portal, see:
[Delete a user from your organization](https://docs.microsoft.com/microsoft-365/admin/add-users/delete-a-user)

## What is the data retention policy?

See [Microsoft 365 subscription information](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?view=o365-worldwide).

## How long does the Teams Exploratory experience last

The Microsoft Teams Exploratory experience is available at no additional cost until your next **agreement anniversary** or **renewal** on or after January 2021. At that time, end users on a Microsoft Exploratory experience license will need to move to a paid license that includes Teams. Any Microsoft Exploratory experience licenses initiated after that will remain available at no additional cost until your next **anniversary** or **renewal** cycle.

### What happens if an end user initiates the Microsoft Teams Exploratory experience just before the anniversary or renewal date

Microsoft Teams Exploratory experience licenses initiated within 90 days of your **agreement anniversary** or **renewal** won't be required to move to a paid license until the subsequent anniversary or renewal cycle.

### What if my agreement doesn’t have an anniversary or yearly renewal date (for example, month-to-month agreements)

For agreements without an anniversary or yearly renewal date, the subsequent year after the first end-user activates the Microsoft Teams Exploratory experience licenses will be treated as the anniversary or renewal date. Users on the Microsoft Teams Exploratory license must be converted to a paid license by that date each year, according to the policies outlined in this article.

For example, if the first end user activates Microsoft Teams Exploratory on June 19, 2020, then they and all other eligible users in the customer tenant must convert to a paid license with Teams by June 19, 2021.

> [!Note]
> Customers will be disabled and blocked from starting a new Exploratory trial licenses for 3 months past the expiration of their previous Exploratory trial license.
