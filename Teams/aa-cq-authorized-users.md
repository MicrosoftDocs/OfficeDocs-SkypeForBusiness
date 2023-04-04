---
title: Auto attendant and call queue authorized users
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: admin
ms.date: 03/15/2023
ms.collection: 
- M365-voice
- tier1
f1.keywords:
  - CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about setting up authorized users and what they can manage for auto attendants and call queues.
---

> [!IMPORTANT]
> The Voice applications policy and Authorized user configuaration options are available to all customers however the end user features in Teams clint are currently only available as part of a Public Preview.
> 
> General availability for all customers is scheduled for the end of April, 2023.


# Auto attendant and call queue authorized users

An authorized user is a Teams user who has been authorized by a Teams admin center administrator to make configuration changes to auto attendants and call queues. The user doesn't need to have access to the Teams admin center portal nor be assigned any administrative roles.

The Teams user accesses these configuration items through their Teams desktop client.

## Requirements

There are two required configuration steps to configure an authorized user:

1. The first step is to create a [Teams Voice Applications Policy](manage-voice-applications-policies.md) that turns on the change functionality that the user needs and to assign that policy to the user.
1. The second step is to assign the user as an *Authorized user* to at least one auto attendant or call queue.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one auto attendant or call queue.
>
> A user won't be able to make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one auto attendant or call queue.
> - The user is assigned as an authorized user to at least one auto attendant or call queue but doesn't have a policy assigned.

## Examples

User 1 needs to be able to change auto attendant business hours greetings and call queue timeout shared voicemail greetings for *Auto attendant 1* and *Call queue 1*.

User 2 needs to be able to change auto attendant after hours greetings for *Auto attendant 1*.

1. Create a *Teams Voice Applications Policy* that enables the auto attendant **Business Hours Greeting** and the call queue **Timeout shared voicemail greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-01.png" alt-text="Screenshot of voice applications policy that enables auto attendant business hours greeting changes and call queue timeout shared voicemail greeting changes.":::

1. Assign this policy to User 1.
1. Create another *Teams Voice Applications Policy* that enables the Auto Attendant **After Hours Greeting**.

    :::image type="content" source="media/voiceapplications-policies-example-02.png" alt-text="Screenshot of voice applications policy that enables auto attendant after hours greeting changes.":::

1. Assign this policy to User 2.
1. Assign both User 1 and User 2 as *Authorized users* for *Auto attendant 1*.
1. Assign User 1 as an *Authorized User* for *Call queue 1*.

Both User 1 and User 2 are now fully authorized users and will have new configuration options available to them in their Teams desktop client once they logout and log back in.

## Related articles

- [Manage Teams Voice Applications Policies](manage-voice-applications-policies.md).
- [Set up a Microsoft Teams auto attendant](create-a-phone-system-auto-attendant.md).
- [Create a call queue in Microsoft Teams](create-a-phone-system-call-queue.md).
