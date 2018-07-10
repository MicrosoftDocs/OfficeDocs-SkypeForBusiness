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

## Deprecated features in Exchange 2019

Unified Messaging (UM) has been deprecated in Exchange 2019. This means that Exchange 2019 no longer offers the following features:
- Voice mail
- Call handling
- Auto attendant
- Subscriber access
- Message waiting indicator for some IP Phone models

If you've deployed the UM role in Exchange 2013, or the UM service in Exchange 2016, and want to upgrade to Exchange 2019, you'll need to either migrate your voicemail to the Microsoft Cloud Voicemail service in Office 365 or to an on-premises 3rd-party voicemail solution. If you want to migrate your voicemail to Microsoft Cloud Voicemail, take a look at the [foo] section below.
> [!IMPORTANT]
> If users on your Exchange 2013 or Exchange 2016 servers have UM-enabled mailboxes, don't move them to Exchange 2019 before you upgrade your Skype for Business servers to Skype for Business 2019. Doing so will prevent them from receiving voicemail messages.

Private Branch Exchanges (PBX) and Session Border Controllers (SBC) aren't supported with Skype for Business Online or with Microsoft Cloud Voicemail. If you use PBXs or SBCs in your on-premises organization, you'll need to adopt one of the three options listed in the blog post [New date for discontinuation of support for Session Border Controllers in Exchange Online Unified Messaging](https://blogs.technet.microsoft.com/exchange/2018/04/24/new-date-for-discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/) on the [Exchange Team Blog](https://blogs.technet.microsoft.com/exchange/) before you migrate to Exchange 2019 or Skype For Business Server 2019.

## Cloud Voicemail feature parity with UM

