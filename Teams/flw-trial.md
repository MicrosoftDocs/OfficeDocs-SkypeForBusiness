---
title: Get started with Teams for frontline workers
author: daisyfell
ms.author: daisyfeller
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to set up a 90-day Teams for frontline workers trial for your organization.
ms.localizationpriority: medium
ms.collection: 
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Teams for frontline workers trial overview

The Microsoft Teams Frontline Trial experience lets users in your organization who have Azure Active Directory (Azure AD) and aren't licensed for Teams initiate a Teams experience designed for frontline workers. Admins can switch this feature on or off for users in their organization.

## What services are included

The trial includes everything in the [Microsoft 365 F3 license](https://www.microsoft.com/microsoft-365/enterprise/f3) with the following exceptions:

- The trial license includes Exchange Foundation rather than Exchange Kiosk.

## Eligibility

> [!NOTE]
> This offer isn't available for GCC, GCC High, DoD, or EDU customers.

Users can start a frontline trial for their team if they:

- Belong to an organization within the trial pilot.
- Have an active license that gives them access to Teams.
- Haven't previously started a frontline worker trial.

Users can participate in a frontline worker trial if they have a managed Azure Active Directory domain email address.

Users are ineligible to participate if they:

- Currently have Microsoft Teams from a paid or trial license.
- Previously held a trial license.

> [!NOTE]
> Once a user has started the trial, users without existing access to Teams cannot be added to the trial team. Existing Teams users can still be added to the trial.

## Set up the trial

Eligible users can start a Frontline Trial by signing into Teams from the desktop or [web](https://teams.microsoft.com). At this time, starting a Frontline Trial through mobile is not supported. When a trial is initiated, the entire team will be assigned the Frontline Trial license automatically. The user who started the trial will receive email notifications throughout the course of the trial. [Learn users can start and manage a trial](link to end user docs).

## Manage the frontline trials experience

Admins can prevent end users from starting the Frontline Trial within their organization by using the **AllowSelfServicePurchase** PowerShell module. This is only for trial licenses. [Learn more](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

### Manage Teams for users who have the Frontline Trial license

You can manage users who have the Frontline Trial license just like you manage users who have a regular paid license. For more information, see [Manage Teams settings for your organization](/microsoftteams/manage-teams-overview).

### Remove a trial license

You can remove the Frontline Trial license through PowerShell or your Microsoft 365 admin center.

[Learn how to remove with PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

[Learn how to remove in the admin center](/microsoft-365/admin/add-users/delete-a-user).

## Upgrade users from Frontline Trial

You'll need admin privileges to upgrade your users. [Learn how](/microsoftteams/upgrade-from-teams-exploratory).

If the Frontline Trial license ends and a user isn't immediately upgraded to a subscription that includes Teams, they lose access to Teams. After 30 days, the data is deleted. The user still exists in Azure Active Directory. If a new license is assigned to the user to enable Teams functionality within the 30-day period, all their content in Teams will still exist.

## FAQ

**How long does the trial last** <br>
The Frontline Trial is available for 90 days.

**What should administrators do at the end of the 90 day Frontline Trial experience?** <br>
At the end of the 90 day trial, administrators can convert Frontline Trial users in need of a paid license to a Microsoft Frontline 1 or 3 license with full capabilities. Make sure to do this before the Frontline Trial subscription expires to avoid any disruption to the users' experiences. [Learn how to upgrade your users](#upgrade-users-from-frontline-trial).

**What is the data retention policy?** <br>
You can learn about data retention from the [Microsoft 365 subscription information](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?)
