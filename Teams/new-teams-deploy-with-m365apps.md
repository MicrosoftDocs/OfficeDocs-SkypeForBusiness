---
title:  Deploy new Microsoft Teams with Microsoft 365 Apps
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 06/30/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about how to deploy new Microsoft Teams with Microsoft 365 Apps.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Deploy the new Microsoft Teams with Microsoft 365 Apps

Starting in late August, new Teams will be part of new and existing installations of Microsoft 365 Apps on Windows.

Currently, users can install the new Microsoft Teams using the "Try the new Teams" toggle switch in classic Teams or by Admins "bulk" deploying directly to the computers in their organization.

Administrators will be able exclude installing new Teams with their Micrososft 365 Apps deployment if they choose.

>[!Important]
>If the classic Teams app is already installed, the Microsoft 365 Apps deployment will install new Teams alongside classic Teams on the device. The classic Teams installation will not change.

## Is the new Teams available for my organization?

>[!Note]
>New Teams client for **Education (EDU)** is rolling out starting June 29, 2023, and is expected to complete over the following weeks.

The new Teams client **is not** yet available for the following customers but is planned for release later in this calendar year:

**Platforms:**  Mac, VDI, Web</br>
**Customer segments:**  </br>- Government clouds: GCC, GCC High, DoD</br>- Special cloud: Air-gapped, Microsoft 365 operated by 21Vianet in China </br>- Consumer


## Rollout schedule 

#### When will the new Microsoft Teams be included with the new installations of Microsoft 365 Apps?

The date when the new Teams starts being installed with Microsoft 365 Apps depends on which update channel you're using. The following table shows the schedule.

**Starting mid-to late August 2023**, the planned rollout will be:


|License|Target date|
|:-----|:-----|
|Business plans (for example, Business Basic, Business Standard, Business Premium, and Teams Essentials (AAD), etc.)|Late July – early August  2023 |
|Enterprise plans (for example, E3, E5, F3, etc.)|See schedule below.|


##### Update channels

>[!Tip]
>Learn more about update channels, including how to make changes here:
> - [**Update channels for Microsoft 365 apps**](/deployoffice/updates/overview-update-channels)

If the update channel isn't listed, then the Monthly Enterprise Channel schedule is followed.

|Update channel|Date|
|:-----|:-----|
Public preview program|Available|
|Targeted release program|Available|
|Current Channel|August 2023|
|Monthly Enterprise Channel|Mid September 2023|
|Semi-Annual Enterprise Channel (Preview)|August 2023|
|Semi-Annual Enterprise Channel, Semi-annual Extended, LTSC and remaining channels|Early November 2023|

>[!Note]
>- Teams for Government includes GCC, GCCH, DoD and other special clouds follow the schedule for the Semi-Annual channels
>- New Teams is not currently available on VDI and Mac OS but is planned for release later in this calendar year


#### When will the new Teams become the default app?

**Starting September 2023**

For new Teams apps included in Microsoft 365 Apps installations, Microsoft begins making the new Teams the default app starting in late September 2023. The planned rollout will be:

|License|Target date|
|:-----|:-----|
|Business plans (including Business Basic, Business Standard, Business Premium, and Teams Essentials (AAD))|Late September 2023|
|Enterprise plans (for example, E3, E5, F3, etc.)| |


##### Licenses

|License|Date|
|:-----|:-----|
|Business Licenses and Teams Essentials|Mid September 2023
|Enterprise and other Licenses|See the schedule listed below.|

##### Update channels

If the update channel isn't listed, then the Monthly Enterprise Channel schedule is followed.

|Update channel|Date|
|:-----|:-----|
|Teams Public Preview|Mid August 2023|
|Targeted Release Channel|Mid August 2023|
|Current Channel|Early October 2023|
|Monthly Enterprise Channel|Early November 2023|
|Semi-Annual Enterprise Channel (Preview)|Early October 2023|
|Semi-Annual Enterprise Channel, Semi-annual Extended, LTSC, and remaining channels|Mid January 2023|



## How to exclude new Microsoft Teams from new installations of Microsoft 365 Apps 

If you don't want new Teams included with Microsoft 365 Apps on devices running Windows,  follow these steps to opt out. 

1. Sign in to the Microsoft 365 Apps admin center (https://config.office.com) with an admin account. 
2. Go to **Customization > Device Configuration > Modern Apps Settings**. 
3. Select **Microsoft Teams (work or school)**,  then clear the **Enable automatic installation of new Microsoft Teams** check box. 

>[!Note]
>For the best Teams experience, we recommend leaving the setting as is. 

## Direct deploy separately

If you prefer to not install new Teams as part of the Microsoft 365 Apps deployment, you can do so separately.If

Admin choices are essentially

- [default] Microsoft will take care of Teams deployment for you
-  Deploy new Teams yourself
- (don't deploy new Teams)Follow the steps in [**Bulk deployment of new Teams**](new-teams-bulk-install-client.md).


## What about Office 365 plans that don't include Microsoft Teams? 
 
Some Office 365 plans include Microsoft 365 Apps, but don't include the Teams service. Teams will still be installed with Microsoft 365 Apps even if a plan doesn't have the Teams service. 

For Office 365 plans that don't include the Teams service, a free trial version of Teams, valid for one year, is available. Your users can start using it when they sign in to Teams. For more information about this free trial version and providing your users access, see Manage the Microsoft Teams Commercial Cloud Trial offer. 