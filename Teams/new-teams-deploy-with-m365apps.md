---
title:  Deploy new Microsoft Teams with Microsoft 365 Apps
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 09/06/2023
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
description: Learn about how to deploy new Microsoft Teams with Microsoft 365 Apps.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Deploy the new Microsoft Teams with Microsoft 365 Apps

Starting in late August, new Teams will automatically install with new and existing installations of Microsoft 365 Apps on Windows.

Currently, users can install the new Microsoft Teams using the "Try the new Teams" toggle switch in classic Teams or by Admins bulk deploying directly to the computers in their organization.

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


## How to exclude new Teams from new installations

Admins who don't want new Teams included with Microsoft 365 Apps on devices running Windows can follow these steps to opt out. 

1. Sign in to the Microsoft 365 Apps admin center (https://config.office.com) with an admin account. 
2. Go to **Customization > Device Configuration > Modern Apps Settings**. 
3. Select **Microsoft Teams (work or school)**,  then clear the **Enable automatic installation of new Microsoft Teams** check box. 

>[!Note]
>For the best Teams experience, we recommend leaving the setting as is. 

## Direct deploy on your own timeline

If you choose to not have Microsoft manage the new Teams deployment for you, pick a  time that is best for you. Deploy new Teams by following the steps detailed in this article: [**Bulk Deploy the new Teams client**](new-teams-bulk-install-client.md).


## Office 365 plans that don't include Microsoft Teams
 
Some Office 365 plans include Microsoft 365 Apps, but don't include the Teams service. Teams will still be installed with Microsoft 365 Apps even if a plan doesn't have the Teams service. 

For Office 365 plans that don't include the Teams service, a free trial version of Teams, valid for one year, is available. Your users can start using it when they sign in to Teams. For more information about this free trial version and providing your users access, see Manage the Microsoft Teams Commercial Cloud Trial offer. 