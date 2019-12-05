---
title: Set up the Ringback bot for Direct Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Learn how to use the Ringback bot for Direct Routing to prevent unexpected silences that can occur when a call is being established.
localization_priority: Normal
ms.collection: 
- M365-voice
appliesto: 
- Microsoft Teams
---

# Set up the Ringback bot for Direct Routing

This article describes the Ringback bot, which you can use to help avoid unexpected silences that can occur when it takes a longer time for calls to be established. The Ringback bot is available for Direct Routing in non-media bypass mode.

Sometimes inbound calls from the public switched telephone network (PSTN) to Teams clients can take longer than expected to be established. This can occur for various reasons. When this happens, the caller might not hear anything, the Teams client doesn't ring, and the call might be canceled by some telecommunications providers.

The Ringback bot helps to avoid unexpected silences that can occur in this scenario. For inbound calls from the PSTN to Teams clients, the Ringback bot plays a distinctive audio signal to the caller to indicate that Teams is in the process of establishing the call.

> [!NOTE]
> The Ringback bot generates early media from the Teams backend. In some countries and regions, you might be charged for the call when the media starts flowing.

## Configure the Ringback bot

Use the [Set-CsOnlineGateway](https://docs.microsoft.com/powershell/module/skype/set-csonlinepstngateway) and [New-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/new-csonlinepstngateway) cmdlets together with the **GenerateRingingWhileLocatingUser** parameter to configure the Ringback bot.

To turn on the Ringback bot, set the **GenerateRingingWhileLocatingUser** parameter to **$True**. This is the default value. 

To turn off the Ringback bot, set the **GenerateRingingWhileLocatingUser** parameter to **$False**. 

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)