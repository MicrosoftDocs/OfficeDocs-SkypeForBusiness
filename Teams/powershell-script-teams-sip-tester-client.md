---
title: PowerShell script to test Direct Routing SBC sessions in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Use this PowerShell script sample to test Direct Routing Session Border Controller sessions in Microsoft TEams
localization_priority: Normal
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# PowerShell script to test Direct Routing SBC sessions in Microsoft Teams

Use this PowerShell script to test Direct Routing Session Border Controller (SBC) connections in Microsoft Teams. This script tests basic functionality of a customer-paired Session Initiation Protocol (SIP) trunk.

The script submits an SIP test to the test runner, waits for the result, and then presents it in a human-readable format. You can use this script to test the following scenarios:

- Outbound and inbound calls
- Simultaneous ring
- Media escalation
- Consultative transfer

## Download the script and documentation

Download the [SIP tester client script and documentation](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/scripts/sip-tester-client/siptesterclient.zip?raw=true).