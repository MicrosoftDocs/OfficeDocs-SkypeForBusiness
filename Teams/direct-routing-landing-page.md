---
title:  Phone System Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/07/2019
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: crowe
search.appverid: MET150
description: Landing page for Direct Routing
appliesto: 
- Microsoft Teams
---

# Phone System Direct Routing

You've completed the [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Maybe you've deployed [Meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md). Now you're ready to add cloud voice workloads, and you've decided to use your own telephony carrier for PSTN connectivity by using Phone System Direct Routing. With Direct Routing, you can use Phone System with virtually any telephony carrier.

This article describes [core deployment considerations](#core deployment considerations) for Direct Routing as well as [additional considerations](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Learn more about Direct Routing

The following articles provide more information about deploying and using Phone System Direct Routing in Teams:

- [Plan Direct Routing](direct-routing-plan.md)
- [List of Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md)
- [Configure Direct Routing](direct-routing-configure.md)
- [Migrate to Direct Routing](direct-routing-migrate.md)
- [Configure a Session Border Controller for multiple tenants](direct-routing-sbc-multiple-tenants.md)


## Core deployment decisions

These are the decisions to consider for Direct Routing. that most organizations want to change (if the Teams default settings don't work for the organization).


|Ask yourself|Action |
|------------|-------|
|<ul><li>For which users will I enable Direct Routing? </li><li>Do I have the required licenses for Direct Routing?</li></ul>|<ul><li>For more information about Direct Routing, see [Make my service decisions - Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md) and [Plan for Direct Routing](direct-routing-plan.md).</li></ul>|
|||

### Session Border Controller (SBC) considerations

With Direct Routing, you connect your own Session Border Controller (SBC) directly to Phone System.  For a list of certified SBCs, see [Supported Session Border Controllers](direct-routing-plan.md#supported-session-border-controllers-sbcs).

|Ask yourself|Action |
|------------|-------|
| Where and how will I deploy SBCs? | For more information, see [Deploy and configure the SBC](direct-routing-sbc-multiple-tenants.md#deploy-and-configure-the-sbc).|
|||

### Voice routing considerations

With Direct Routing, you'll need to configure Phone System to route the calls to the specific SBCs.

|Ask yourself|Action |
|------------|-------|
|<ul><li>What voice routing policies, PSTN usage, and voice routes do I need to create?</li><li>Which users will be assigned to the voice routing policy that I define?</li></ul> | For voice routing policy information, see [Configure Voice Routing](direct-routing-configure.md#configure-voice-routing).</li></ul> |
|||

### Calling and interop policies

Direct Routing is only supported with Microsoft Teams. To place or receive PSTN calls through Direct Routing, you need to configure the necessary policies to ensure incoming calls are received in Teams. You can configure users to set Teams as their preferred client for calls by either configuring the user for Teams Only mode or configuring Teams as the preferred calling client by assigning the TeamsCallingPolicy and the TeamsInteropPolicy.

|Ask yourself|Action |
|------------|-------|
|How will I set Teams as the preferred client for calls? |For more information, see [Calling and interop policies](2-envision-make-my-service-decisions-direct-routing.md#calling-and-interop-policies). |
|||

## Additional deployment considerations

You may want to change settings for the following, based on your organization's needs and configuration:

| Ask yourself| Action |
| :------------|-------:|
| Do you have an existing Skype for Business Server deployment with hybrid connectivity configured? |  To understand how user accounts in a hybrid environment are provisioned and managed, see [User accounts in a hybrid environment with PSTN connectivity](direct-routing-user-accounts-in-a-hybrid-environment).| 
| Are you migrating to Direct Routing from Calling Plan or from a Skype for Business on-premises environment? | To understand more about migrating to Direct Routing from an existing environment, see [Migrating to Direct Routing](direct-routing-migrating.md) |
|||
