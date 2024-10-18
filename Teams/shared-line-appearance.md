---
title: "Shared line appearance in Microsoft Teams"
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.date: 10/15/2024
ms.reviewer: ashgupt
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Phone System
  - ms.teamsadmincenter.users.voice.calldelegation.tooltip
  - seo-marvel-apr2020
description: Learn about the Shared line appearance feature in Microsoft Teams.
---

# Shared line appearance in Microsoft Teams

Shared line appearance lets a user choose a delegate to answer or handle calls on their behalf. This feature is helpful if a user has an administrative assistant who regularly handles the user's calls. In the context of shared line appearance, a manager is someone who authorizes a delegate to make or receive calls on their behalf. A delegate can make or receive calls on behalf of the delegator.

> [!IMPORTANT]
> This feature is only in Teams Only deployment mode. For more information on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## Dialing Permissions and Routing

When a delegate makes an outbound Public Switched Telephone Network (PSTN) call on behalf of a delegator, the delegator's settings control the checks for appropriate licensing, dial-out restrictions, and call routing.

## License required

Managers and delegates must have a Teams Phone license. Managers must have a phone number assigned, PSTN connectivity, and a required license for PSTN connectivity: Calling Plan, Operator Connect, or Direct Routing. The shared line experience is part of delegation and is included with Teams Phone. For more information on licensing, see [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description).

> [!NOTE]
> A delegate without a phone number assigned must be **EnterpriseVoiceEnabled** using the Teams PowerShell cmdlet `Set-CsPhoneNumberAssignment -Identity \<user\> -EnterpriseVoiceEnabled $true`, see [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment). If a Dial Pad shows in the Calls App of the Delegate, they're correctly configured for Enterprise Voice.  

## Shared line appearance feature availability

The following apps and devices currently support shared line appearance:

| Capability | Teams Desktop | Teams Mac App | Teams Web App (Edge) | Teams mobile iOS/Android App | Teams IP phone |
|--|--|--|--|--|--|
| Set up delegation | Yes | Yes | Yes | Yes | Yes |
| Receive calls on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a phone number on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a Teams user on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Join active calls | Yes | No | Yes | No | Yes |
| See the delegate view of shared lines | Yes | Yes | Yes | Yes | Yes |
| See the delegate view of manager's call activities | Yes | Yes | Yes | No | Yes |
| See the manager view of delegates | Yes | Yes | Yes | Yes | Yes |
| See shared call history | Yes | No | Yes | No | No|
| Delegate or manager can hold or resume | Yes | Yes | Yes | No | Yes |

## Limitations

Managers can add up to 25 delegates, and delegates can have up to 25 managers. There's no limit to the number of delegation relationships that can be created in a tenant.

If the delegator and delegate aren't in the same geographic location, the PSTN provider must allow caller ID to show up from a different geographic location for a delegated call.

Circular delegation configuration isn't permitted. If the delegated users also have delegations between them, they'll only be able to see their delegation and not the initial delegation.

## Enable delegation and shared line appearance

You enable delegation by using the **TeamsCallingPolicy AllowDelegation** setting. You can use Teams admin center or Teams PowerShell. This setting is turned on by default.

When enabled, the end user can configure their delegation relationships directly in Teams.

> [!IMPORTANT]
> When you turn off delegation for a user, you also need to clean up delegation relationships for that user in the Teams admin center to avoid incorrect call routing.

## Use Teams admin center

To configure delegation and shared line appearance:

1. In the navigation menu of the Microsoft Teams admin center, select **Voice** > **Calling policies**.

1. Choose the policy you would like to update or select **Add** to create a new policy.

1. Toggle **Delegation for inbound and outbound calls** on.  

1. Select **Save**.

## Use PowerShell

To configure delegation and shared line appearance by using Teams PowerShell, use the following cmdlets:

- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate)

- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate)

- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate)

- [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)

### Examples

In the following example, user2@contoso.com is added as a delegate of user1@contoso.com with permissions to make and receive call on behalf of user1, and to change settings for other delegates:

```powershell
New-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $true -ReceiveCalls $true -ManageSettings $true
```

In the next example, delegate user2@contoso.com isn't allowed to make calls anymore on behalf of user1:

```powershell
Set-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $false
```

In the next example, user2@contoso.com is removed as a delegate of user1@contoso.com:

```powershell
Remove-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com
```

## More information

[Share a phone line with a delegate](https://support.office.com/article/16307929-a51f-43fc-8323-3b1bf115e5a8)

[Configure Teams calling policy](/MicrosoftTeams/teams-calling-policy)

[New-CsTeamsCallingPolicy](/powershell/module/teams/new-csteamscallingpolicy)

[Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)
