---
title: Auto attendant and call queue authorized users
ms.author: colongma
author: CLYVR
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.voiceapplications.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about authorized users and what they can do
---

# Authorized Users
An authorized user is a Teams user who has been authorized by an Teamd Admin Center administrator to make configuration changes to auto attendants and call queues.  The user does not need to have access to the Teams Admin Center portal nor do they need to be assigned any administrative roles.

## General Overview


## Requirements
There are two configuration steps required in order to configure an authorized user:

1. The first step is to create a [Teams Voice Applications Policy](./manage-voice-applications-policies.md) that enables the change functionality that the user will need and to assign that policy to the user.
1. The second step is to assign the user as an Authorized user to at least one auto attendant or call queue.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one auto attendant or call queue.
> A user will not be able to make any configuration changes if:
> - The user has a policy assigned but is not assigned as an authorized user to at least one auto attendant or call queue
> - The user is assigned as an authorized user to at least one auto attendant or call queue but does not have a policy assigned

## Examples


## Related articles

[Manage Teams Voice Applications Policies](./manage-voice-applications-policies.md)

[Set up a Microsoft Teams auto attendant](./create-a-phone-system-auto-attendant.md)

[Create a call queue in Microsoft Teams](./create-a-phone-system-call-queue.md)
