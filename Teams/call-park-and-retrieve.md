---
title: "Call park and retrieve in Microsoft Teams"
ms.author: lolaj
author: lolaj
manager: serdars
ms.date: 01/16/2019
ms.reviewer: srividhc
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
- Teams_ITAdmin_Help
- M365-voice
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
description: "Use call park and retrieve to place a call on hold in the Teams service in the cloud."
---

# Call park and retrieve in Microsoft Teams

Call park and retrieve is a feature that lets a user place a call on hold in the Teams service in the cloud. When a call is parked, the service generates a unique code for call retrieval. The user who parked the call or someone else can then use that code and a supported app or device to retrieve the call. 

Some of the common scenarios for using call park are: 

- A receptionist parks a call for someone working in a factory. The receptionist then announces the call and the code number over the public address system. The user who the call is for can then pick up a Teams phone on the factory floor and enter the code to retrieve the call.
- A user parks a call on a mobile device because the device battery is running out of power. The user can then enter then code to retrieve the call from a Teams desk phone.
- A support representative parks a customer call and sends an announcement on a Teams channel for an expert to retrieve the call and help the customer. An expert enters the code in Teams clients to retrieve the call

> [!IMPORTANT]
> This feature is only available in Teams Only deployment mode. For more details on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## License required

To park and retrieve calls, a user must be an Enterprise Voice user, and an administrator must grant the user a call park policy. For additional details on the licensing model, See [Office 365 licensing for Microsoft Teams](office-365-licensing.md).

## Call park and retrieve feature availability

Call park and retrieve is currently supported by the following clients and devices. (Supported in Teams Only mode, with or without PSTN connectivity.)

| Capability | Teams Desktop | Teams Mac App | Teams Web App (Edge) |Teams mobile iOS/Android App | Teams IP phone | Skype for Business IP phone |
|------------|---------------|---------------|----------------------|-----------------------------|----------------|-----------------------------|
| Park a call | Yes | Yes | Yes | Yes | Coming soon| No |
| Retrieve a parked call | Yes | Yes | Yes | Yes | Coming soon| No |
| Un-retrieved call ring back | Yes | Yes | Yes | Yes | Coming soon| No |

## Configuring call park and retrieve

You must be an administrator to configure call park and retrieve, and the feature is disabled by default. You can enable it for users and create user groups using the call park policy. When you apply the same policy to a set of users, they will be able to park and retrieve calls among themselves. To configure call park for users and create call park user groups, follow the procedure below.

For information about how to use the call park and retrieve feature, see [Park a call in Teams](https://support.office.com/article/park-a-call-in-teams-8538c063-d676-4e9a-8045-fc3b7299bb2f).

### Assign a call park policy

Follow these steps to assign a call park policy to one or more users:

1. Go to **Microsoft Teams admin center** > **Voice** > **Call park policies**.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you are finished adding users, select **Save**.
 
### Configure call park and retrieve with PowerShell

Use the [New-CsTeamsCallParkPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamscallparkpolicy?view=skype-ps) PowerShell cmdlet to create a call park policy.

Use the [Grant-CsTeamsCallParkPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamscallparkpolicy?view=skype-ps) PowerShell cmdlet to grant a call park policy.

You can change the default setting by using [Set-CsTeamsCallParkPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallparkpolicy?view=skype-ps) as follows:

`Set-CsTeamsCallParkPolicy -Identity Global -AllowCallPark $true`


## Troubleshooting

If users can’t see the park or retrieve button: 

- Check that the user has the Call Park policy enabled. 

If a user attempts to retrieve a call and is unsuccessful, check the following:

- Verify that the user is using the Teams client or a Teams-enabled device/Phone
- Grouping – is the user a member of the call park group?
- Island mode – Call park and retrieve is unavailable in Teams island mode.
- The call has already been retrieved or terminated.

## More information

[Park a call in Teams](https://support.office.com/article/park-a-call-in-teams-8538c063-d676-4e9a-8045-fc3b7299bb2f).