---
title: Set up Auto attendant and Call queue authorized users
ms.author: danismith
author: DaniEASmith
manager: pamgreen
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 04/05/2023
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up authorized users and what they can manage for Auto attendants and Call queues.
---

# Set up Auto attendant and Call queue authorized users

An authorized user is a Teams user who has been authorized by a Teams admin center administrator to make configuration changes to Auto attendants and Call queues. The user doesn't need to have access to the Teams admin center portal nor be assigned any administrative roles.

The Teams user accesses these configuration items through their Teams desktop client.

## Requirements for setting up authorized users

There are two required configuration steps to set up an authorized user:

1. The first step is to create a [Teams voice applications policy](manage-voice-applications-policies.md) that turns on the change functionality that the user needs and to assign that policy to the user.
1. The second step is to assign the user as an *Authorized user* to at least one Auto attendant or Call queue. There is a maximum of 15 authorized users per each Auto attendant or Call queue.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one Auto attendant or Call queue.
>
> A user won't be able to make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one Auto attendant or Call queue.
> - The user is assigned as an authorized user to at least one Auto attendant or Call queue but doesn't have a policy assigned.

## Examples

User 1 needs to be able to change Auto attendant business hours greetings and Call queue timeout shared voicemail greetings for *Auto attendant 1* and *Call queue 1*.

User 2 needs to be able to change Auto attendant after hours greetings for *Auto attendant 1*.

1. Create a *Teams voice applications policy* that enables the Auto attendant **Business Hours Greeting** and the Call queue **Timeout shared voicemail greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-01.png" alt-text="Screenshot of voice applications policy that enables Auto attendant business hours greeting changes and Call queue timeout shared voicemail greeting changes.":::

1. Assign this policy to User 1.
1. Create another *Teams voice applications policy* that enables the Auto attendant **After Hours Greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-02.png" alt-text="Screenshot of voice applications policy that enables Auto attendant after hours greeting changes.":::

1. Assign this policy to User 2.
1. Assign both User 1 and User 2 as *Authorized users* for *Auto attendant 1*.
1. Assign User 1 as an *Authorized User* for *Call queue 1*.

Both User 1 and User 2 are now fully authorized users and will have new configuration options available to them in their Teams desktop client once they sign out and sign back in.

## Related articles

- [Manage Teams voice applications policies](manage-voice-applications-policies.md).
- [Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md).
- [Manage your Call queue and Auto attendant greetings in Microsoft Teams](https://support.microsoft.com/office/manage-your-call-queue-and-auto-attendant-greetings-in-microsoft-teams-52c741c6-8577-4faf-aa5a-c7853e0ab8f8)
