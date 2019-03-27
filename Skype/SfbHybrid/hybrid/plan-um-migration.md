---
title: Plan for Skype for Business Server and Exchange Server migration 
ms.reviewer: 
author: dstrome
manager: serdars 
audience: ITPro 
ms.topic: article
localization_priority: Normal
ms.prod: skypeforbusiness-server-itpro
description: "This topic covers what you need to consider when you decide to migrate your existing Skype for Business Server or Exchange Server deployments to the latest version or to Skype for Business Online or Exchange Online."
---

# Plan for Skype for Business Server and Exchange Server migration

This topic covers what you need to consider when you decide to migrate your existing Skype for Business Server or Exchange Server deployments to the latest version or to Skype for Business Online or Exchange Online. What you can migrate, and when, heavily depends on what you've already got set up in your organization. Some features, such as Organization Auto Attendant, aren't available at General Availability (GA) but will be coming later in 2018.

## Feature changes in Exchange 2019 and Skype for Business Server 2019

With Exchange 2019 and Skype for Business Server 2019, we're making some changes to the features we support.

### Unified Messaging support in Exchange 2019

Unified Messaging (UM) has been deprecated in Exchange 2019. This means that Exchange 2019 no longer offers the following features:

- Voicemail
- Auto attendant

If you've deployed the UM role in Exchange 2013 or the UM service in Exchange 2016 and you want to upgrade to Exchange 2019, you'll need to migrate your voicemail to the Microsoft Cloud Voicemail service in Office 365. If you want to migrate your voicemail to Cloud Voicemail, take a look at the [Exchange 2013/Exchange 2016 and Skype for Business 2015 to Exchange 2019 and Skype for Business 2019](#exchange-2013exchange-2016-and-skype-for-business-2015-to-exchange-2019-and-skype-for-business-2019) section below.
> [!IMPORTANT]
> If users on your Exchange 2013 or Exchange 2016 servers have UM-enabled mailboxes, don't move them to Exchange 2019 before you upgrade your Skype for Business servers to Skype for Business Server 2019 and move users to them to avoid a voice messaging outage.

### PBX support in Exchange 2019 and Skype for Business Server 2019

Cloud Voicemail doesn't provide voice messaging functionality to Private Branch Exchanges (PBXs). If you're using Exchange Server Unified Messaging for PBXs and you want to upgrade to Exchange Server 2019, you'll need to adopt one of the three options listed in the blog post [New date for discontinuation of support for Session Border Controllers in Exchange Online Unified Messaging](https://blogs.technet.microsoft.com/exchange/2018/04/24/new-date-for-discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/) on the [Exchange Team Blog](https://blogs.technet.microsoft.com/exchange/).

### Exchange Online UM support in Skype for Business Server 2019

With Skype for Business Server 2019, we're moving from Exchange Online UM to Cloud Voicemail. When a user is moved to a Skype for Business 2019 server, they'll automatically start using Cloud Voicemail when configured for hosted voicemail. If you're currently using Exchange Online UM, you don't need to do anything other than move a user to Skype for Business Server 2019 to start using Cloud Voicemail. However, there are some changes to functionality you need to be aware of:

- Organizational Auto Attendant (the replacement for auto attendant in Exchange Online UM) isn't available at GA but will be available later in 2018.
- User voicemail settings in Outlook on the Web don't apply to Cloud Voicemail.

## On-premises UM migration scenarios

We support the following scenarios that will enable you to migrate users both to Exchange 2019 and to Cloud Voicemail. Later in 2018 we'll support additional scenarios that will let you migrate from additional versions of Exchange and Skype for Business server. We'll also provide additional features such as Organizational Auto Attendant.

- Exchange 2013/Exchange 2016 and Skype for Business Server 2015 to Exchange 2019 and Skype for Business Server 2019
- Skype for Business Server 2015 to Skype for Business Server 2019 with Exchange 2013/Exchange 2016

The following scenarios require that no PBX or SBC configurations exist as part of your current deployment and assume that you have UM configured on your on-premises Exchange servers. Each of these solutions also assumes that you've decided to configure a hybrid deployment between your on-premises Skype for Business servers and Office 365. For more information about Skype for Business hybrid deployments, see [Plan hybrid connectivity](plan-hybrid-connectivity.md).

### Exchange 2013/Exchange 2016 and Skype for Business 2015 to Exchange 2019 and Skype for Business 2019

In this scenario, you want to migrate your existing Exchange 2013, Exchange 2016, and Skype for Business 2015 servers to Exchange 2019 and Skype for Business 2019.

As mentioned earlier in this topic, Exchange 2019 no longer includes the UM service. This means that, for any mailboxes that you want to move to Exchange 2019, you need to use Cloud Voicemail to replace the functionality that was provided by the UM service. When you set up Skype for Business Server 2019 and a hybrid deployment between it and Office 365, Cloud Voicemail replaces these Exchange UM voicemail services.

The order in which you move users to Exchange 2019 and Skype for Business Server 2019 is critical to ensuring that voicemail functionality remains available to all users. Where voicemail is processed is also determined by where the Exchange and Skype for Business mailboxes and users are located. Take a look at the following table to see which combinations of Exchange and Skype for Business Server are supported and where voicemail is processed.

| Mailbox located on:            | User located on Skype for Business Server 2015 | User located on Skype for Business Server 2019  |
|--------------------------------|-----------------------------------------|------------------------------------------|
| Exchange 2013/Exchange 2016    | Exchange UM                             | Exchange UM                              |
| Exchange 2019                  | Not supported                           | Cloud Voicemail                          |

Before you start your migration to Skype for Business Server 2019 and Exchange 2019, keep the following in mind:

- Cloud voicemail doesn't support Organizational Auto Attendant at GA. If you want mailboxes moved to Cloud Voicemail to continue to be available via auto attendant, you'll need to keep at least one Exchange 2013 or Exchange 2016 server running the UM role or service available.
- You need to set up at least one Skype for Business 2019 server **and** move users to that server before you move their mailboxes to Exchange 2019. Failing to do so will result in those mailboxes being unable to receive voicemail messages.
- Calls sent to voicemail will be transferred to Cloud Voicemail where they will be recorded. After the call has ended, the voicemail message will be sent to the recipient's mailbox on the on-premises Exchange 2019 server. You need to take this voice traffic into account when determining whether your Internet connectivity is sufficient to support Cloud Voicemail.

Here are the high-level steps to complete this migration.

1. Install and configure Skype for Business Server 2019 on a new server.
2. Update your hybrid deployment configuration to include the new Skype for Business 2019 server.
3. Install and configure Exchange Server 2019 on a new server.
4. Move users from your Skype for Business 2015 server to your Skype for Business 2019 server.
5. Set the hosted voicemail policy for each user moved to Skype for Business Server 2019 to use Cloud Voicemail.
6. Move mailboxes from your Exchange 2013 or Exchange 2016 server to your Exchange 2019 server.
7. Decommission your Skype for Business 2015 servers after the last user has been moved off of them.
8. Decommission your Exchange 2013 or Exchange 2016 servers after the last mailbox has been moved off of them.

    > [!IMPORTANT]
    > If you rely on an auto attendant, keep at least one Exchange 2013 or Exchange 2016 running and available.

### Skype for Business Server 2015 to Skype for Business Server 2019 with Exchange 2013/Exchange 2016

In this scenario, you want to migrate your existing Skype for Business 2015 server to Skype for Business Server 2019 but remain on Exchange 2013 or Exchange 2016.

When Skype for Business Server 2015 and Skype for Business Server 2019 coexist in the same organization, they work seamlessly with Exchange UM and Cloud Voicemail to ensure that voicemail is correctly delivered to Exchange mailboxes. Whether Exchange UM or Cloud Voicemail processes the voicemail depends on whether the user is located on Skype for Business Server 2015 or Skype for Business Server 2019:

- If a user is located on Skype for Business Server 2015, Exchange UM will process the voicemail message.
- If a user is located on Skype for Business Server 2019, Cloud Voicemail will process the voicemail message.

Regardless of whether Exchange UM or Cloud Voicemail processes the voicemail message, the message will be stored in the user's Exchange mailbox.

Before you start your migration to Skype for Business Server 2019, keep the following in mind:

- Cloud voicemail doesn't support Organizational Auto Attendant at GA. If you want mailboxes moved to Cloud Voicemail to continue to be available via auto attendant, you'll need to keep at least one Exchange 2013 or Exchange 2016 server running the UM role or service available.
- Calls sent to voicemail will be transferred to Cloud Voicemail where they will be recorded. After the call has ended, the voicemail message will be sent to the recipient's mailbox on the on-premises Exchange server. You need to take this voice traffic into account when determining whether your Internet connectivity is sufficient to support Cloud Voicemail.

Here are the high-level steps to complete this migration.

1. Install and configure Skype for Business Server 2019 on a new server.
2. Update your hybrid deployment configuration to include the new Skype for Business 2019 server.
3. Move users from your Skype for Business 2015 server to your Skype for Business 2019 server.
4. Set the hosted voicemail policy for each user moved to Skype for Business Server 2019 to use Cloud Voicemail.
5. Decommission your Skype for Business 2015 servers after the last user has been moved off of them.

    > [!IMPORTANT]
    > If you rely on an auto attendant, keep at least one Exchange 2013 or Exchange 2016 running and available.
