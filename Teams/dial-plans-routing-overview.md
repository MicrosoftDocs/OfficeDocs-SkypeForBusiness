---
title: "Microsoft Teams Dial plans and routing"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 10/02/2023
ms.topic: article
ms.assetid: aa2ec464-3481-4bbb-8c14-e13e18093df5
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: Medium
f1.keywords:
- CSH

description: "Dial plans and routing in Microsoft Teams"
---

# Microsoft Teams Dial plans and routing

The articles in this section describe dial plans and call routing in Microsoft Teams.

- [What are dial plans](what-are-dial-plans.md)
- [Create and manage dial plans](create-and-manage-dial-plans.md)
- [Route calls to unassigned numbers](routing-calls-to-unassigned-numbers.md)

The articles in this section apply to all options for connecting to the Public Switched Telephone Network (PSTN): Calling Plan, Operator Connect, Teams Phone Mobile, and Direct Routing. For more information about all PSTN connectivity options, see [PSTN connectivity options](pstn-connectivity.md).

## Dial plans and routing considerations

If you choose Calling Plan, Operator Connect, or Teams Phone Mobile, most call routing is handled by either Microsoft or your provider. Direct Routing, however, requires additional steps to configure call routing.

For Direct Routing, you must configure call routing by specifying the voice routes and assigning voice routing policies to users. You can configure dial plans for number translation at the trunk level to ensure interoperability with Session Border Controllers (SBCs). For more information, see [Configure voice routing for Direct Routing](direct-routing-voice-routing.md), [Manage voice routing policies](manage-voice-routing-policies.md) and [Translate phone numbers](direct-routing-translate-numbers.md).

You can assign a Direct Routing online voice routing policy to Calling Plan and Operator Connect users. You might want to do this, for example, to enable users to dial in to a call center directly. You can set up a Direct Routing trunk to the call center.

If a user has a Calling Plan license, for example, that user’s outgoing calls are automatically routed through the Microsoft Calling Plan PSTN infrastructure. If you configure and assign a Direct Routing online voice routing policy to the user, the user’s outgoing calls are checked to determine whether the dialed number matches a number pattern defined in the online voice routing policy. If there’s a match, the call is routed through the Direct Routing trunk. If there’s no match, the call is routed through the Calling Plan PSTN infrastructure.

For more information, see [Direct Routing voice routing policy considerations](direct-routing-voice-routing.md#voice-routing-policy-considerations).

## Match dialed number to user

A process called **Reverse Number Lookup (RNL)** uses strict string matching to find a user or resource account that matches the dialed number for an incoming PSTN call. For example, assume that a user is assigned the phone number +14255551212. If a PSTN caller has dialed +14255551212, RNL finds the user and the call is connected to that user. However, if the +14255551212 number hasn't been assigned to a user or resource account, the call will fail to route or be routed according to [unassigned number routing](routing-calls-to-unassigned-numbers.md), if configured.

If you want internal users who call a phone number that assigned to a resource account to be connected to that number on the PSTN instead of the resource account it's assigned to, you can enable the skip RNL option for the phone number by changing the phone number assignment by using the **Set-CsPhoneNumberAssignment** PowerShell cmdlet with `-ReverseNumberLookup`. For more information, see [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) and [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment).

## Related topics

[PSTN connectivity options](pstn-connectivity.md)

[What are dial plans](what-are-dial-plans.md)

[Create and manage dial plans](create-and-manage-dial-plans.md)

[Route calls to unassigned numbers](routing-calls-to-unassigned-numbers.md)
