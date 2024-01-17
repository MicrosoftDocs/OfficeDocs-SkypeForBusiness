---
title:  Upgrade to new Microsoft Teams with Microsoft 365 Apps
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 11/30/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about how to upgrade to new Microsoft Teams with Microsoft 365 Apps.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Upgrade to new Microsoft Teams with Microsoft 365 Apps

Starting in late August, new Teams will automatically install with new and existing installations of Microsoft 365 Apps on Windows.

Currently, users can install the new Microsoft Teams using the "Try the new Teams" toggle switch in classic Teams or by Admins bulk upgrading directly to the computers in their organization.

Administrators may exclude new Teams from automatically installing with Microsoft 365 Apps on Windows.

>[!Important]
>If the classic Teams app is already installed, the Microsoft 365 Apps deployment will install new Teams alongside classic Teams on the device. The classic Teams installation will not change.

## Rollout schedule

When will the new Microsoft Teams be included with installations of Microsoft 365 Apps?

The date when the new Teams starts being installed with Microsoft 365 Apps depends on which update channel you're using. The following table shows the schedule.

|Plan|Channel|Date|
|:-----|:-----|:-----|
|Business||October 2023|
|Enterprise|Office Beta Channel and Current Channel (Preview)|October 2023|
|Enterprise|Current Channel|October 2023|
|Enterprise|Monthly Enterprise Channel and Semi-Annual Enterprise Channel (Preview)|November 2023|
|Enterprise|Semi-Annual Enterprise Channel|December 2023|

## Prerequisites for target computers

For new Teams to be successfully installed, computers must meet the minimum requirements listed here.

### Required system and app requirements

|Requirement|Version/Description|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher (excluding Windows 10 LTSC for Teams desktop app)|
|Classic Teams app|Version 1.6.00.4472 or later to see the *Try the new Teams* toggle.</br>**Important:** Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client.|
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Delivery optimization (DO)|DO powers Teams automatic updates, which are required as part of the [Servicing Agreement](/microsoftteams/new-teams-automatic-upgrade-announced#servicing-agreement).</br></br>Overview: [What is Delivery Optimization?](/windows/deployment/do/waas-delivery-optimization)</br></br>Recommended settings: [Set up Delivery Optimization](/windows/deployment/do/waas-delivery-optimization-setup#recommended-delivery-optimization-settings)<br></br>**Note:** Download Mode 100 (Bypass) is not supported.|

>[!Note]
>Learn more: [**Update History for Microsoft 365 Apps**](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions).

## How to exclude new Teams from new installations

Admins who don't want new Teams included with Microsoft 365 Apps on devices running Windows can follow these steps to opt out.

1. Sign in to the Microsoft 365 Apps admin center (https://config.office.com) with an admin account.
2. Go to **Customization > Device Configuration > Modern Apps Settings**.
3. Select **Microsoft Teams (work or school)**,  then clear the **Enable automatic installation of new Microsoft Teams** check box.

>[!Note]
>For the best Teams experience, we recommend leaving the setting as is.

> [!NOTE]
> If you've set Teams update policy to **Not enabled**, but users still received new Teams client with M365 Apps, please follow instructions in our [How to uninstall the new Teams client](new-teams-deploy-using-policies.md#how-to-uninstall-the-new-teams-client) article to uninstall it for your users.

## Direct upgrade on your own timeline

If you choose to not have Microsoft manage the new Teams upgrade for you, pick a time that is best for you. Upgrade to new Teams by following the steps detailed in this article: [**Bulk upgrade to the new Teams client**](new-teams-bulk-install-client.md).

## Office 365 plans that don't include Microsoft Teams

Some Office 365 plans include Microsoft 365 Apps, but don't include the Teams service. Teams will still be installed with Microsoft 365 Apps even if a plan doesn't have the Teams service.

For Office 365 plans that don't include the Teams service, a free trial version of Teams, valid for one year, is available. Your users can start using it when they sign in to Teams. For more information about this free trial version and providing your users access, see Manage the Microsoft Teams Commercial Cloud Trial offer.
