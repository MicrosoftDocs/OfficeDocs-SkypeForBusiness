---
title: Use inline message translation in Microsoft Teams
author: ChuckEdmonson
ms.author: chucked
manager: serdars
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: salilda
localization_priority: Normal
search.appverid: MET150
description: Learn how to use inline translation in Microsoft Teams.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

Use inline message translation in Microsoft Teams 
=================================================

Inline message translation is a new Microsoft Teams feature that lets users automatically translate Teams messages into the [language](https://support.office.com/article/translate-a-message-in-teams-d8926ce9-d6a6-47df-a416-f1adb62d3194) specified by their personal language settings for Office 365.

Inline message translation is being rolled out by default for your organization. If you want to allow users to use this feature within the Teams client, you must turn this setting on.

> [!NOTE]
>This rollout is excluded from Office 365 subscriptions in our Office 365 Government Community Cloud and Office 365 Germany environments.

## Enable by using PowerShell

You can turn on the inline message translation feature by using the Messaging Policy.

1. Turn on the policy by using the [Set-CsTeamsMessagingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmessagingpolicy?view=skype-ps) cmdlet.
2. The policy takes a few minutes to apply. Users might need to sign out and sign back in to Teams.

## Enable by using the Microsoft Teams admin center

In the **Microsoft Teams admin center**, select **Messaging Policies** from the left-hand bar, then either create a new policy or edit an existing policy, and set the **Allow users to translate messages** option to **On**.

> [!NOTE]
>Translation is done by the service and delivered to the client with no effect on the content captured in the compliance records. To learn more about translation, see [What is Microsoft Translator?](https://docs.microsoft.com/azure/cognitive-services/translator/translator-info-overview).