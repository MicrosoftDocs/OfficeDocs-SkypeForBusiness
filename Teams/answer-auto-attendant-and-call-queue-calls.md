---
title: Answer Auto attendant and Call queue calls
ms.reviewer: colongma
author: mkbond007
ms.author: mabond
manager: pamgreen
audience: ITPro
ms.date: 08/01/2023
ms.topic: conceptual
ms.service: msteams
description: Describes Cloud Auto attendants and Call queues, and explains how you can answer these calls in Teams.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Answer Auto attendant and Call queue calls directly from Teams

Teams users can receive and answer calls from Cloud Auto attendants and Call queues directly from their Teams client.

## What are Auto attendants and Call queues?

Cloud Auto attendants provide a series of voice prompts or an audio file that callers hear instead of a human operator when they call in to an organization. An Auto attendant lets callers move through the menu system, place calls, or locate users by using a phone keypad (DTMF) or voice inputs using speech recognition.

Cloud Call queues include greetings that are used when someone calls in to a phone number for your organization, the ability to automatically put the calls on hold, and the ability to search for the next available call agent to handle the call while the people who call are listening to music on hold. You can create single or multiple Call queues for your organization.

## Handling an Auto attendant or Call queue call

Users will be able to differentiate incoming calls from an Auto attendant or Call queue before they answer the call. Along with the name and/or number of the caller, each call will include the display name of the resource account assigned to the Auto attendant or the Call queue that the caller was trying to reach, giving users a better context for addressing the caller.

The following illustration shows how an incoming call from an Auto attendant or Call queue will appear to a user.

![Screenshot of an incoming call notification.](media/answer-auto-attendant-and-call-queue-calls-image1.png)

Once an Auto attendant or Call queue call is answered, the user can process the call like any other call &#x2014; they can add or conference in another user or transfer the call to another party. Also, Auto attendant calls will be forwarded based on the user's configuration.

> [!NOTE] 
> Call queue calls are not forwarded based on the user's call answering rules configuration. This is to ensure callers remain in the queue until an agent can answer the call and the caller isn't forwarded unexpectedly.
>
> Users receiving calls from Call queues will only be presented with the name of the caller if it's provided from the PSTN or if the caller's number matches the target user's local Team's client contacts.
>
> Agents are not notified of any missed calls or voicemails for Call queue calls.

## Supported clients

Support for Auto attendant and Call queue calls is available in the following clients:

- Microsoft Teams Windows client (32 and 64-bit versions)
- Microsoft Teams Mac client
- Microsoft Teams iPhone app
- Microsoft Teams Android app

The Teams client is only supported with a [co-existence mode of Teams Only](/microsoftteams/setting-your-coexistence-and-upgrade-settings).

## Configure Auto attendant and Call queue support for Microsoft Teams

To receive Auto attendant and Call queue calls on Microsoft Teams, you need to configure your interoperability policy and upgrade policy. Please review [Migration and interoperability for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md). If you do not have Auto attendant and/or Call queue configured and would like to do so, see [Set up a Cloud Auto attendant](create-a-phone-system-auto-attendant.md) and [Create a Cloud Call queue](create-a-phone-system-call-queue.md).

## Known Issues

When a Call queue agent receives a call on their mobile device, the call may go on hold if the device is locked. Users must unlock the device first and then answer the call.

## Related topics

[Create a Cloud Call queue](create-a-phone-system-call-queue.md)

[What are Cloud Auto attendants?](what-are-phone-system-auto-attendants.md)

[Set up a Cloud Auto attendant](create-a-phone-system-auto-attendant.md)
