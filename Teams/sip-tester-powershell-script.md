---
title: PowerShell script to test Direct Routing Session Border Controller connections
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.topic: article
ms.reviewer: filippse
ms.date: 10/03/2019
ms.service: msteams
audience: admin
description: Use this PowerShell script sample to test Direct Routing Session Border Controller connections in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
---

# PowerShell script to test Direct Routing Session Border Controller connections

 > [!NOTE]
  > The SIP Tester client script will be deprecated on November 30, 2024

SIP Tester client is a sample PowerShell script that you can use to test Direct Routing Session Border Controller (SBC) connections in Microsoft Teams. This script tests basic functionality of a customer-paired Session Initiation Protocol (SIP) trunk with Direct Routing.

The script submits an SIP test to the test runner, waits for the result, and then presents it in a human-readable format. You can use this script to test the following scenarios:

- Outbound and inbound calls
- Simultaneous ring
- Media escalation
- Consultative transfer

## Download the script and documentation

Download the [SIP Tester client script and documentation](https://download.microsoft.com/download/7/5/b/75b7202f-86f0-4e89-88d4-830c44503a4e/siptesterclient.zip).

  > [!NOTE]
  > SIP Tester client script only supports adal.ps version 3.19.8.1. An error will be returned if a later version of the adal.ps is used.
  
  
