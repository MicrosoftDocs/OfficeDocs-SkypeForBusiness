---
title: "Plan Cloud Voicemail service"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "This article describes benefits, planning considerations, and requirements for implementing the Microsoft Coud Voicemail Service. For information on configuring Cloud Voicemail, see Configuring Cloud Voicemail."
---


# Plan Cloud Voicemail service

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 

This article describes benefits, planning considerations, and requirements for implementing the Microsoft Cloud Voicemail service. For information on configuring Cloud Voicemail, see [Configure Cloud Voicemail](configure-cloud-voicemail.md).

Cloud Voicemail enables all your Skype for Business 2019 users--whether their mailbox is homed on premises or online--to have access to the same voicemail service in the Microsoft Cloud. Cloud Voicemail provides the following benefits for both your on-premises and online users:


**NEED TO DECIDE WHETHER TEAMS SHOULD BE LISTED IN FIRST BULLET**

- Access to voicemail in their Exchange mailbox by using the Skype for Business Online, Teams (?), or Outlook clients 

- Ability to use the web-based portal to manage their voicemail options

Cloud Voicemail takes the place of Exchange Unified Messaging (UM) for voice messaging functionality. For more information about feature comparison, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md). 

Because UM is not in Exchange Server 2019, and Skype for Business Server 2019 doesn't use Exchange Online UM, you  need to plan your migration strategy based on your current environment, version of Skype for Business and Exchange servers, and so on.  For more information about migration and interoperability, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md). 

With Cloud Voicemail, your administration tasks are greatly simplified because:

- There is no need to configure the Exchange UM role.
- The setup tasks for Cloud Voicemail are simpler.
- Updates to voicemail functionality are delivered directly in the cloud, so your users always have access to the latest features and updates with less dependency on Cumulative Updates (CUs).
- You have the same set of controls for both on-premises and online Exchange mailboxes. For more information on these controls, see 
 [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US).

The following diagram shows Cloud Voicemail in a hybrid deployment:


![SfB Cloud Voicemail](../../sfbserver2019/media/plan-cloud-voice-mail-server1.png)

Unanswered calls are handled as follows:  

1. For users homed in Skype for Business 2019 on premises, unanswered calls are sent by the on-premises Skype for Business Server to the online Cloud Voicemail service. 
2. The service processes the voicemail, including transcription.
3.  The service then deposits the voicemail in the Exchange mailbox of the user, whether the mailbox is on-premises or online.  
4. Users can access their voicemail from either their Skype for Business Online, Teams (?), or Outlook client.

## Requirements

**NATHAN TO VERIFY THIS SECTION**

**We will refer to the hybrid connectivity docs as much as possible.**

The following requirements assume that you already have Skype for Business Server deployed in a supported topology.  For more information about deploying Skype for Business Server and supported topologies, see INSERT LINK HERE.

**WHAT ARE THE POSSIBLE STARTING TOPOLOGIES? REQUIREMENTS DEPEND ON STARTING POINT** 

    -  Full SfB Server split domain w or w/o hosted Exchange UM
    -  SfB on prem with hosted Exchange UM
    -  Exchange UM on prem


- **Hybrid connectivity.**  If you already have Skype for Business Server deployed, and you want to enable Cloud Voicemail for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments.  This is sometimes called a split domain configuration. Hybrid connectivity requires the following:

    - Azure Active Directory (AAD) Connect, which is used to synchronize your on-premises directory with Office 365. For more information, see Connect Active Directory with Azure Active Directory.

    - An Office 365 tenant with Skype for Business Online enabled.  

    - Federation enabled between your on-premises Skype for Business Server deployment and your Office 365 tenant. For more information, see [Configure federation with Skype for Business Online](configure-federation-with-skype-for-business-online.md).  

    - A shared Session Initiation Protocol (SIP) address space.  A SIP address is a unique identifier for each user on a network, similar to a phone number or an email address. For more information, see Configure federation with Skype for Business Online. 

    For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Skype for Business Online](configure-hybrid-connectivity.md)

- On-premises users must be enabled for voice and hosted voicemail in Skype for Business Server. For more information, see INSERT LINK HERE.

- **ANYTHING MISSING?**

NOTE: If you have an on-premises only deployment--that is, only Exchange and Skype for Business on-premises servers--but you want to take advantage of Cloud Voicemail, then you need the ON-PREM license.  **NEED DETAILS ABOUT THE ON-PREM-ONLY LICENSE.**

##Migration and interoperability

If you are planning to deploy Skype for Business Server 2019 and/or Exchange Server 2019, you must plan your migration carefully to ensure continued service for voice messaging.  Keep the following in mind:

- Exchange Server 2019 no longer provides Exchange UM functionality
- Skype for Business Server 2019 no longer integrates with Exchange Online UM

Version interoperability and supported topologies for Cloud Voicemail are listed in the following table.  For the preview release, Cloud Voicemail only works with Skype for Business Server and Exchange Server 2019 or Exchange Online.


|                               | Exchange Server 2013 | Exchange Server 2016 | Exchange Server 2019 | Exchange Online   |
|:---------------------------    |:---------------------|:---------------------|:------------------|:---------------------- |
| Skype for Business Server 2019 | Exchange Server UM | Exchange Server UM | Cloud Voicemail | Cloud Voicemail
Skype for Business Server 2015 | Exchange Server UM | Exchange Server UM |  | Cloud Voicemail <br> Exchange Online UM* |
Lync Server 2013 <br>  | Exchange Server UM | Exchange Server UM | | Cloud Voicemail <br> Exchange Online UM* |

\* Until deprecated.

Microsoft recommends the following migration paths:

-  If you are upgrading to Skype for Business Server 2019, you can use Exchange UM in Exchange Server 2013 or 2016, but you must upgrade to Cloud Voicemail if you are using Exchange Server 2019.

- If you are upgrading to Exchange Server 2019, and you are using previous versions of Exchange Server UM for Skype for Business Server voice messaging, Microsoft recommendeds that you upgrade to Skype for Business Server 2019 before the mailbox upgrade.  Otherwise, voice messaging capabilities will be lost. 


For more information about planning your migration, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).