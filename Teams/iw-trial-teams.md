---
title: Manage the Microsoft Teams Commercial Cloud Trial offer
author: ChuckEdmonson
ms.author: chucked
manager: serdars
ms.date: 12/10/2018
ms.topic: reference
audience: Admin
ms.reviewer: annikaelias
ms.service: msteams
search.appverid: MET150
localization_priority : Priority
description: Office 365 users who are not licensed for Microsoft Teams can initiate a 1-year trial of Teams.
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Manage the Microsoft Teams Commercial Cloud Trial offer
=======================================================

Microsoft Teams is a great collaborative tool for your organization. It empowers people and teams to discuss, innovate, and share ideas using the power of Office 365. The Microsoft Teams Commercial Cloud Trial offers existing Office 365 users in your organization who are not licensed for Microsoft Teams to initiate a 1-year trial of the product. Admins can switch this feature on or off for users in their organization.

## What's in the offer

The service plans included in this offer are:

- Exchange Foundation
- Flow for Office 365 Plan 1
- Microsoft Planner
- Microsoft Teams (Teams1, Teams IW)
- Office Online
- PowerApps for Office 365 Plan 1
- SharePoint Online Kiosk
- Sway
- Yammer Enterprise

The trial grants a one-year trial subscription to your entire organization. The trial makes 500,000 licenses available for assignment. For each license assigned, the trial allocates 2 GB of SharePoint Online storage. 

## Who is eligible

Users must be enabled to sign up for apps and trials (in the Office 365 admin center). For more information, see [Manage the trial](#manage-the-trial) later in this article. 

Users who do not have an Office 365 license that includes Teams can initiate the Microsoft Teams Commercial Cloud Trial offer. For example, if a user has Office 365 Business (which doesn't include Teams), they are eligible for the trial.

## Who is not eligible

Your organization is not eligible for the trial if: 

- You are a Syndication Partner Customer
- You are a Reseller Partner Customer
- You are a Government or EDU customer

If your organization is ineligible for the Microsoft Teams Commercial Cloud Trial offer, you will not see the **Let users install trial apps and services** switch.

## How users sign up for the trial

Eligible users can sign up for the trial offer by logging into Teams ([teams.microsoft.com](https://teams.microsoft.com)). They will see the following screen to start the trial. 

![Screenshot of the start page for the Teams IW trial.](media/iw-trial-start-screen.png)

All trials within your organization share the same start and end dates, which is the date the first user signed up for the trial. For example, if user A starts the first trial on January 25, 2019 and user B starts a trial on June 3, 2019, both users' trial will expire on January 25, 2020.

## <a name="manage-the-trial"></a>Manage the trial

Admins can manage the licenses for users who have signed up. 

In addition, admins can disable the ability for end users to claim trial apps and services within their organization. Currently, the trial described in this article is the only trial in this category, but it might apply to other similar programs in the future. 

### Prevent users from installing trial apps and services

You can turn off a user’s ability to install trial apps and services.

1. From the [Microsoft 365 admin center](https://portal.office.com/adminportal/home), go to **Settings** > **Services & add-ins** > **User owned Apps and Services**.

    ![Screenshot of the Services & add-ins page in the Office 365 admin center.](media/iw-trial-enable-1.png)

2. Turn off **Let users install trial apps and services**.

    ![Screenshot of the User owned Apps and Services page in the Office 365 admin center.](media/iw-trial-enable-2.png)


### Manage trial availability for a user with a license that includes Teams

A user who is assigned a license that includes Teams is not eligible for the trial. When the Teams service plan is enabled, the user can log in and use Teams. If the service plan is disabled, the user cannot log in and is not presented with the trial option either.

To turn off access to Teams:

1. In the Microsoft 365 admin center, select **Users** > **Active users**.

2. Select the box next to the name of the user.

3. On the right, in the **Product licenses** row, choose **Edit**.

4. In the **Product licenses** pane, switch the toggle to **Off**.

    ![Screenshot of the Product licenses page in the Office 365 admin center.](media/iw-trial-enable-3.png)

### Manage Teams availability for users who already claimed the trial

If a user has claimed a Teams trial license, you can remove it by removing the license or service plan.

To turn off the trial license:

1. In the Microsoft 365 admin center, select **Users** > **Active users**.

2. Select the box next to the name of the user.

3. On the right, in the **Product licenses** row, choose **Edit**.

4. In the **Product licenses** pane, switch the toggle to **Off**.

    ![Screenshot of the Teams trial license setting on the Product licenses pane](media/iW-trial-enable-4.png)
    
>[!Note]
>The Microsoft Teams Trial toggle switch will appear once the first user signed up for the trial in the organization.

### Manage Teams for users who have the trial license

You can manage users who have a trial license just like you manage users who have a regular paid license. For more information, see [Manage Microsoft Teams settings for your organization](enable-features-office-365.md).

### Upgrade users from the trial license

To upgrade users from the trial license, do the following:

1. Purchase a subscription that includes Teams.

2. Remove the Teams trial subscription from the user.

3. Assign the newly purchased license.

For more information, see [Office 365 licensing for Microsoft Teams](Office-365-licensing.md).
