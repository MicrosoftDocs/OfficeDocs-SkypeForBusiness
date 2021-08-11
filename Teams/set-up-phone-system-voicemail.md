---
title: "Set up Cloud Voicemail"
author: dstrome
ms.author: dstrome
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
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn how to set up Cloud Voicemail for your users. "
---

# Set up Cloud Voicemail

This article is for the Microsoft 365 or Office 365 admin as described in [About admin roles](/microsoft-365/admin/add-users/about-admin-roles) who wants to set up the Cloud Voicemail feature for everyone in the business.

> [!NOTE]
> Cloud Voicemail supports depositing voicemail messages only in an Exchange mailbox and doesn't support any third-party email systems. 

> [!NOTE]
> When a delegate answers a call on behalf of a delegator, notifications are not available in Cloud Voicemail. Users can receive notifications for missed calls.

## Cloud-only environments: Set up Cloud Voicemail for Online Phone System users

For Online Phone System users, Cloud Voicemail is automatically set up and provisioned for users after you assign a **Phone System** license to the users. 

> [!NOTE]
> For Online Skype for Business Phone System users with on-premises provided phone numbers, you may need to enable hosted voice mail with [Set-CsUser -HostedVoicemail $True](/powershell/module/skype/set-csuser?view=skype-ps). 

## Set up Cloud Voicemail for Exchange Server Mailbox Users

The following information is about configuring Cloud Voicemail to work with users who are online for Phone System but have their mailbox on Exchange Server. 
  
1. Voicemail messages are delivered to users' Exchange mailbox via SMTP routed through Exchange Online Protection. To enable successful delivery of these messages, please be sure that Exchange Connectors are configured correctly between your Exchange servers and Exchange Online Protection; [Use Connectors to Configure Mail Flow](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow). 

2. To enable Voicemail features such as customizing greetings and visual voicemail in Skype for Business clients, connectivity from Microsoft 365 or Office 365 to the Exchange server mailbox via Exchange Web Services is required. To enable this connectivity, you must configure the new Exchange Oauth authentication protocol described in [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help), or run the Exchange Hybrid Wizard from Exchange 2013 CU5 or greater. Additionally, you must configure integration and Oauth between Skype for Business Online and Exchange server described in [Configure Integration and OAuth between Skype for Business Online and Exchange Server](/skypeforbusiness/deploy/integrate-with-exchange-server/oauth-with-online-and-on-premises). 

## Set up Cloud Voicemail for Skype for Business Server Users

To configure Skype for Business server users for Cloud Voicemail, please see [Plan Cloud Voicemail service for on-premises users](/skypeforbusiness/hybrid/plan-cloud-voicemail).

## Enabling protected voicemail in your organization

When someone leaves a voicemail message for a user in your organization, the voicemail is delivered to the user's mailbox as an email message attachment. Using mail flow rules to apply message encryption, you can prevent those voicemail messages from being forwarded to other recipients. When you enable protected voicemail, users can listen to protected voicemail messages by calling into their voicemail mailbox or by opening the message in Outlook, Outlook on the web, or in Outlook for Android or iOS. Protected voicemail messages can't be opened in Skype for Business or Microsoft Teams.

For more information about message encryption, see [Email encryption](/microsoft-365/compliance/email-encryption?view=o365-worldwide).

To set up protected voicemail, do the following:

1. Go to https://admin.microsoft.com and sign in using an account with global administrator permissions.
2. Select **Show all** and then go to **Admin centers** > **Exchange**.
3. In the Exchange Admin Center, select **Mail flow** > **Rules**.
4. Select **+** **Add**, and then select **Apply Office 365 Message Encryption and rights protection to messages**.
5. Provide a name for the new mail flow rule and then under **Apply this rule if**, select **The message properties** > **Include the message type** > **Voice mail**. Select **OK**.
6. Under **Do the following**, select **Apply Office 365 Message Encryption and rights protection to the message with** and then select **Select one**. Under **RMS template**, select **Do not forward**. Select **OK** and then **Save**.
    > [!NOTE]
    > If the **RMS template** list is empty, you need to set up Message Encryption. For more information about setting up Message Encryption, see the following articles:
    > - [Set up new Message Encryption capabilities](/microsoft-365/compliance/set-up-new-message-encryption-capabilities?view=o365-worldwide)
    > - [Configuring and managing templates for Azure Information Protection](/information-protection/deploy-use/configure-policy-templates)
    > - [Do Not Forward option for emails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails)

## Help your users learn Teams voicemail features

We have the following information for your users on managing their voicemail settings as well as other calling features in Teams:

- [Manage your call settings in Teams](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f). This article explains how to manage all end-user Teams calling features. 

## Help your users learn Skype for Business voicemail features

We have training information and articles to help your users be successful with Skype for Business voicemail. Point them to the following articles:

- [Check Skype for Business voicemail and options](https://support.office.com/article/2deea7f8-831f-4e85-a0d4-b34da55945a8): This article explains how to listen to your voicemail in Skype for Business, change your voice mail greeting, change your voicemail settings, and listen to your voicemail at different speeds.

- [Skype for Business 2016 training](https://support.office.com/article/eb2081bc-fd0a-4eda-94da-5a39f369ee74)

## Related topics
[Set up Skype for Business Online](/skypeforbusiness/set-up-skype-for-business-online/set-up-skype-for-business-online)

[Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)

[Plan for Skype for Business Server and Exchange Server migration](/SkypeForBusiness/hybrid/plan-um-migration)
