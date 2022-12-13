---
title: Manage Teams transitioning to the new Teams admin center
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: 
ROBOTS: NOINDEX, NOFOLLOW
description: Learn how to manage tenant-wide and user settings for Teams during the transition from Teams in the Microsoft 365 admin center to the new Teams admin center.
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - ms.teamsadmincenter.dashboard.helparticle.manageteamsnewadmincenter
  - seo-marvel-mar2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
  - Skype for Business Online
---

# Manage Teams during the transition to the new Microsoft Teams admin center

> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

## What is the new Microsoft Teams admin center  

The new admin center experience will provide you with a unified experience to manage both Teams and Skype for Business. We're delivering additional functionality, end-to-end insights, and the ability to manage Teams settings on a user level.

![Screenshot of the Microsoft Teams admin center.](media/manage-teams-skype-for-business-admin-center-portal.png)

## Settings migrated to the new Microsoft Teams admin center

The following table identifies the sections of the Teams experience that have been migrated and shows the relationship between the current settings and the policies in the new admin portal.

|Section of Teams in Microsoft 365 admin center  |Setting name (Tenant level)  |Microsoft Teams admin center policy   |Level: Tenant or User   |
|---------|---------|---------|---------|
|General     |Show organizational chart in personal profile        |  [TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)       |  Tenant       |
|General     |Use Skype for Business for recipients who don't have Teams         |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Email integration     |Allow users to send emails to channels         |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Email integration     |Allow senders list         |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)        |Tenant         |
|Custom cloud storage     |Box         |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Custom cloud storage     |Dropbox        |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Custom cloud storage     |Egnyte        |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Custom cloud storage     |Google Drive        |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Custom cloud storage     |ShareFile        |[TeamsClientConfiguration](/powershell/module/skype/set-csteamsclientconfiguration)         |Tenant         |
|Settings by user/license type     |Turn Microsoft Teams on or off for all users          |Deprecated<sup>1</sup>        |         |
|Teams and channels     |         |Redirects to Azure Active Directory Group Management (same as current experience).              |User         |
|Teams and channels     |         |Redirects to AAD Group Management (same as current experience).             |User          |
|Apps|Enable new external apps by default|Org-wide app settings|Tenant|
|Apps|Allow external apps|Org-wide app settings|Tenant|
|Apps|Allow sideloading of external apps<sup>2</sup>|[TeamsAppSetupPolicy](/powershell/module/skype/set-csteamsappsetuppolicy)|User|
|Apps|Default apps<sup>3</sup>|TeamsAppPermissionPolicy|User|
|Apps|External apps<sup>3</sup>|TeamsAppPermissionPolicy|User|
|Calls and Meetings     |Allow scheduling for private meetings         |[TeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)         |User          |
|Calls and Meetings     |Allow Ad-hoc channel meetup         |[TeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)         |User          |
|Calls and Meetings     |Allow scheduling for channel meetings         |[TeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)         |User          |
|Calls and Meetings     |Allow videos in meetings         |[TeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)         |User          |
|Calls and Meetings     |Allow screen sharing in meetings         |[TeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)         |User          |
|Calls and Meetings     |Allow private calling         |[TeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)        |User          |
|Messaging     |Enable Giphy so users can add GIFs to conversations         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Content rating         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Enable memes that users can edit and add to conversations         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Enable stickers that users can edit and add to conversations         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Allow owners to delete all messages         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Allow users to edit their own messages         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Allow users to delete their own messages         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |
|Messaging     |Allows users to chat privately         |[TeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)         |User         |

<sup>1</sup> Deprecated for Guest. Enabling/disabling Guest can now be managed in the Microsoft Teams admin center. Enabling/disabling Teams for Business Enterprise, Edu Student, and Edu Faculty will be deprecated soon. This should be managed by assigning licenses in the Microsoft 365 admin center. See [Manage user access to Microsoft Teams](user-access.md).
<br><br>
<sup>2</sup> Sideloading is split as follows:

- Allow a user to sideload apps which can be managed at a user level in [TeamsAppSetupPolicy](/powershell/module/skype/set-csteamsappsetuppolicy).
- Allow users in a tenant to interact with custom apps which can be managed at a tenant level in org-wide app settings.

<sup>3</sup> Default apps and external apps can be enabled and disabled at the user level in TeamsAppPermissionPolicy. Additionally, apps can be blocked at the tenant level in org-wide app settings which overrides any user and tenant-level settings.

> [!NOTE]
> You'll continue to use the Groups dashboard in the Microsoft 365 admin center for configuration related to Teams and channels. Settings for Apps will remain in the Teams area of the Microsoft 365 admin center and will be migrated later.

## Manage settings during the migration

You can continue to modify settings in the Microsoft 365 admin center and the Skype for Business admin center until migration for a section is complete for your tenant.

The following table shows where you can manage features during the migration.

|Feature  |Microsoft Teams admin center                      |Skype for Business admin center (legacy)  |Microsoft 365 admin center  |
|---------|:---------:|:---------:|:---------:|
|Teams Messaging, Meetings, and Live Events policies     |     X    |         |         |
|Teams Upgrade policy     |    X     |         |         |
|Guest settings for Messaging, Meetings, and Voice     |   X      |         |         |
|Teams Lifecycle Management   |    X    |      |       |
|Teams Settings   |    X    |      |       |
|External access settings     |    X    |      |       |
|User management    |         |         |    X     |
|Audio conferencing     |    X     |    X     |         |
|Calling plans     |    X    |    X     |         |
|Phone System    |    X    |     X    |         |
|Phone number management     |    X    |   X      |         |
|Licensing for Cloud voice features     |         |         |    X     |
|Auto attendants     |    X    |          |         |
|Call queues     |    X    |          |         |

## Manage settings after the migration

When the migration of these settings is complete, we'll disable them in the Microsoft 365 admin center and the Skype for Business admin center, and they can then be managed in the new Microsoft Teams admin center.
