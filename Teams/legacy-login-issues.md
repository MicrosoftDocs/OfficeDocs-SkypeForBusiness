---
title: Issues receiving messages and calls on legacy systems in Teams
ms.reviewer: 
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 05/29/2020
ms.topic: troubleshooting
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
search.appverid: MET150
f1.keywords:
- NOCSH
description: Troubleshoot issues related to receiving messages and calls on legacy systems
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Issues receiving messages and calls on legacy systems

Users might have issues receiving messages or calls if they are using older versions of Teams or have logged in with other applications.

## Legacy ADU setups

 If users are signed in to a domain-joined computer and you **don't want their user name pre-populated on the Teams sign-in screen**, admins can set the following Windows registry to turn off pre-population of the user name (UPN):

  Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams<br/>
  SkipUpnPrefill(REG_DWORD)<br/>
  0x00000001 (1)

> [!NOTE]
> Skipping or ignoring user name pre-fill for user names that end in ".local" or ".corp" is on by default, so you don't need to set a registry key to turn these off.

See [Sign in to Microsoft Teams using modern authentication](sign-in-teams.md) for more information.

## Skype token revocation

When changing/resetting a password, older clients will not receive messages and calls for up to an hour. To resolve this issue, either restart the app or move to newer clients.


## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)