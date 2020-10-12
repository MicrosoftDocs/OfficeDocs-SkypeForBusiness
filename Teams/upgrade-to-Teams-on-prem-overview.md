---
title: Upgrade to Teams from a Skype for Business on-premises deployment - Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/16/20
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Upgrade from Skype for Business to Teams  
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from Skype for Business to Teams &mdash; for IT administrators

## Overview

When upgrading from Skype for Business to Teams, some organizations require a progressive rollout that is planned and managed by their IT departments. The articles in this section apply primarily to IT administrators in large organizations. These organizations are typically on-premises, but they might also be large Skype for Business Online organizations. Before reading these articles, be sure to read [Getting started with your Teams Upgrade](upgrade-start-here.md) and [About the Upgrade framework](upgrade-framework.md).


The following articles will guide you through the upgrade process for your organization: 

- [Upgrade methods](upgrade-to-teams-on-prem-upgrade-methods.md)
- [Tools for managing your upgrade](upgrade-to-teams-on-prem-tools.md)
- [Additional considerations for organizations with Skype for Business on-premises](upgrade-to-teams-on-prem-considerations.md)
- [Implement your upgrade](upgrade-to-teams-on-prem-implement.md)
- [Public Switched Telephone Network (PSTN) considerations](upgrade-to-teams-on-prem-pstn-considerations.md)

In addition, the following articles describe important upgrade concepts and coexistence behaviors:

- [Coexistence of Teams and Skype for Business](upgrade-to-teams-on-prem-coexistence.md)
- [Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)
- [Teams client experience and conformance to coexistence modes](teams-client-experience-and-conformance-to-coexistence-modes.md)

>[!NOTE]
>These articles use the terms Skype for Business Online, Skype for Business Server on-premises, and Skype for Business. The latter term refers to both online and on-premises versions.

Before you get started, be aware that a user who has been migrated to Teams no longer uses a Skype for Business client except to join a meeting hosted in Skype for Business.  All incoming chats and calls land in the user’s Teams client, regardless of whether the sender uses Teams or Skype for Business. Any new meetings organized by the migrated user will be scheduled as Teams meetings. If the user attempts to use the Skype for Business client, initiation of chats and calls is blocked.  However, the user can (and must) still use the Skype for Business client to join Skype for Business meetings they are invited to. (Older Skype for Business clients that shipped before 2017 do not honor TeamsUpgradePolicy. Make sure you are using the latest Skype for Business client.)
 
You manage your user's transition to Teams using the concept of [mode](migration-interop-guidance-for-teams-with-skype.md), which is a property of [TeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps). A user who has been migrated to Teams as described above is in “TeamsOnly” mode.  For an organization that is migrating to Teams, the ultimate goal is to move all users to TeamsOnly mode.

>[!NOTE]
>Users who have a Skype for Business on-premises account cannot be TeamsOnly. Although these users can [use Teams in Islands mode](https://docs.microsoft.com/microsoftteams/migration-interop-guidance-for-teams-with-skype), this does not provide the full set of Teams functionality that is available in TeamsOnly mode. To make these users TeamsOnly, they must be moved to the cloud using `Move-CsUser` in the on-premises Skype for Business Server tools.

OK. Let's get started.  The first step is understanding the [upgrade methods available to you](upgrade-to-teams-on-prem-upgrade-methods.md).







   

## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)

