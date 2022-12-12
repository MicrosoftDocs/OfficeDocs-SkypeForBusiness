---
title: Quick start guide - Configuring Calling Plans
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 8/21/2018
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: rowille, crowe
search.appverid: MET150
f1.keywords:
- NOCSH
description: Quick start guide for configuring calling plans in Microsoft Teams so you can get a set of users up and running.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Quick start guide: Configuring Calling Plans in Microsoft Teams

This guide will help you get a set of users up and running so they can explore Calling Plans in Teams.

Read the December 12, 2017, announcement of Calling Plans in Teams: [Intelligent Communications takes the next step with calling in Teams](https://aka.ms/ipyqus)

> [!NOTE]
> We recommend that, in parallel with this quick-start guide, you read [Phone System with Calling Plans](calling-plan-landing-page.md) and [FastTrack](https://aka.ms/cloudvoice) to plan and drive a successful rollout.

By adding Calling Plans - a Microsoft 365 and Office 365 feature powered by Skype for Business - you can now use Teams to make and receive phone calls to or from land lines and mobile phones via the public switched telephone network (PSTN).

![Screen shot showing the Contacts page in Teams.](media/Calling_in_Teams.png)
## Prerequisites for enabling the **Calls** tab in Teams
To enable the **Calls** tab in Teams users need to have 1:1 calling enabled in Teams and using a Teams client that supports 1:1 Teams calling. To learn how to manage 1:1 calling in Teams, read [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy). To learn which clients support calling, please read [Limits and specifications for Microsoft Teams](./limits-specifications-teams.md).

> [!NOTE]
> Currently, Voicemail will not be available in the Calls tab unless the user is enabled for PSTN calls. 

## Prerequisites for enabling the **Dial Pad** in Teams
To enable the **Dial Pad** tab in Teams and allow your users to make and receive PSTN calls you will need to provision users for Phone System and Calling Plans. To learn how to set up Calling Plans, read [Set up Calling Plans](./set-up-calling-plans.md).
Additionally, for Teams only users, you must ensure that "Allow private calling" is enabled in the Teams calling policy. See [Manage Teams during the transition to the new Microsoft Teams admin center](./manage-teams-skypeforbusiness-admin-center.md) for more information.
> [!NOTE]
> You can also use Direct Routing to allow your users to make and receive PSTN calls. To learn how to set up Direct Routing, read [Configure Direct Routing](./direct-routing-configure.md).

## Using TeamsUpgradePolicy to control where calls land
To control whether incoming calls (and chats) land in Teams or Skype for Business, administrators use TeamsUpgradePolicy, using either [Microsoft Teams admin center](https://aka.ms/teamsadmincenter) or using a remote Windows PowerShell session with the [Skype for Business](/powershell/module/skype) cmdlets.


The default configuration of TeamsUpgradePolicy is Islands mode, which is designed to ensure that existing business workflows are not interrupted during a Teams deployment. By default, VoIP, PSTN, and federated calls to your users will continue to be routed to Skype for Business until you update the policy to enable inbound calling to Teams.  When recipients are in islands mode:

 - Incoming VOIP calls that originated in Skype for Business always land in the recipient's Skype for Business client.
 - Incoming VOIP calls that originated in Teams land in Teams, *if the sender and receiver are in the same tenant*.
 - Incoming federated VOIP (regardless of which client originates) and PSTN calls always land in the recipient's Skype for Business client.
 
To ensure that incoming VOIP and PSTN calls always land in a user's Teams client, update the user's coexistence mode to be TeamsOnly (which means, assign them the "UpgradeToTeams" instance of TeamsUpgradePolicy.  For more information on coexistence modes and TeamsUpgradePolicy, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](./migration-interop-guidance-for-teams-with-skype.md)

**NOTES**
 - Skype for Business IP phones will receive calls, even if the user is in TeamsOnly mode.  
 - Users that have been provisioned with Phone System and Calling Plans licenses for use with Skype for Business Online (e.g. they have been assigned a value of OnlineVoiceRoutingPolicy) , will have the Calls tab enabled in Teams and can place outbound PSTN calls from Teams without administrators having to take any administrative action.


### How to configure users to receive all incoming VOIP and PSTN calls in Teams
To ensure users receive all incoming VOIP and PSTN calls in Teams, set the user's coexistence mode to TeamsOnly in the Microsoft Teams admin center, or use Skype for Business remote Windows PowerShell session to update TeamsUpgradePolicy as follows:

```powershell
Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity user@contoso.com
```

## See also
[Set up Calling Plans](/SkypeForBusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](./migration-interop-guidance-for-teams-with-skype.md)

[Phone System with Calling Plans](calling-plan-landing-page.md)

[Skype for Business PowerShell cmdlet reference](/powershell/module/skype)
