---
title: Configure Operator Connect for Audio Conferencing
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.date: 09/30/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about how to configure Operator Connect for Audio Conferencing.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Operator Connect for Audio Conferencing

This article describes how to configure Operator Connect for Audio Conferencing. Before configuring Operator Connect for Audio Conferencing, be sure to read [Plan for Operator Connect Conferencing](operator-connect-conferencing-plan.md) for information about prerequisites and licensing.

The topics covered below include:

- [Enable an operator](#enable-an-operator)
- [Acquire numbers for your Audio Conferencing bridge](#acquire-numbers-for-your-audio-conferencing-bridge)
- [Change the default phone numbers that are included in the meeting invites of users](#change-the-default-phone-numbers-that-are-included-in-the-meeting-invites-of-users)
- [Sending outbound calls from Microsoft Teams meetings via an operator](#sending-outbound-calls-from-microsoft-teams-meetings-via-an-operator)
- [Manage your operators](#manage-your-operators)
- [Release numbers from your Audio Conferencing bridge](#release-numbers-from-your-audio-conferencing-bridge)
- [Additional information on Microsoft Audio Conferencing](#additional-information-on-microsoft-audio-conferencing)

## Enable an operator

You can enable, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then, select the operator you want to enable. For Operator Connect Conferencing, verify that your operator has **Conferencing** listed as an available product.

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information** Your contact information, including your full name and email address, will be shared automatically with your operator. You can change this information later. Additionally, you'll need to provide company size, and you'll have the option to provide your phone number. Operators will use this information to contact you with more details about Operator Connect Conferencing.

4. Accept the data transfer notice.

5. **Add your operator.** Select **Add as my operator** to save.

## Acquire numbers for your Audio Conferencing bridge

The Audio Conferencing bridge of your organization includes the phone numbers that are available to all users in your organization to join Microsoft Teams meetings via phone numbers. You can see the phone numbers that are associated to the Audio Conferencing bridge of your organization in the Teams Admin Center under **Meetings > Conference Bridges**.

To acquire phone numbers for your Audio Conferencing bridge, follow these steps:

1. **Audio Conferencing or Operator Connect Conferencing license.** Users that need Operator Connect Conferencing numbers to join the meetings that they organize need to have an Audio Conferencing Standard subscription license or an Operator Connect Conferencing license assigned to them. For additional information, see [Plan for Operator Connect Conferencing](operator-connect-conferencing-plan.md).

2. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, go to the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information. Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**.

3. **Assign numbers to your Audio Conferencing bridge.** You can assign numbers to your Audio Conferencing bridge from the Teams admin center under **Meetings > Conference Bridges > Add**. For more information, see [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

>[!NOTE]
>Operator Connect Conferencing numbers can’t be assigned as default numbers of a bridge. Once a phone number is assigned to your Audio Conferencing bridge, the number will be listed in the **Find a local number page** of your organization that is included in the meeting invites of users in your organization with an Audio Conferencing license or an Operator Connect Conferencing license.
>
>To route outbound calls via an operator, see the [**Sending outbound calls from Teams meetings via an operator**](#sending-outbound-calls-from-microsoft-teams-meetings-via-an-operator) section further down in this article.

## Change the default phone numbers that are included in the meeting invites of users

This is an optional step.

The default phone numbers of a user are the ones that are included in their meeting invites when they schedule a meeting. You can update the phone numbers that are included in the meeting invites of users in the Teams Admin Center under **Users > Manage users**. To update the phone numbers included in the meeting invites of users, select the user, and select **Edit** in the **Audio Conferencing** section.

After the changes have been applied, the new default phone numbers will be included in the meeting invites of organizers when they schedule a new meeting.

## Sending outbound calls from Microsoft Teams meetings via an operator

If you have a Microsoft Audio Conferencing Standard subscription, you can configure the Audio Conferencing service to route all or a set of outbound calls from Teams meetings via your operator (as opposed to via Microsoft) by setting up an Audio Conferencing Routing policy.

With an Operator Connect Conferencing license, outbound calls can only go through your operator.

An Audio Conferencing Routing policy can be applied at a user level, meaning that only the outbound calls from Teams meetings organized by the users with the associated policy will be routed via your operator, or at the global level, meaning that the outbound calls from Teams meetings organized by all users in your organization will be routed via your operator.

Audio Conferencing Routing policies can only be created using PowerShell. To create an Audio Conferencing Routing policy and specify an operator as the primary route for outbound calls from Teams meetings, you can use the following PowerShell commands:

### Add a new string to the Online PSTN Usage policy

Read [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage) for more information on using this cmdlet.

```PowerShell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="International"}
```

### Create a new Online Voice Route policy

Read [Set-CsOnlineVoiceRoute](/powershell/module/skype/set-csonlinevoiceroute) for more information on using this cmdlet.

```powershell
New-CsOnlineVoiceRoute -Identity "International" -NumberPattern "\d+" -OnlinePstnUsages "International" -BridgeSourcePhoneNumber <an Operator Connect Conferencing number assigned to your Audio Conferencing bridge>
```

### Create a new Online Audio Conferencing Routing policy

Read [New-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/new-csonlinevoiceroutingpolicy) for more information on using this cmdlet.

```powershell
New-CsOnlineAudioConferencingRoutingPolicy "International Policy" -OnlinePstnUsages "International"
```

### Assign the new policy to users

Read [Grant-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/grant-csonlinevoiceroutingpolicy) for more information on using this cmdlet.

```powershell
Grant-CsOnlineAudioConferencingRoutingPolicy -Identity <identity of the organizer of the meeting> -PolicyName "International Policy”
```

>[!NOTE]
>To set an Audio Conferencing Routing policy as global and apply it to all users in your organization, you can use the ``-Global`` parameter instead of the ``-Identity`` parameter. For example, ``Grant-CsOnlineAudioConferencingRoutingPolicy -Global -PolicyName "International Policy”``.

When the Audio Conferencing Routing policy is created and applied to a user, the outbound calls from Microsoft Teams meetings will be routed via the operator that is the provider of the phone number specified in the ``BridgeSourcePhoneNumber`` parameter. Additionally, the phone number specified in the ``BridgeSourcePhoneNumber`` will be used as the calling line identification phone number of outbound calls from Microsoft Teams meetings.

The pattern specified in the ``NumberPattern`` is of regex form, and it specifies which calls the policy will be applied to, meaning which calls will be routed via your operator. The ``"\d+"`` pattern specified in the example above matches all outbound calls from Teams meetings. Other examples that can be used in the NumberPattern parameter are ``“^\+1(425|206)(\d{7})$”``, which matches dialed numbers with the following formats: +1 425 XXX XX XX or +1 206 XXX XX XX, or ``“^\+1(\d{10})$”``, which matches dialed numbers with the following format: +1 425 XXX XX XX.

Once an Audio Conferencing Routing policy has been assigned to a user, all calls from their meetings to a phone number that matches the regex specified in their Audio Conferencing Routing policy will be routed via your operator, including **Call me at** calls and calls initiated via the **Invite someone or dial a number** meeting option.

## Manage your operators

From the **My operators** tab, you can view your operators, their status, and make the following changes to your selections:

- Manage operator services by country
- Suspend an operator
- Remove an operator

>[!NOTE]
>Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to the users and your Audio Conferencing bridge, then contact the operator to release the numbers.

## Release numbers from your Audio Conferencing bridge

To release phone numbers from your Audio Conferencing bridge from the Teams admin center, see **Steps when you are unassigning a service phone number for a conferencing bridge** in [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#steps-when-you-are-unassigning-a-service-phone-number-for-a-conferencing-bridge).

## Additional information on Microsoft Audio Conferencing

The Microsoft Audio Conferencing service enables participants to join Microsoft Teams meetings by dialing in via a phone number or by dialing out to a phone number. The Microsoft Audio Conferencing service has multiple capabilities to meet the needs of your organization. For additional information on how the Microsoft Audio Conferencing service works and the capabilities available to your organization, please refer to the following articles.

- Overview of the Microsoft Audio Conferencing service: [Audio Conferencing in Microsoft 365](audio-conferencing-in-office-365.md)

- Managing the Microsoft Audio Conferencing service settings for your organization: [Manage the Audio Conferencing settings for your organization in Microsoft Teams](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md)

- Managing the Microsoft Audio Conferencing service setting of the users in your organization: [Manage the Audio Conferencing settings for a user in Microsoft Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md)

- Changing the auto attendant languages of your Audio Conferencing phone numbers: [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md)
