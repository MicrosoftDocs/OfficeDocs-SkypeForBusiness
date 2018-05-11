---
title: "Plan Cloud Voicemail Service"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "This topic describes benefits, planning considerations, and requirements for implementing the Microsoft Coud Voicemail Service. For information on configuring Cloud Voicemail, see Configuring Cloud Voicemail."
---
<!-- PM Roy Kuntz  -->

# Plan Cloud Voicemail Service

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 

This topic describes benefits, planning considerations, and requirements for implementing the Microsoft Coud Voicemail Service. For information on configuring Cloud Voicemail, see Configuring Cloud Voicemail.

Cloud Voicemail enables all your Skype for Business users--whether they are homed on premises or online--to have access to the same voicemail service in the Microsoft Cloud. Cloud Voicemail provides the following benefits for both your on-premises and online users:

- Access to voicemail in their Exchange mailbox by using the Skype for Business Online or Teams client. 

- Ability to use the web-based portal to manage their voicemail options. 

- **WHAT ELSE?**

If you have an on-premises Skype for Business Server, Cloud Voicemail simplifies the task of maintaining a hybrid environment in which some of your users are homed on premises and some are homed online.  

Cloud Voicemail provides the same functionality as Exchange Unified Messaging (UM) **TRUE?**. Your administration tasks are greatly simplified because:

- There is no need to configure the Exchange UM role.
- The setup tasks for Cloud Voicemail are simpler.
- Updates to voicemail functionality are delivered directly in the cloud, so your users always have access to the latest features and updates with less dependency on Cumulative Updates (CUs).
- You have the same set of controls for both on-premises and online users.  For more information on these controls, see 
 [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US).

**SPECIFICALLY, HOW IS CLOUD VOICEMAIL EASIER? HOW DOES THE CONFIG CHANGE?  DO YOU STILL NEED TO SET UP A DIAL PLAN? DOES THE SPLIT DOMAIN SETUP FOR HYBRID CONNECTIVITY TAKE CARE OF ALL SHARED SIP ADDRESS SPACE REQUIREMENTS, AND SO ON...**  

Note:  Exchange UM is being deprecated.  For more information, see INSERT LINK HERE.

The following diagram shows Cloud Voicemail in a hybrid deployment:

**IS THE DIAGRAM ACCURATE?**


![SfB Cloud Voicemail](../../sfbserver2019/media/plan-cloud-voice-mail-server1.png)

Unanswered calls are handled as follows:  **IS THE FOLLOWING CORRECT?**

1. For users homed on premises, unanswered calls are sent by the on-premises Skype for Business Server to the online Cloud Voicemail Service. 
2. For users homed online, unanswered calls are sent directly to the online service.  
3. The Service processes the voicemail, including transcription.
4.  The Service then deposits the voicemail in the Exchange mailbox of the user, whether the mailbox is on-premises on online.  
5. Users have access to their voicemail from either their Skype for Business Online or Teams client, and from their Exchange mailbox.

##Requirements

The following requirements assume that you already have Skype for Business Server deployed in a supported topology.  For more information about deploying Skype for Business Server 2019 and supported topologies, see INSERT LINK HERE.

If you already have Skype for Business Server deployed, and you want to enable Cloud Voicemail for both your on-premises and online users, the following are required:        

  **IS THE FOLLOWING CORRECT?**

- Hybrid connectivity between your on-premises server and the online service. This is sometimes called a split domain configuration. For details, see Plan hybrid connectivity and Configure hybrid connectivity.

- Azure Active Directory (AAD) Connect, which is used to synchronize your on-premises directory with Office 365. For more information, see Connect Active Directory with Azure Active Directory.

- An Office 365 tenant with Skype for Business Online enabled.  If you want to enable Teams, see Migration to Teams.

- You must have the following licenses:    **WHAT ARE THE REQUIRED LICENSES?**

- Enabled federation between your on-premises Skype for Business Server deployment and your Office 365 tenant. For more information, see Configure federation with Skype for Business Online.  

- Enabled shared Session Initiation Protocol (SIP) address space.  A SIP address is a unique identifier for each user on a network, similar to a phone number or an email address. For more information, see Configure federation with Skype for Business Online. 

- On-premises users must be enabled for voice and hosted voicemail in Skype for Business Server, and the necessary Skype for Business and Exchange attributes must be synchronized to the cloud. For more information, see INSERT LINK HERE.

- **ANYTHING MISSING?**

##Interoperability and supported topologies

Version interoperability and supported topologies for Cloud Voicemail are listed below:  **IS THE FOLLOWING ACCURATE?**

|                                | Exchange Server 2016 | Exchange Server 2019 | Exchange Online   |
|:---------------------------    |:---------------------|:---------------------|:------------------|
|Skype for Business Server 2015 |Exchange Server UM <br> Cloud Voicemail Service |Cloud Voicemail Service |Exchange Server UM (until deprecated)<br>Cloud Voicemail Service|
|Skype for Business Server 2019 | Cloud Voicemail Service | Cloud Voicemail Service | Exchange Server UM (until deprecated)<br>Cloud Voicemail Service |
Microsoft Phone System | Cloud Voicemail Service | Cloud Voicemail Service | Cloud Voicemail Service |
PBX on premises | Exchange Server UM | Not supported | Exchange Server UM (until deprecated)




**QUESTIONS:**

**THE GOAL OF THIS TOPIC SHOULD BE HIGH-LEVEL WITH POINTERS TO OTHER DOCS FOR DETAILS ABOUT HYBRID CONNECTIVITY, CONFIGURING VOICEMAIL, EXCHANGE UM MIGRATION, ETC.  HOWEVER, ARE WE MISSING IMPORTANT CONCEPTS AND PREREQUISITES SPECIFIC TO THIS FEATURE/SCENARIO THAT SHOULD BE DESCRIBED IN THIS DOCUMENT?**

**HOW MUCH DO WE NEED TO SAY ABOUT EXCHANGE UM IN THIS TOPIC?  DO WE NEED TO DOCUMENT MIXED SCENARIOS?  FOR EXAMPLE, CUSTOMER HAS SOME CUSTOMERS STILL USING EXCHANGE UM ON PREM, BUT SOME USERS USING CLOUD VOICEMAIL? CUSTOMERS WHO STILL HAVE AN ONPREM PBX?  CUSTOMERS WITH MIXED VERSIONS OF SERVERS?**

**DO WE NEED SPECIFIC GUIDANCE ON EXCHANGE UM MIGRATION TO VOICEMAIL?  IF YES, WHAT ARE THE MIGRATION STEPS?  DIAL PLANS? LICENSES? SPLIT DOMAIN AND MOVING USERS ONLINE?**

**HOW LONG IS EXCHANGE UM BEING SUPPORTED?** 





                                 
                 
















