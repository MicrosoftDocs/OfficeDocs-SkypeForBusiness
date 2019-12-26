---
title: Teams and Outlook email integration
author: LanaChin
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: kblevens
localization_priority: Normal
search.appverid: MET150
description: Learn how users can share information between email in Outlook and chat in Teams.  
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Teams and Outlook email integration

These features make it easier to share information between email and chat.

## Share to Teams

Share to Teams is an Outlook add-in that lets users share an email from Outlook, including attachments, along with a message to a chat or channel in Teams. A preview of the email is displayed in Teams and people in the chat or channel can open any attachments.

To enable and disable this feature, you can use the [Disable-App](https://docs.microsoft.com/powershell/module/exchange/mailboxes/disable-app?view=exchange-ps) PowerShell cmdlet. Note that the Share to Teams add-in must be installed before you can use the Disable-App cmdlet to enable or disable it. 

## Share to Outlook

Share to Outlook lets users share a copy of a Teams conversation to an email in Outlook, without having to leave Teams.

To use this feature, Outlook on the web must be enabled for the user. If Outlook on the web isn't enabled for a user mailbox, the **Share to Outlook** option isn't displayed in Teams for the user.  To learn more about how to enable or disable Outlook on the web, see [Enable or disable Outlook on the web for a mailbox](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app).

## Actionable activity emails

Users get actionable missed activity emails which make it easy to stay on top of a missed conversation in Teams. The missed activity emails show the latest replies from a conversation including messages sent after the missed message and lets users respond directly from within Outlook.

## Related topics

- [Teams Meeting add-in in Outlook for Windows](Teams-add-in-for-Outlook.md)