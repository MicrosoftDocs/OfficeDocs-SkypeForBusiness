---
title: "Set up Cloud Voicemail"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: wasseemh, phans
ms.topic: article
ms.assetid: 9c590873-b014-4df3-9e27-1bb97322a79d
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto:
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Phone System
description: "Learn how to set up Cloud Voicemail for your users."
---

# Set up Cloud Voicemail

This article is for the Microsoft 365 or Office 365 admin as described in [About admin roles](/microsoft-365/admin/add-users/about-admin-roles) who wants to set up the Cloud Voicemail feature for everyone in the business. Cloud Voicemail requires Exchange mailboxes for users where it deposits voicemail messages. It doesn't support third-party email systems.

## Cloud Voicemail for Teams users

For Teams users, Cloud Voicemail is automatically set up and provisioned. A Microsoft Teams Phone license is not required for Cloud Voicemail.

## Help your users learn Teams voicemail features

We have the following information for your users on using and managing voicemail in Teams:

- [Check your voicemail in Teams](https://support.microsoft.com/office/check-your-voicemail-in-teams-f8d568ce-7329-4fe2-a6a2-325ec2e2b419)
- [Manage your call settings in Teams](https://support.microsoft.com/office/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f)

## Setting up Cloud Voicemail to work with on-premises users

You can use Cloud Voicemail to provide voice mail functionality to your users who have mailboxes on your Exchange Servers, or for users who are using Skype for Business Server. This section provides information for these scenarios. 

### Set up Cloud Voicemail for Exchange Server Mailbox Users

The following information is about configuring Cloud Voicemail to work with Microsoft Teams Phone users who have their mailbox on Exchange Server.

1. Voicemail messages are delivered to users' Exchange mailbox via SMTP routed through Exchange Online Protection. To enable successful delivery of these messages, be sure that Exchange Connectors are configured correctly between your Exchange servers and Exchange Online Protection; [Use Connectors to Configure Mail Flow](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

2. To enable Voicemail features such as customizing greetings and visual voicemail in Skype for Business clients, connectivity from Microsoft 365 or Office 365 to the Exchange server mailbox via Exchange Web Services is required. To enable this connectivity, you must configure the new Exchange Oauth authentication protocol described in [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help), or run the Exchange Hybrid Wizard from Exchange 2013 CU5 or greater. Additionally, you must configure integration and Oauth between Skype for Business Online and Exchange server described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises).

### Set up Cloud Voicemail for Skype for Business Server Users

To configure Skype for Business server users for Cloud Voicemail, see [Plan Cloud Voicemail service for on-premises users](/skypeforbusiness/hybrid/plan-cloud-voicemail).

## Enabling protected voicemail in your organization

When someone leaves a voicemail message for a user in your organization, the voicemail is delivered to the user's mailbox as an email message attachment. Using mail flow rules to apply message encryption, you can prevent those voicemail messages from being forwarded to other recipients. When you enable protected voicemail, users can listen to protected voicemail messages by calling into their voicemail mailbox or by opening the message in Outlook, Outlook on the web, or in Outlook for Android or iOS. Protected voicemail messages can't be opened in Skype for Business or Microsoft Teams.

For more information about message encryption, see [Define mail flow rules to encrypt email messages](/microsoft-365/compliance/define-mail-flow-rules-to-encrypt-email).
