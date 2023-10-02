---
title: Audio Conferencing in Microsoft Teams
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.date: 09/07/2022
ms.topic: conceptual
ms.assetid: a5a696c3-d321-4e61-9aad-e3a87041196e
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - m365initiative-meetings
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
search.appverid: MET150
audience: admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Audio Conferencing
  - ms.teamsadmincenter.audioconferencing.overview
  - seo-marvel-apr2020
description: Learn about how Audio Conferencing in Microsoft 365 allows users to call in to meetings from their phones.
---

# Audio Conferencing in Microsoft Teams

Audio Conferencing in Microsoft Teams enables users to call in to Teams meetings from their phones. Audio Conferencing allows up to 1000 phone attendees.

## What is Audio Conferencing?

Calling in (dialing in) to meetings is very useful for users who are on the road and can't attend a meeting using the Microsoft Teams app on their laptops or mobile devices. But there are other scenarios in which using a phone to attend a Teams meeting can be a better option than using an app on a computer:
  
- Internet connectivity is limited.
- A meeting is audio only.
- The person tried to join a Teams meeting and it failed.
- The call quality is better when dialing in.
- People can join a meeting "hands free" using Bluetooth devices.
- People find it's easier and more convenient for their situation.

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. Meeting attendees who dial in don't need any licenses assigned to them or other setup.

After attendees have joined meeting, they can also dial out and invite other callers into a Teams meeting.
See [Dialing out from a Teams meeting so other people can join it](dialing-out-from-a-teams-meeting-so-other-people-can-join-it.md) for more information.

## What does it cost?

For pricing info, see [Pricing for Audio Conferencing](https://go.microsoft.com/fwlink/?linkid=799762&clcid=0x409).

## Where is it available?

With Audio Conferencing, your users can use toll and toll-free phone numbers to dial in to meetings. Toll (service) numbers are automatically assigned as shared audio conferencing numbers to organizations when they're enabled for Audio Conferencing. Dedicated toll and toll-free numbers can be assigned to your organization from additional cities.

Toll-free phone numbers (service numbers) are available, but only in some countries/regions. To see what is available in your country or region, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

After you have decided you want Audio Conferencing for your organization, you need to buy one **Audio Conferencing** license for each person in your organization who is going to schedule/host an audio meeting.

## How do conferencing bridges work?

When you are setting up Audio Conferencing for Teams, you will get an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. The phone number you set will be included on the meeting invites for Teams apps. You can [change the phone numbers on your conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md), and you can also [change other audio conferencing bridge settings](change-the-settings-for-an-audio-conferencing-bridge.md).

The audio conferencing bridge answers a call for people who are dialing in to a meeting using a phone. It answers the caller with voice prompts from an auto attendant, and then, depending on your settings, can play notifications and ask callers to record their name. **Microsoft bridge settings** allow you to change the settings for meeting notifications and the meeting join experience, and set the length of the PINs that are used by meeting organizers [in Microsoft Teams](set-the-pin-length-for-audio-conferencing-meetings-in-teams.md). Meeting organizers use PINs to start meetings if they can't join the meeting using the Teams app.

## Dial-in phone numbers set on an audio conferencing bridge

There are two types of audio conferencing phone numbers that can be assigned to your conferencing bridge: **Shared** and **Dedicated**. Both types of numbers can be used by any caller to join audio meetings that are being held in your organization.
  
 **Dedicated phone numbers** are those phone numbers that are only available to users within your organization. You can change the languages that are used when someone calls in to one of these numbers. You will need to get a service phone number for these.
  
 **Shared phone numbers** are those phone numbers that can be shared with other Microsoft 365. You can't change the languages that are used when someone calls in to one of these numbers.
  
While the default audio conferencing number that is assigned to an organizer is only included in the meeting invite, a caller can use any of the phone numbers that are assigned to your conferencing bridge to join a meeting. The list of phone numbers that can be used to join a meeting is available using the **Find a local number** link that is included on every meeting invite.

For more information, see [Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md) .

## Automatically assigned audio conferencing phone numbers

Shared audio conferencing phone numbers are automatically assigned to organizations when they're enabled for audio conferencing. When the phone numbers are assigned, a phone number is assigned as the default phone number of the conferencing bridge. The phone number assigned as the default number of the bridge will be one from the country/region of the organization.

> [!NOTE]
> The country or region location of your organization can be found by signing in to the **Microsoft 365 admin center** and looking under **Organization Profile**.

> [!CAUTION]
> Due to limited availability of toll phone numbers in Venezuela, Indonesia, and United Arab Emirates (UAE), organizations from these countries/regions won't have an Audio Conferencing toll number automatically assigned to them. Toll-free numbers from these locations are available depending on available inventory.

To see a list of those countries/regions that have phone numbers automatically assigned to organizations, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

## How do you get dedicated phone numbers?

Dedicated audio conferencing phone numbers are service numbers that you can get and then assign to your organization. You can get dedicated toll and toll-free phone numbers for your conferencing bridges in one of three ways:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your conference bridges using the Teams admin center. See [Getting service phone numbers](./getting-service-phone-numbers.md).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365. See [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information to help you do this.  
  
- **Use a request form for new numbers.** Sometimes (depending on your country/region) you won't be able to get your new phone numbers using the Teams admin center, or you will need specific phone numbers or area codes. If so, you'll need to download a form and send it back to us. See [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) for more information.

## How do you set it up?

After you've decided to set up Audio Conferencing for your users, see [Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md) for the steps you need to follow.

## Related topics

[Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md)
