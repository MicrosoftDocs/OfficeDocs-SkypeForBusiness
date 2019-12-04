---
title: Ringback bot for Direct Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Learn how to configure the Ringback bot for Direct Routing to prevent prolonged silences that may occur when a call is being established.
localization_priority: Normal
ms.collection: 
- M365-voice
appliesto: 
- Microsoft Teams
---

# Ringback bot for Direct Routing


- Direct Routing now supports a Ringback bot
- Administrators can configure this bot with a new parameter GenerateRingingWhileLocatingUser in the Set-CsOnlineGateway and New-CsOnlinePSTNGateway cmdlets


SIP Tester client is a sample PowerShell script that you can use to test Direct Routing Session Border Controller (SBC) connections in Microsoft Teams. This script tests basic functionality of a customer-paired Session Initiation Protocol (SIP) trunk with Direct Routing.

The script submits an SIP test to the test runner, waits for the result, and then presents it in a human-readable format. You can use this script to test the following scenarios:

- Outbound and inbound calls
- Simultaneous ring
- Media escalation
- Consultative transfer

## Download the script and documentation

Download the [SIP Tester client script and documentation](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/sip-tester-client/siptesterclient.zip?raw=true).