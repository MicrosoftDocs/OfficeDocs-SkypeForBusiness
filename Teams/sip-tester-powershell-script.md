---
title: PowerShell script to test Direct Routing Session Border Controller connections
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Use this PowerShell script sample to test Direct Routing Session Border Controller connections in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
- M365-voice
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
---

# PowerShell script to test Direct Routing Session Border Controller connections

SIP Tester client is a sample PowerShell script that you can use to test Direct Routing Session Border Controller (SBC) connections in Microsoft Teams. This script tests basic functionality of a customer-paired Session Initiation Protocol (SIP) trunk with Direct Routing.

The script submits an SIP test to the test runner, waits for the result, and then presents it in a human-readable format. You can use this script to test the following scenarios:

- Outbound and inbound calls
- Simultaneous ring
- Media escalation
- Consultative transfer

## Download the script and documentation

Download the [SIP Tester client script and documentation](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/sip-tester-client/siptesterclient.zip?raw=true).

  > [!NOTE]
  > SIP Tester client script only supports adal.ps version 3.19.8.1. An error will be returned if a later version of the adal.ps is used.
  
  
