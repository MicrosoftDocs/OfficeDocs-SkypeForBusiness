---
title: "Create a call queue in Microsoft Teams"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
    - seo-marvel-apr2020
description: Learn how to set up call queues for large organizations in Microsoft Teams, which provides a greeting message, hold music, call redirecting, and other features.
---
# Create a call queue

Call queues provide a method of routing callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue (who are known as *agents*).

> [!TIP]
> This article is for large organizations. If your organization is a small business, read [Create a call queue - small business tutorial](/microsoftteams/business-voice/create-a-phone-system-call-queue-smb) instead.

[!INCLUDE [create-call-queue-steps](./includes/create-call-queue-steps.md)]

## Summary of recommended call queue settings

The following settings are recommended:

- **Conference mode** to **On**
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to **20 seconds**

## Call queue feature compatibility

|Feature                          |Teams Desktop<sup>1</sup> |Teams Mobile<sup>2</sup> |Lync |IP Phones | Standard Call Queues |Channel Based Call Queues | Comment |
|:--------------------------------|:------------------------:|:-----------------------:|:---:|:--------:|:--------------------:|:------------------------:|:-------------|
|**Agent Routing Methods**        |                          |                         |     |          |                      |                          |              |
|`Attendant Routing`              |Y                         |Y                        |Y    |Y         |Y                     |Y                         |*Default*     |
|`Longest Idle`<sup>3</sup>       |Y                         |Y                        |N    |Y         |Y                     |Y                         |*Recommended* |
|`Round Robin`                    |Y                         |Y                        |Y    |Y         |Y                     |Y                         |*Recommended* |
|`Serial`                         |Y                         |Y                        |Y    |Y         |Y<sup>4</sup>         |Y<sup>4</sup>             |              |
|**Transfer Modes**               |                          |                         |     |          |                      |                          |              |
|`Conference Mode`<sup>5</sup>    |Y                         |Y                        |N    |Y<sup>6</sup>|Y                  |Y                         |*Recommended* |
|`Transfer Mode`                  |Y                         |Y                        |Y    |Y         |Y                     |Y                         |              |
|Presence Based Routing<sup>3</sup>|Y                        |Y                        |N    |Y         |Y                     |Y                         |*Recommended* |
|Agents can Opt-out               |Y                         |Y                        |Y<sup>7</sup>|Y<sup>7</sup>|Y          |Y                         |*Default*     |
|Channel Based Queues             |Y                         |N                        |N    |N         |n/a                   |Y<sup>8</sup>             |              |
|Call toast shows Resource Account Name |Y<sup>9</sup>       |Y                        |Y    |          |Y                     |Y                         |              |
|**Dynamic caller ID**            |                          |                         |     |          |                      |                          |              |
|`Standard call queue`            |N                         |Y                        |N    |N         |Y                     |n/a                       |              |
|`Channel based call queue`       |Y                         |n/a                      |n/a  |n/a       |n/a                   |Y                         |              |
|**PSTN Connectivity Methods**    |                          |                         |     |          |                      |                          |See Note 10   |
|`Calling Plans`                  |Y                         |Y                        |Y    |Y         |Y                     |Y                         |              |
|`Direct Routing`                 |Y                         |Y                        |N    |N         |Y                     |Y                         |              |
|`Operator Connect`               |Y                         |Y                        |     |          |Y                     |Y                         |              |

Notes:

1. Microsoft Teams Windows client, Microsoft Teams Mac Client, Microsoft Teams on Virtualized Desktop Infrastructure, Microsoft Teams Web client.
2. Microsoft Teams iPhone app, Microsoft Teams Android app.
3. Selecting Longest Idle for the agent routing method will automatically enable Presence based routing.
4. Can only set the order when adding individual users as part of standard call queues. When a distribution list or Teams Channel is used order will be alphabetical.
5. Conference mode is not supported if phone calls are routed to the queue from a Direct Routing gateway that is enabled for Location Based Routing.
6. Microsoft Teams phone only.
7. Via the User Settings Portal page at https://aka.ms/vmsettings
8. Only public channels are supported.
9. Excluding Teams Web client.
10. Auto Attendants and Call Queues cannot transfer calls between PSTN connectivity methods.

## Supported clients

The following clients are supported for call agents in a call queue:

- Skype for Business desktop client 2016 (32-bit and 64-bit versions)
- Lync desktop client 2013 (32-bit and 64-bit versions)
- All IP phone models supported for Microsoft Teams. See [Getting phones for Skype for Business Online](/skypeforbusiness/what-is-phone-system-in-office-365/getting-phones-for-skype-for-business-online/getting-phones-for-skype-for-business-online).
- Mac Skype for Business Client (version 16.8.196 and later)
- Android Skype for Business Client (version 6.16.0.9 and later)
- iPhone Skype for Business Client (version 6.16.0 and later)
- iPad Skype for Business Client (version 6.16.0 and later)
- Microsoft Teams Windows client (32-bit and 64-bit versions)
- Microsoft Teams Mac client
- Microsoft Teams on [Virtualized Desktop Infrastructure](/microsoftteams/teams-for-vdi) (Windows Virtual Desktop, Citrix, and VMware)
- Microsoft Teams iPhone app
- Microsoft Teams Android app

  > [!NOTE]
  > Call queues that are assigned a direct routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents. The Teams client is only supported with a [co-existence mode of Teams Only](/microsoftteams/setting-your-coexistence-and-upgrade-settings).

## Call queue cmdlets

Windows PowerShell allows you to create and manage call queues via the command line in a batch or programmatic manner.

The following cmdlets allow you to manage a call queue:

- [New-CsCallQueue](/powershell/module/skype/New-CsCallQueue)
- [Get-CsCallQueue](/powershell/module/skype/Get-CsCallQueue)
- [Set-CsCallQueue](/powershell/module/skype/Set-CsCallQueue)
- [Remove-CsCallQueue](/powershell/module/skype/Remove-CsCallQueue)

The following additional cmdlets are also required to manage the users, resource accounts, Microsoft Teams Phone licenses, phone numbers, audio files, and supported language that will be used with call queues:

Users/Teams

- Users
  - [Get-CsOnlineUser](/powershell/module/skype/Get-CsOnlineUser)

- Teams:
  - [Get-Team](/powershell/module/teams/Get-Team)
  - [Get-TeamChannel](/powershell/module/teams/Get-TeamChannel)

Resource accounts:

- [New-CsOnlineApplicationInstance](/powershell/module/skype/New-CsOnlineApplicationInstance)
- [Find-CsOnlineApplicationInstance](/powershell/module/skype/Find-CsOnlineApplicationInstance)
- [Get-CsOnlineApplicationInstance](/powershell/module/skype/Get-CsOnlineApplicationInstance)
- [Set-CsOnlineApplicationInstance](/powershell/module/skype/Set-CsOnlineApplicationInstance)
- [New-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/New-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociation)
- [Remove-CsOnlineApplicationInstanceAssociation](/powershell/module/skype/Remove-CsOnlineApplicationInstanceAssociation)
- [Get-CsOnlineApplicationInstanceAssociationStatus](/powershell/module/skype/Get-CsOnlineApplicationInstanceAssociationStatus)

Virtual Teams Phone licenses:

- [Get-MsolAccountSku](/powershell/module/msonline/get-msolaccountsku)
- [Set-MsolUserLicense](/powershell/module/msonline/set-msoluserlicense)

Phone number assignment:

- [Get-CsOnlineTelephoneNumber](/powershell/module/skype/Get-CsOnlineTelephoneNumber)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/Set-csphonenumberassignment)

Audio Files

- [Get-CsOnlineAudioFile](/powershell/module/skype/Get-CsOnlineAudioFile)
- [Import-CsOnlineAudioFile](/powershell/module/skype/Import-CsOnlineAudioFile)
- [Export-CsOnlineAudioFile](/powershell/module/skype/Export-CsOnlineAudioFile)
- [Remove-CsOnlineAudioFile](/powershell/module/skype/Remove-CsOnlineAudioFile)

Support Language Lists

- [Get-CsAutoAttendantSupportedLanguage](/powershell/module/skype/Get-CsAutoAttendantSupportedLanguage)

For a step-by-step guide to creating call queues with PowerShell, see [Creating Call Queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md)

## Call Queue Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that a call queue is able to receive calls:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Queue](https://aka.ms/TeamsCallQueueDiag)

2. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant, policy, and resource account configurations to validate that the call queue is able to receive calls.

## Related topics

[Here's what you get with Microsoft Teams Phone](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
