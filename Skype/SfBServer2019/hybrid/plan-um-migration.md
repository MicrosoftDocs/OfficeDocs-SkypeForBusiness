---
title: Plan for Skype for Business Server and Exchange Server migration       # Very important for SEO. See https://aka.ms/seo-for-writers-cheat-sheet
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

This topic talks about what you need to consider when you decide to migrate your existing Skype for Business Server or Exchange Server deployments to the latest version or to Skype for Business Online or Exchange Online. What you can migrate, and when, heavily depends on what you've already got set up in your organization. At Preview, we're focusing on supporting a few specific scenarios with additional scenarios becoming available at General Availability (GA).

## Feature changes in Exchange 2019 and Skype for Business 2019

With Exchange 2019 and Skype for Business 2019, we're making some changes to the features we support.

### Unified Messaging support in Exchange 2019

Unified Messaging (UM) has been deprecated in Exchange 2019. This means that Exchange 2019 no longer offers the following features:

- Voice mail
- Auto attendant

If you've deployed the UM role in Exchange 2013 or the UM service in Exchange 2016, and want to upgrade to Exchange 2019, you'll need to migrate your voicemail to the Microsoft Cloud Voicemail service in Office 365. If you want to migrate your voicemail to Cloud Voicemail, take a look at the [foo] section below.
> [!IMPORTANT]
> If users on your Exchange 2013 or Exchange 2016 servers have UM-enabled mailboxes, don't move them to Exchange 2019 before you upgrade your Skype for Business servers to Skype for Business 2019 to avoid a voice messaging outage.

### PBX support in Exchange 2019 and Skype for Business 2019

Microsoft Cloud Voice Mail does not provide voice messaging functionality to Private Branch Exchange's (PBX's). If you are utilizing Exchange Server Unified Messaging for PBXs and want to upgrade to Exchange Server 2019, you'll need to adopt one of the three options listed in the blog post [New date for discontinuation of support for Session Border Controllers in Exchange Online Unified Messaging](https://blogs.technet.microsoft.com/exchange/2018/04/24/new-date-for-discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/) on the [Exchange Team Blog](https://blogs.technet.microsoft.com/exchange/).

### Exchange Online UM support in Skype for Business 2019

With Skype for Business 2019, we're moving from Exchange Online UM to Cloud Voicemail. When a user is moved to a Skype for Business 2019 server, they'll automatically start using Cloud Voicemail when configured for hosted voicemail. If you are currently using Exchange Online UM, you don't need to do anything other than move a user to Skype for Business 2019 to start using Cloud Voicemail, there are some changes to functionality you need to be aware of:

- For Preview, Organizational Auto Attendant (the replacement for auto attendant in Exchange Online UM) isn't available. Organizational Auto Attendant will be available at GA.
- User voicemail settings in Outlook on the Web don't apply to Cloud Voicemail.

## On-premises UM migration scenarios

At Preview, we're supporting the following scenarios with additional scenarios coming at GA. (we need to give more context here that these are migration scenarios...probably more descriptive of the list...it took me way to long to figure out what this meant!)

- Exchange 2013/Exchange 2016 and Skype for Business 2015 to Exchange 2019 and Skype for Business 2019
- Exchange 2013/Exchange 2016 to Exchange 2019 with Skype for Business 2015
- Skype for Business 2015 to Skype for Business 2019 with Exchange 2013/Exchange/2016

The following scenarios require that no PBX or SBC configurations exist as part of your current deployment and assume that you have UM configured on your on-premises Exchange servers. Each of these solutions also assumes that you've decided to configure a hybrid deployment between your on-premises Skype for Business servers and Office 365. For more information about Skype for Business hybrid deployments, see [Skype for Business hybrid solutions](hybrid-solutions.md).

### Exchange 2013/Exchange 2016 and Skype for Business 2015 to Exchange 2019 and Skype for Business 2019

In this scenario, you want to migrate your existing Exchange 2013, Exchange 2016, and Skype for Business 2015 servers to Exchange 2019 and Skype for Business 2019.

As mentioned earlier in this topic, Exchange 2019 no longer includes the UM service. This means that, for any mailboxes that you want to move to Exchange 2019, you need to use Cloud Voice Mail. When you set up Skype for Business 2019 and a hybrid deployment between it and Office 365, you can use Cloud Voicemail to replace these Exchange UM voicemail services.

Keep the following things in mind before starting your migration:

- Cloud voicemail doesn't support Organizational Auto Attendant at Preview. If you want mailboxes moved to Cloud Voicemail to continue to be available via auto attendant, you'll need to keep at least one Exchange 2013 or Exchange 2016 server running the UM role or service available.
- You need to set up at least one Skype for Business 2019 server **and** move users to that server before you move their mailboxes to Exchange 2019. Failing to do so will result in those mailboxes being unable to receive voicemail messages.
- Calls sent to voicemail will be transferred to Cloud Voicemail where they will be recorded. After the call has ended, the voicemail message will be sent to the recipient's mailbox on the on-premises Exchange 2019 server. You need to take this voice traffic into account when determining whether your Internet connectivity is sufficient to support Cloud Voicemail.

Here are the high-level steps to complete this migration. For more information, read each topic:

1. Install and configure Skype for Business Server 2019 on a new server.
2. Update your hybrid deployment configuration to include the new Skype for Business 2019 server.
3. Install and configure Exchange Server 2019 on a new server.
4. Move users from your Skype for Business 2015 server to your Skype for Business 2019 server.
5. Move mailboxes from your Exchange 2013 or Exchange 2016 server to your Exchange 2019 server.
6. Decommission your Skype for Business 2015 server after the last user has been moved off of it.
7. Decommission your Exchange 2013 or Exchange 2016 servers after the last mailbox has been moved off of it.

    > [!IMPORTANT]
    > If you rely on an auto attendant, keep at least one Exchange 2013 or Exchange 2016 running and available.

### Exchange 2013/Exchange 2016 to Exchange 2019 with Skype for Business 2015

In this scenario, you want to migrate your existing Exchange 2013 and Exchange 2016 servers to Exchange 2019 but remain on Skype for Business 2015.

### Skype for Business 2015 to Skype for Business 2019 with Exchange 2013/Exchange/2016

In this scenario, you want to migrate your existing Skype for Business 2015 server to Skype for Business 2019 but remain on Exchange 2013 or Exchange 2016.
