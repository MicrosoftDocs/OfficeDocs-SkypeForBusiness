---
title: Manage the Frontline Trial in Teams
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

# Manage the Frontline Trial in Teams

> [!NOTE]
> This trial experience is coming soon. You can check when this is available to your organization by looking for a message in the [Message center](https://go.microsoft.com/fwlink/p/?linkid=2070717) in your Microsoft 365 Admin center.

The Microsoft Teams Frontline Trial experience lets users in your organization who have Azure Active Directory (Azure AD) and are in Teams initiate a Teams experience for their entire frontline team. You can disable this feature for users in your organization by using the [AllowSelfServicePurchase PowerShell module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

## What services are included

The trial includes everything in the [Microsoft 365 F3 license](https://www.microsoft.com/microsoft-365/enterprise/f3) with the following exceptions:

- The Frontline Trial includes Exchange Foundation rather than Exchange Kiosk.

> [!NOTE]
> Users may be missing other Teams functionalities due to this change.

## Eligibility

> [!NOTE]
> You can check if your organization is part of the trial pilot by looking for an announcement in the [Message center](https://go.microsoft.com/fwlink/p/?linkid=2070717) in your Microsoft 365 Admin center. Your organization will need to be a part of the trial pilot for users to initiate or participate in a trial. This offer isn't available for GCC, GCC High, DoD, or EDU customers.

Users can start a frontline trial for their team if they:

- Have an active license that gives them access to Teams.
- Haven't previously started a frontline worker trial.

> [!IMPORTANT]
> If the user who initiated the trial leaves your organization before the trial ends, you as admin will need to monitor the trial,check in with the team to see who's making use of these features, and decide which users you'll need to upgrade to a paid license.

Users can participate in a frontline worker trial if they have a managed Azure Active Directory domain email address.

Users are ineligible to participate if they've previously started a trial.

> [!NOTE]
> Users without existing access to Teams can only be added to the trial team at the time of team creation. Existing Teams users can still be added to the trial after the team has been created.

## Set up the trial

Eligible users can start a Frontline Trial by signing into the Tasks app in Teams from the desktop or [web app](https://teams.microsoft.com/_#/apps/com.microsoft.teamspace.tab.planner/sections/mytasks). At this time, starting a Frontline Trial through mobile is not supported. When a trial is initiated, the entire team will be assigned the Frontline Trial license automatically. The user who started the trial will receive email notifications throughout the course of the trial. [Learn users can start and manage a trial](link to end user docs).

## Manage the frontline trials experience

Admins can prevent end users from starting the Frontline Trial within their organization by using the **AllowSelfServicePurchase** PowerShell module. This is only for trial licenses. [Learn how to use the AllowSelfServicePurchase PowerShell module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

### Manage Teams for users who have the Frontline Trial license

You can manage users who have the Frontline Trial license just like you manage users who have a regular paid license. For more information, see [Manage Teams settings for your organization](/microsoftteams/manage-teams-overview).

### Remove a trial license

You can remove the Frontline Trial license through PowerShell or your Microsoft 365 admin center.

[Learn how to remove with PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

[Learn how to remove in the admin center](/microsoft-365/admin/add-users/delete-a-user).

## Upgrade users from Frontline Trial

You'll need admin privileges to upgrade your users. [Learn more about upgrading from a trial license](/microsoftteams/upgrade-from-teams-exploratory).

At the end of the 90-day trial, you'll need to check with your users to see who needs to continue with a paid license. Upgrade your users to a [Microsoft 365 F3 license](https://www.microsoft.com/microsoft-365/enterprise/f3) with full capabilities, or another license that suits your needs. Make sure to do this before the Frontline Trial subscription expires to avoid any disruption to the users' experiences.
If the Frontline Trial license ends and a user isn't immediately upgraded to a subscription that includes Teams, they lose access to Teams. After 30 days, their data (files, messages, and more) is deleted. The user still exists in Azure Active Directory. If a new license is assigned to the user to enable Teams functionality within the 30-day period, all their content in Teams will still exist. [Learn how to upgrade your users](#upgrade-users-from-frontline-trial).

## FAQ

**How long does the trial last** <br>
The Frontline Trial lasts for 90 days.

**What should administrators do at the end of the 90-day Frontline Trial experience?** <br>
At the end of the 90-day trial, you'll need to check with your users to see who needs to continue with a paid license. Then you'll need to [Upgrade your users](#upgrade-users-from-frontline-trial)

**What happens if the user who started the trial leaves your organization?** <br>
You as admin will need to monitor the trial for the rest of the 90-day period, and upgrade to paid licenses for users who need them when the trial ends.

**What is the data retention policy?** <br>
You can learn about data retention from the [Microsoft 365 subscription information](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?)

**What if a user encounters an error when starting the Frontline Trial?** <br>
Make sure that your organization, the user starting the trial, and the users being added to the trial meet the [eligibility criteria](#eligibility).