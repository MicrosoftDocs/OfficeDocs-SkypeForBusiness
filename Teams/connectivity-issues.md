---
title: Troubleshoot connectivity issues with Teams client
ms.reviewer: 
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: troubleshooting
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
search.appverid: MET150
f1.keywords:
- NOCSH
description: Troubleshoot connectivity issues with the Microsoft Teams client, primarily caused by the firewall or proxy connection, and learn how to fix it.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Troubleshoot connectivity issues with the Microsoft Teams client

Most issues discovered with the Microsoft Teams client can be traced back to firewall or proxy connectivity. Verifying that the necessary URLs, IP addresses and ports are opened in your firewall or proxy will minimize unnecessary troubleshooting. For specific information on URLs and IPs required for Microsoft Teams, please see the [Microsoft 365 and Office 365 URLs and IP Address](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) support article. The following scenarios require specific URLs and ports to be opened in the firewall.

- Authentication

- Microsoft Teams Client Connectivity

- Collaboration

- Media

- Shared Services

- Third Party Integration

- Skype for Business Interoperability

- Skype for Business Client Interoperability

## When Teams is offline or in low bandwidth conditions

The good news is that Teams keeps running even when you're offline or running in low bandwidth conditions. Teams saves all your unsent messages for existing chats (for up to 24 hours) and sends them as soon as you're back online. If you're offline for longer than 24 hours, Teams lets you choose to resend or delete unsent messages. We're working on adding this functionality to new chats and will update this documentation when that's available.

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)