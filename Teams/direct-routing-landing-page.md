---
title: Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: filippse
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
search.appverid: MET150
f1.keywords: 
  - NOCSH
  - ms.teamsadmincenter.directrouting.overview
description: Learn about Teams Phone System with Direct Routing.
ms.custom: 
  - seo-marvel-apr2020
  - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Direct Routing

You've completed [Get started](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Maybe you've deployed [Meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md). Now you're ready to add voice workloads, and you've decided to use your own telephony carrier for Public Switched Telephone Network (PSTN) connectivity by using Phone System with Direct Routing. With Direct Routing, you can use Phone System with virtually any telephony carrier.

This article describes core deployment decisions for Direct Routing as well as additional considerations you may want to think about, based on your organization's needs. You should also read [Plan your voice solution](cloud-voice-landing-page.md) for more information about Microsoft's voice offerings.

## Learn more about Direct Routing

The following articles provide more information about configuring and using Direct Routing. Configuring Direct Routing requires understanding of PSTN routing design. You should read all of these articles to understand how to plan and configure Direct Routing:

- [Plan Direct Routing](direct-routing-plan.md) 
- [Configure Direct Routing](direct-routing-configure.md)
- [List of Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md)
- [Monitor and troubleshoot Direct Routing](direct-routing-monitor-and-troubleshoot.md)

In addition, you might want to read the following articles depending on your requirements:

-  [Configure a Session Border Controller for multiple tenants](direct-routing-sbc-multiple-tenants.md)
-  [Migrate to Direct Routing](direct-routing-migrating.md)
-  [User accounts in a hybrid environment with PSTN connectivity](direct-routing-user-accounts-in-a-hybrid-environment.md)
- Watch the following session to learn more about Direct Routing: [Direct Routing in Microsoft Teams](https://aka.ms/teams-direct-routing)

## Core deployment decisions

These are the core decisions to consider for Direct Routing. 

|Ask yourself|Action |
| :------------|:-------|
|For which users will I enable Direct Routing? | For more information, see [Enable users for Direct Routing Service](direct-routing-configure.md). |
Do I have the required licenses for Direct Routing? | For more information, see [Licensing and other requirements](direct-routing-plan.md#licensing-and-other-requirements).
|||

### Session Border Controller (SBC) considerations

With Direct Routing, you connect your own Session Border Controller (SBC) directly to Phone System. For a list of certified SBCs, see [Supported Session Border Controllers](direct-routing-border-controllers.md).

|Ask yourself|Action |
|:------------|:-------|
| Where and how will I deploy SBCs? | For more information, see [Configure Direct Routing](direct-routing-configure.md) | 
Do I have multiple tenants? | For more information, see [Configure a Session Border Controller for multiple tenants](direct-routing-sbc-multiple-tenants.md).|
|||

### Voice routing considerations

You'll need to configure Phone System to route the calls to the specific SBCs.

|Ask yourself|Action |
|:------------|:-------|
| What voice routing policies, PSTN usage, and voice routes do I need to create? | For voice routing  information, see [Configure Voice Routing](direct-routing-configure.md).
| Which users will be assigned to the voice routing policy that I define? | See the examples in [Configure Voice Routing](direct-routing-configure.md). |
|||

### Ensure incoming calls land in the Teams client using TeamsUpgradePolicy

Direct Routing is only supported with Microsoft Teams. To receive PSTN calls through Direct Routing, you need to configure TeamsUpgradePolicy to ensure incoming calls are received in Teams. Users must be in TeamsOnly mode, which you can do by assigning them the "UpgradeToTeams" instance of TeamsUpgradePolicy. 

|Ask yourself|Action |
|:------------|:-------|
|What does TeamsOnly mode mean? | For more information, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](./migration-interop-guidance-for-teams-with-skype.md).|
|||


