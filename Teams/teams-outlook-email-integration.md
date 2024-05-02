---
title: Manage actionable activity emails
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 12/13/2019
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about enabling and disabling actionable activity emails of Microsoft Teams conversations  
ms.collection: 
  - M365-collaboration
ms.custom: chat-teams-channels-revamp
appliesto:
  - Microsoft Teams
---

# Manage actionable activity emails

Actionable activity emails are enabled by default and notify users in your organization of missed conversations on Microsoft Teams.

A missed activity email shows the latest replies to a conversation, including messages sent after the missed message. This feature lets users reply directly from Outlook by selecting **Reply**.

## Disable actionability in missed activity emails

While this feature is set to enable by default, you can turn off actionability in activity emails across your organization by running the following command:

```Powershell
Set-OrganizationConfig -SmtpActionableMessagesEnabled $false
```

Once the feature is disabled, the **Reply** option is replaced by **Reply in Teams** making the missed activity emails no longer considered actionable. Users will no longer be able to respond directly from Outlook and are directed to continue the conversation on Teams.

> [!NOTE]
> This feature isn't supported in Outlook for Mac or some older versions of Outlook for Windows. For more information, see [Actionable messages in Outlook and Office 365 Groups](/outlook/actionable-messages/).

## Related topics

[Reply to missed activity emails from Outlook](https://support.office.com/article/reply-to-missed-activity-emails-from-outlook-bc0cf587-db26-4946-aac7-8eebd84f1381).

[Actionable messages in Outlook and Office 365 Groups](/outlook/actionable-messages/).
