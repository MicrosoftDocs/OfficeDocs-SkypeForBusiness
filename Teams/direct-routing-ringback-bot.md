---
title: Ringback bot for Direct Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Learn how to configure and use the Ringback bot for Direct Routing to prevent unexpected silences that may occur when a call is being established.
localization_priority: Normal
ms.collection: 
- M365-voice
appliesto: 
- Microsoft Teams
---

# Ringback bot for Direct Routing


- Direct Routing now supports a Ringback bot
- Administrators can configure this bot with a new parameter GenerateRingingWhileLocatingUser in the Set-CsOnlineGateway and New-CsOnlinePSTNGateway cmdlets

During inbound PSTN call (calls from PSTN to Teams client) call establishing might take long time due to various reasons. During this period caller might not hear anything, recipient device (Teams client) does not ring and some such calls might be even canceled by some telco providers. 

The Ringback Bot helps to avoid unexpected silence when call setup is delayed. In case of inbound PSTN call to Teams in Direct Routing non-bypass mode distinctive audio signal is played to the caller during prolonged call setup procedure. This signal indicates that Teams is in the process of establishing the call. 

The Ringback bot helps to avoid unexpected silences that may occur when a call is being established. For inbound calls from the PSTN to Teams in non-media bypass mode

## Configure the Ringback bot

You use the [Set-CsOnlineGateway](https://docs.microsoft.com/powershell/module/skype/set-csonlinepstngateway) and [New-CsOnlinePSTNGateway](https://docs.microsoft.com/powershell/module/skype/new-csonlinepstngateway) cmdlets together with the GenerateRingingWhileLocatingUser parameter to configure the Ringback bot. 

To learn more, see 


## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)