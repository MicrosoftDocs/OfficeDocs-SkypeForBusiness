---
title: Plan Cloud Voicemail service for on-premises users| PBX Skype for Business Server 2019 
ms.reviewer: 
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.collection: 
description: "This article describes benefits, planning considerations, and requirements for implementing the Microsoft Cloud Voicemail service. For information on configuring Cloud Voicemail, see Configuring Cloud Voicemail."
---

# Plan Cloud Voicemail service for on-premises users

## Overview

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

This article describes benefits, planning considerations, and requirements for implementing the Microsoft Cloud Voicemail service for your on-premises users. For information on configuring Cloud Voicemail, see [Configure Cloud Voicemail service](configure-cloud-voicemail.md).

Cloud Voicemail takes the place of Exchange Unified Messaging (UM) in providing voice messaging functionality for Skype for Business 2019 voice users who have mailboxes on Exchange Server 2019 or Exchange Online. Cloud Voicemail provides the following benefits for both your on-premises and online users:

- Voicemail answering and deposit functionality with enhanced speech transcription

- Access to voicemail in the user's Exchange mailbox by using the Skype for Business Online or Outlook clients

- The ability to use the Microsoft 365 admin center to manage voicemail options

- Support for Exchange mailboxes on premises or in the cloud

- Leveraging of existing user greetings from Exchange Online Unified Messaging

> [!Important]
> Skype for Business Online was retired on July 31, 2021. Users can no longer access voicemail in their Exchange mailbox through the Skype for Business Online client.

For more information about feature comparison, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).

Skype for Business Server 2019 continues to use Exchange UM for users whose mailboxes are on previous versions of Exchange Server (2013, 2016).  Understanding which voicemail solution will be used based on the Exchange Server and Skype for Business Server version is an important part of planning for migration to either Skype for Business Server 2019 or Exchange Server 2019. For more information about migration and interoperability, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).

With Cloud Voicemail, your administration tasks are greatly simplified because:

- There is no need to configure the Exchange UM role.
- The setup tasks for Cloud Voicemail are simpler.
- Updates to voicemail functionality are delivered directly in the cloud, so your users always have access to the latest features and updates with less dependency on Cumulative Updates (CUs).
- You have the same set of controls for both on-premises and online Exchange mailboxes. For more information on these controls, see [Set up Phone System voicemail](https://support.office.com/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d).

The following diagram shows Cloud Voicemail in a hybrid deployment:

![SfB Cloud Voicemail.](../../sfbserver2019/media/plan-cloud-voice-mail-server1.png)

Unanswered calls are handled as follows:  

1. For users homed in Skype for Business 2019 on premises, unanswered calls are sent by the on-premises Skype for Business Server to the online Cloud Voicemail service.
2. The service processes the voicemail, including transcription.
3. The service then deposits the voicemail in the Exchange mailbox of the user, whether the mailbox is on-premises or online.  
4. Users can access their voicemail from either their Skype for Business or Outlook client.

## Requirements

The following requirements assume that you already have Skype for Business Server deployed in a supported topology.  Your requirements depend on your scenario:

- If you are already using Exchange UM online and you upgrade to Skype for Business 2019, you will need to modify your hosted voicemail policy and verify that your hosting providers are set correctly. For more information, see [Configure Cloud Voicemail service](configure-cloud-voicemail.md).

- If you are using Exchange UM on premises, or you have a mix of users using Exchange UM online and on premises, you will need modify both your hosted voicemail policy and hosting provider.  For more information, see [Configure Cloud Voicemail service](configure-cloud-voicemail.md).

- For a new configuration of Cloud Voicemail, follow the steps outlined in [Configure Cloud Voicemail service](configure-cloud-voicemail.md).

In addition to the requirements above, the below requirements must be configured to connect to the Microsoft Cloud Voicemail service:

- Hybrid connectivity. If you already have Skype for Business Server deployed, and you want to enable Cloud Voicemail for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md).

- On-premises users must be enabled for Enterprise Voice and Hosted Voicemail in Skype for Business Server.

- An External Exchange Web Services (EWS) URL and Autodiscover must be set up or some Cloud Voicemail features will be limited.

- If you have an on-premises Exchange server, set up Cloud Voicemail using the steps in [Set up Cloud Voicemail for Exchange Server Mailbox Users](/microsoftteams/set-up-phone-system-voicemail#set-up-cloud-voicemail-for-exchange-server-mailbox-users).

## Migration and interoperability

If you are planning to deploy Skype for Business Server 2019 and/or Exchange Server 2019, you must plan your migration carefully to ensure continued service for voice messaging. Keep the following in mind:

- Exchange Server 2019 no longer provides Exchange UM functionality
- Skype for Business Server 2019 no longer integrates with Exchange Online UM

Version interoperability and supported topologies for Cloud Voicemail are listed in the following table, which compares the Skype for Business Server versions the user might be homed on with the possible version providing their Exchange Mailbox. You need to use Cloud Voicemail if you want to use Skype for Business 2019 with Exchange Online or Exchange Server 2019.

| Skype/Lync version | Exchange Server 2013 | Exchange Server 2016 | Exchange Server 2019 | Exchange Online   |
|:---    |:--- |:--- |:--- |:---  |
| Skype for Business Server 2019 | Exchange Server UM | Exchange Server UM | Cloud Voicemail | Cloud Voicemail |
| Skype for Business Server 2015 | Exchange Server UM | Exchange Server UM | Not supported | Cloud Voicemail |
| Lync Server 2013 <br>  | Exchange Server UM | Exchange Server UM | Not Supported | Cloud Voicemail |

Microsoft recommends the following migration paths:

- If you are upgrading to Skype for Business Server 2019, you can use Exchange UM in Exchange Server 2013 or 2016, but you must upgrade to Cloud Voicemail if you are using Exchange Server 2019.
- If you are upgrading to Exchange Server 2019, and you are using previous versions of Exchange Server UM for Skype for Business Server voice messaging, Microsoft recommends that you upgrade to Skype for Business Server 2019 before the mailbox upgrade.  Otherwise, voice messaging capabilities will be lost.
- If you are upgrading to Skype for Business Server 2019, and have Skype for Business Server 2015 configured for voicemail with Exchange Online UM, users' voicemail will automatically migrate from Exchange Online UM to Cloud Voicemail when their account is moved to Skype for Business Server 2019. 

For more information about planning your migration, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).