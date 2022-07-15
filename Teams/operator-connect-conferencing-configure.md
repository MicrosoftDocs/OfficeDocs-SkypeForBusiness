---
title: Configure Operator Connect Conferencing
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
description: Learn more about how to configure Operator Connect Conferencing.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Operator Connect Conferencing

This article details how to configure Operator Connect Conferencing for your organization and users.

Before configuring Operator Connect Conferencing, read [Plan for Operator Connect Conferencing](operator-connect-conferencing-plan.md) for information about benefits and licensing requirements.

The topics covered in this article include:

- [Set up an operator](#set-up-an-operator)
- [Acquire numbers for your Audio Conferencing bridge](#acquire-numbers-for-your-audio-conferencing-bridge)
- [Change the default phone numbers that are included in the meeting invites of users](#change-the-default-phone-numbers-that-are-included-in-the-meeting-invites-of-users)
- [Sending outbound calls from Microsoft Teams meetings through an operator](#sending-outbound-calls-from-microsoft-teams-meetings-through-an-operator)
- [Manage your operators](#manage-your-operators)
- [Release numbers from your Audio Conferencing bridge](#release-numbers-from-your-audio-conferencing-bridge)
- [Additional information on managing Microsoft Audio Conferencing](#additional-information-on-managing-microsoft-audio-conferencing)

## Set up an operator

You can set up, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

To set up an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then, select the operator you want to use. For Operator Connect Conferencing, verify that your operator has **Conferencing** listed as an available product.

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information** Your contact information, including your full name and email address, will be shared with your operator. You can change this information later. Additionally, you'll need to provide company size, with the option to provide your phone number. Operators use this information to contact you with more details about Operator Connect Conferencing.

4. Accept the data transfer notice.

5. **Add your operator.** Select **Add as my operator** to save.

## Acquire numbers for your Audio Conferencing bridge

Your organization's Audio Conferencing bridge includes phone numbers available to all users in your organization to join Microsoft Teams meetings with PSTN phone numbers. You can see the phone numbers associated with your organization's Audio Conferencing bridge in the Teams Admin Center under **Meetings > Conference Bridges**.

To acquire phone numbers for your Audio Conferencing bridge, follow these steps:

1. **Audio Conferencing Standard subscription or Operator Connect Conferencing license.** Users that need Operator Connect Conferencing numbers to join the meetings that they organize need to have an Audio Conferencing Standard subscription license or an Operator Connect Conferencing license assigned to them. For more information, see [Plan for Operator Connect Conferencing](operator-connect-conferencing-plan.md).

2. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, go to the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id). Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**.

3. **Assign numbers to your Audio Conferencing bridge.** You can assign numbers to your Audio Conferencing bridge from the Teams admin center under **Meetings > Conference Bridges > Add**. For more information, see [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

>[!NOTE]
>You can't assign Operator Connect Conferencing numbers as default numbers of a bridge. Once a phone number is assigned to your Audio Conferencing bridge, the number will be listed in the **Find a local number page** included in meeting invites of users in your organization with an Audio Conferencing license or an Operator Connect Conferencing license.
>
>To route outbound calls through an operator, see the [**Sending outbound calls from Teams meetings through an operator**](#sending-outbound-calls-from-microsoft-teams-meetings-through-an-operator) section further down in this article.

## Change the default phone numbers that are included in the meeting invites of users

 This step is optional.

The default phone numbers of a user are the ones included in their meeting invites when they schedule a meeting. You can update the phone numbers included in the meeting invites of users in the Teams Admin Center under **Users > Manage users**. To update the phone numbers included in the meeting invites of users, select the user, and select **Edit** in the **Audio Conferencing** section.

After the changes have been applied, new meeting invites of organizers will include the new default phone numbers. However, existing meeting invites that were scheduled before the change will keep the original default numbers.

## Sending outbound calls from Microsoft Teams meetings through an operator

If you have a Microsoft Audio Conferencing Standard subscription or an Operator Connect Conferencing license, you can configure the Audio Conferencing service to route all or a set of outbound calls from Teams meetings through your operator by setting up an Audio Conferencing Routing policy.

>[!NOTE]
>With an Operator Connect Conferencing license, outbound calls can only go through your operator. If you have Operator Connect Conferencing licenses, you need to configure the service as described below to enable outbound calls from Teams meetings to telephone numbers.

You can apply Audio Conferencing Routing policies at the user level, meaning that your operator routes only the outbound calls from Teams meetings organized by users with the associated policy. You can also apply these policies at the global level, meaning that your operator routes outbound calls from Teams meetings organized by all users in your organization.

Using PowerShell, create your organization's new Audio Conferencing Routing policy. To specify an operator as the primary route for outbound calls from Teams meetings, follow the steps below using the PowerShell commands indicated:

1. [Step 1: Add a new string to the Online PSTN Usage policy](#step-1-add-a-new-string-to-the-online-pstn-usage-policy)
2. [Step 2: Create a new Online Voice Route policy](#step-2-create-a-new-online-voice-route-policy)
3. [Step 3: Create a new Online Audio Conferencing Routing policy](#step-3-create-a-new-online-audio-conferencing-routing-policy)
4. [Step 4: Assign the new policy to users](#step-4-assign-the-new-policy-to-users)

### Step 1: Add a new string to the Online PSTN Usage policy

Read [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage) for more information on using this cmdlet.

```powershell
Set-CsOnlinePstnUsage -Identity Global -Usage @{Add="International"}
```

### Step 2: Create a new Online Voice Route policy

Read [Set-CsOnlineVoiceRoute](/powershell/module/skype/set-csonlinevoiceroute) for more information on using this cmdlet.

```powershell
New-CsOnlineVoiceRoute -Identity "International" -NumberPattern "\d+" -OnlinePstnUsages "International" -BridgeSourcePhoneNumber <an Operator Connect Conferencing number assigned to your Audio Conferencing bridge>
```

### Step 3: Create a new Online Audio Conferencing Routing policy

```powershell
New-CsOnlineAudioConferencingRoutingPolicy "International Policy" -OnlinePstnUsages "International"
```

### Step 4: Assign the new policy to users

```powershell
Grant-CsOnlineAudioConferencingRoutingPolicy -Identity <identity of the organizer of the meeting> -PolicyName "International Policy"
```

>[!NOTE]
>To set an Audio Conferencing Routing policy as global and apply it to all users in your organization, you can use the ``-Global`` parameter instead of the ``-Identity`` parameter. For example, ``Grant-CsOnlineAudioConferencingRoutingPolicy -Global -PolicyName "International Policy"``.

When you create an Audio Conferencing Routing policy and apply it to a user, the operator that provides the phone number specified in the ``BridgeSourcePhoneNumber`` parameter routes Teams outbound calls to PSTN phone numbers. Additionally, the ``BridgeSourcePhoneNumber`` parameter specifies the phone number to use as the calling line identification phone number of outbound calls to PSTN phone numbers.

The pattern specified in the ``NumberPattern`` is of regex form, and it specifies which calls to route through your operator. The ``"\d+"`` pattern in the example above matches all outbound calls from Teams meetings. You can also set the NumberPattern parameter as  ``"^\+1(425|206)(\d{7})$"``, which matches dialed numbers with the following formats: +1 425 XXX XX XX or +1 206 XXX XX XX, or ``"^\+1(\d{10})$"``, which matches dialed numbers with the following format: +1 425 XXX XX XX.

Once you assign an Audio Conferencing Routing policy to a user, all calls from their meetings to a phone number that matches the regex specified in their Audio Conferencing Routing policy routes through your operator, including **Call me at** calls and calls initiated through the **Invite someone or dial a number** meeting option.

## Manage your operators

From the **My operators** tab, you can view your operators, their status, and make the following changes to your selections:

- Manage operator services by country
- Suspend an operator
- Remove an operator

>[!NOTE]
>Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to the users and your Audio Conferencing bridge, then contact the operator to release the numbers.

## Release numbers from your Audio Conferencing bridge

To release phone numbers from your Audio Conferencing bridge from the Teams admin center, see **Steps when you are unassigning a service phone number for a conferencing bridge** in [Change the phone numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#steps-when-you-are-unassigning-a-service-phone-number-for-a-conferencing-bridge).

## Additional information on managing Microsoft Audio Conferencing

For additional information on how to manage Microsoft Audio Conferencing for your organization, see the following articles:

- Managing the Microsoft Audio Conferencing service settings for your organization: [Manage the Audio Conferencing settings for your organization in Microsoft Teams](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md)

- Managing the Microsoft Audio Conferencing service setting of the users in your organization: [Manage the Audio Conferencing settings for a user in Microsoft Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md)

- Changing the auto attendant languages of your Audio Conferencing phone numbers: [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md)
