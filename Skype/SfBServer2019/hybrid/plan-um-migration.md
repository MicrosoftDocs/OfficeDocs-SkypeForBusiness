---   
title: Article title goes here       # Very important for SEO. See https://aka.ms/seo-for-writers-cheat-sheet
author: dstrome           # This is your GitHub alias, not your Microsoft alias
ms.author: dstrome        # Your Microsoft alias without @microsoft.com
manager: serdars                     # Delete for SharePoint
audience: ITPro                      # One of: Admin, ITPro, Developer
ms.topic: article                    # See metadata requirements link above for additional allowed values.
localization_priority: Normal        # See metadata requirements link above for allowed values.
ms.prod: skypeforbusiness-server-itpro     # See metadata requirements link above for allowed values.
description:                         # Treat this like a summary tag in DxStudio. It helps with SEO.
---

# Plan for Skype for Business Server and Exchange Server migration

[!INCLUDE [disclaimer](../disclaimer.md)]

This topic talks about what you need to consider when you decide to migrate your existing Skype for Business Server or Exchange Server deployments to the latest version or to Skype for Business Online or Exchange Online. What you can migrate, and when, heavily depends on what you've already got set up in your organization.

## Deprecated features

Unified Messaging (UM) has been deprecated in Exchange 2019. This means that Exchange 2019 no longer offers voice mail, call handling, auto attendant, and other features provided by UM. If you've deployed the UM role in Exchange 2013, or the UM service in Exchange 2016, you'll need to either migrate your voicemail to the Microsoft Cloud Voicemail service in Office 365 or to an on-premises 3rd-party voicemail solution. If you want to migrate your voicemail to Microsoft Cloud Voicemail, take a look at the [foo] section below.



## Features or deployments not supported at Preview
