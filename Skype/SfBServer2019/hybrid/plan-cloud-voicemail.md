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

Cloud Voicemail enables all your Skype for Business 2019 users--whether they are homed on premises or online--to have access to the same voicemail service in the Microsoft Cloud. Cloud Voicemail provides the following benefits for both your on-premises and online users:

- Access to voicemail in their Exchange mailbox by using the Skype for Business Online, Teams, or Outlook clients. 

- Ability to use the web-based portal to manage their voicemail options. 

- **WHAT ELSE?**

If you have an on-premises Skype for Business Server, Cloud Voicemail simplifies the task of maintaining a hybrid environment in which some of your users are homed on premises and some are homed online.  

Cloud Voicemail takes the place of Exchange Unified Messaging (UM) and provides much of the same functionality. **Need specifics on Exchange UM functionality**    Because Exchange UM is being deprecated, if you are currently using Exchange UM, you will need to plan your migration strategy based on your current environment, version of Skype for Business and Exchange servers, and so on.  For more information about migration and interoperability, see INSERT LINK HERE. **TRUE?**. 

With Cloud Voicemail, your administration tasks are greatly simplified because:

- There is no need to configure the Exchange UM role.
- The setup tasks for Cloud Voicemail are simpler.
- Updates to voicemail functionality are delivered directly in the cloud, so your users always have access to the latest features and updates with less dependency on Cumulative Updates (CUs).
- You have the same set of controls for both on-premises and online users.  For more information on these controls, see 
 [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US).

**SPECIFICALLY, HOW IS CLOUD VOICEMAIL EASIER? HOW DOES THE CONFIG CHANGE?  DO YOU STILL NEED TO SET UP A DIAL PLAN? DOES THE SPLIT DOMAIN SETUP FOR HYBRID CONNECTIVITY TAKE CARE OF ALL SHARED SIP ADDRESS SPACE REQUIREMENTS, AND SO ON...**  

The following diagram shows Cloud Voicemail in a hybrid deployment:

**MAKE ROY'S CHANGE TO DIAGRAM**


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
- 
   -Enabled federation between your on-premises Skype for Business Server deployment and your Office 365 tenant. For more information, see Configure federation with Skype for Business Online.

   - Enabled shared Session Initiation Protocol (SIP) address space. A SIP address is a unique identifier for each user on a network, similar to a phone number or an email address. For more information, see Configure federation with Skype for Business Online. 

- Azure Active Directory (AAD) Connect, which is used to synchronize your on-premises directory (and the necessary Skype for Business and Exchange attributes) with Office 365. For more information, see Connect Active Directory with Azure Active Directory.   

- An Office 365 tenant with Skype for Business Online license enabled.  

 NOTE: If you have an on-premises only deployment--that is, Exchange and Skype for Business on-premises only deployments--then you need the ON-PREM license.  **NEED DETAILS ABOUT THE ON-PREM-ONLY LICENSE.**

- On-premises users must be enabled for voice and hosted voicemail in Skype for Business Server, For more information, see INSERT LINK HERE.

- **ANYTHING MISSING?**

##Migration and interoperbility

**HOW GNARLY WILL MIGRATION BE?  DO WE LINK OFF TO MORE GNARLY ARTICLE?**

**NEED TO EXPLAIN VARIOUS MIGRATION PATHS...  NEED TO EXPLAIN FIRST TWO ROWS...  IF YOU ARE RUNNING EXCHANGE SERVER 2016, EXCHANGE SERVER 2019, SFB Server 2015, 2019, ETC.** 

**ACCORDING TO ROY, FOR TAP, SFB 2015 DOES NOT WORK WITH CLOUD VOICEMAIL, SO MUST UPGRADE TO SFB 2019.  WILL 2015 WORK WITH CLOUD VOICEMAIL FOR BETA?  ROY FOLLOWING UP...**

**AT TAP, GUIDANCE IS UPGRADE SFB 2019 FIRST, THEN UPGRADE TO EXCHANGE SERVER 2019, THE START MOVING USERS TO EXCHANGE SERVER 2019...**

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

**DO WE NEED SPECIFIC GUIDANCE ON EXCHANGE UM MIGRATION TO VOICEMAIL IN THIS DOC?  OR POINT TO MORE GNARLY MIGRATION DOC?  WHAT ARE THE SUPPORTED MIGRATION PATHS FOR BETA, GA?    DIAL PLANS? LICENSES? SPLIT DOMAIN AND MOVING USERS ONLINE?**

**HOW LONG IS EXCHANGE UM BEING SUPPORTED?** 

**NOTE: IT IS NOT THE PURPOSE OF THIS DOC TO DESCRIBE TAP FUNCTIONALITY.  GOAL IS BETA AT END OF JUNE.**





                                 
                 
















