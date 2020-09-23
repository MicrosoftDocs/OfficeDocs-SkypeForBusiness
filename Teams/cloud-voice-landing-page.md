---
title: Voice in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - M365-voice
ms.reviewer: crowe
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.cloudvoice
  - seo-marvel-apr2020
search.appverid: MET150
description: Learn more about Microsoft voice solutions, and understand the necessary deployment decisions that you will face.
appliesto: 
  - Microsoft Teams
---

# Voice - Phone System and PSTN connectivity solutions

This article helps you decide which Microsoft voice solution is right for your organization. The article also provides a roadmap to content that will enable you to implement your chosen solution. This article describes:

- **Phone System** -  Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud with Microsoft Teams.

- **Public Switched Telephone Network (PSTN)** connectivity options - A choice between using Microsoft as your telephony carrier or connecting your own telephony carrier to Microsoft Teams. Combined with Phone System, PSTN connectivity options enable your users to make phone calls all over the world.

- **Migrating your existing voice solution** - What you need to think about when migrating your existing voice solution to Teams.

> [!Important]
> This article focuses on voice solutions with Microsoft Teams. While solutions with Skype for Business Online are still available (as described in [Microsoft telephony solutions](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions), it's important to understand that Skype for Business Online will be retired on July 31, 2021, after which the service will no longer be accessible. In addition, PSTN connectivity between your on-premises environment whether through Skype for Business Server or Cloud Connector Edition and Skype for Business Online will no longer be supported. This article introduces how you can connect your on-premises telephony network to Teams by using Direct Routing.




## Phone System

Phone System is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 or Office 365 cloud with Microsoft Teams.

Phone System works with Teams or Skype for Business clients and certified devices. Phone System allows you to replace your existing PBX system with a set of features directly delivered from Microsoft or Office 365 and tightly integrated into the company’s cloud productivity experience. 

This article introduces several key features and functionality related to Phone System and the deployment decisions you will need to consider. The following features are discussed in greater detail in this article:

- [Auto attendants and call queues](#auto-attendants-and-call-queues)
- [Voicemail](#voicemail)
- [Calling identity](#calling-identity)
- [Dial plans and call routing](#dial-plans)
- [Phone numbers from Microsoft](#phone-numbers-from-microsoft)
- Emergency calling

For information about all Phone System features and functionality and how to set up Phone System, see the following articles:

- [What is Phone System](what-is-phone-system-in-office-365.md) and [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md).

- [Set up Phone System in your organization](setting-up-your-phone-system.md).

For information about managing supported devices, see [Manage your devices in Microsoft Teams](devices/device-management.md) and [Teams Marketplace](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).


### Auto attendants and Call queues

Auto attendants allow you to set up menu options to route calls based on caller input. Call queues are waiting areas for callers. Used together, auto attendants and call queues can easily route callers to the appropriate person or department in your organization.

For information about auto attendants and call queues, see the following articles:

- [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md).
- [Set up an auto attendant](create-a-phone-system-auto-attendant.md). 
- [Create a call queue](create-a-phone-system-call-queue.md) 

For an example of how a fictitious, multinational corporation implemented auto attendants and call queues, see [Contoso case study: Auto attendants and call queues](voice-case-study-call-queues.md).

### Voicemail

Cloud Voicemail, powered by Azure Voicemail services, supports voicemail deposits to Exchange mailboxes only and doesn't support third-party email systems. For online only users, cloud voicemail is automatically set up and provisioned for users after they are assigned a Phone System license. For Phone System users with an Exchange mailbox, you will need to perform extra configuration steps. 

Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs might require that you disable voicemail transcription for specific users or everyone throughout the organization.

For more information about Cloud Voicemail, see the following articles:

- [Set up Cloud Voicemail](set-up-phone-system-voicemail.md)
- [Set voicemail policies in your organization](set-up-phone-system-voicemail.md#setting-voicemail-policies-in-your-organization)



### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. For information about configuring caller ID or to change or block the caller ID, see [Set the caller ID for a user](set-the-caller-id-for-a-user.md). 


### Dial plans

A dial plan is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

You will need to decide the following: 

- Does my organization need a customized dial plan?
- Which users require a customized dial plan?
- Which tenant dial plan should be assigned to each user?

For more information, see the following articles: 

- [What are dial plans?](what-are-dial-plans.md)
- [Plan for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans)
- [Create and manage dial plans](create-and-manage-dial-plans.md). 


### Phone numbers from Microsoft

Microsoft has two types of telephone numbers available: *subscriber* (user) numbers, which can be assigned to users in your organization, and *service* numbers, available as toll and toll-free service numbers, which have higher concurrent call capacity than subscriber numbers and can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues.

You will need to decide:

- Which user locations need new phone numbers from Microsoft?
- Which type of telephone number (subscriber or service) do I need? 
- How do I port existing phone numbers to Teams?

For more information about managing phone numbers in your organization, including getting new numbers or transferring exsiting numbers, see the following articles:

- [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) 
- [Getting phone numbers for your users](getting-phone-numbers-for-your-users.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Transfer phone numbers to Microsoft Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md)




## Public Switched Telephone Network (PSTN) connectivity options

Phone System provides complete PBX capabilities for your orgaization. However, to enable your users to make calls outside your organization, you need to connect Phone System to the Public Switched Telephone Network (PSTN). To connect Phone System to the PSTN, you can choose one--or a combination--of the following options:

- **Phone System with Calling Plan** as your PSTN carrier. An all-in-the-cloud Microsoft solution.

- **Phone System with your own PSTN carrier** by using Direct Routing to connect your on-premises environment to Teams.

You can choose a combination of options in case you need to design a solution for a complex environment or you are managing a multi-step migration.

### Phone System with Calling Plan (Microsoft 365 or Office 365)

Phone System with Calling Plan is Microsoft's all-in-the-cloud voice solution for Teams users.

This option connects the Microsoft 365 or Office 365 Phone System to the Public Switched Telephone Network (PSTN) to enable calls to landlines and mobile phones around the world. With Calling Plan, Microsoft is your PSTN carrier as shown in the following diagram:

INSERT DIAGRAM HERE

If you answer yes to the following, then this is the right solution for you:

- Calling Plan is available in your region.
- You do not need to retain your current PSTN carrier.
- You want to use Microsoft-managed access to the PSTN.
- You do not want to manage Session Border Controllers on your own.
- Teams has all the features that your organization requires.

This option requires uninterrupted connection to Microsoft 365 or Office 365.

With this option: 

- You get Microsoft Phone System with added Domestic or International Calling Plans that enable calling to phones around the world (depending on the level of service being licensed).

- You do not require deployment or maintenance of an on-premises deployment--because PSTN Calling Plan operates out of Microsoft 365 or Office 365.

- Note:  If necessary, you can choose to connect a supported SBC via Direct Routing for interoperability with 3rd-party PBX, analog devices, and other 3rd party telephony equipment supported by the SBC.

For more information about Calling Plans, see the following articles:

- [Which Calling Plan is right for you?](calling-plan-landing-page.md)
- [How to buy a Calling Plan](calling-plans-for-office-365.md)
- [Country and region availability for Calling Plans](https://docs.microsoft.com/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)
- [Set up Calling Plans](set-up-calling-plans.md)




### Phone System with own PSTN carrier with Direct Routing

This option connects Phone System in Microsoft 365 or Office 365 to your telephony network. 

If you answer yes to the following questions, then this is the right solution for you:

- You want to use Teams with Phone System.
- You need to retain your current PSTN carrier.
- You want to mix routing, some calls are going via Calling Plans, some via your carrier.
- You need to interoperate with 3rd party PBXs and/or equipment such us overhead pagers, analog devices, and so on.
- Teams has all the features that your organization requires.


This option requires the following:

- Uninterrupted connection to Microsoft 365 or Office 365.

- Deploying and maintaining a supported Session Border Controller (SBC).

- A contract with third-party carrier.
  (Unless deployed as an option to provide connection to 3rd party PBX, analog devices, or other telephony equipment for users who are on Phone System with Calling Plans.)

With this option:

- You connect your own supported SBC to Microsoft Phone System without need of additional on-premises software.

- You can use virtually any telephony carrier with Microsoft Phone System.

- You can choose to configure and manage this option, or it can be configured and managed by your carrier or partner (ask if your carrier or partner provides this option).

- You can configure interoperability between your telephony equipment—such as a third-party PBX and analog devices—and Microsoft Phone System.

For more information about Direct Routing, see the following articles:

[Phone System Direct Routing](direct-routing-landing-page.md)
[Plan Direct Routing](direct-routing-plan.md)
[Configure Direct Routing](direct-routing-configure.md)
[List of Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md)

## Considerations for migrating your voice solution to Teams

There are four possible calling scenarios when moving to TeamsOnly mode:

- [A user in Skype for Business Online, with a Microsoft Calling Plan](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-online-with-microsoft-calling-plans). Upon upgrade, this user will continue to have a Microsoft Calling plan.

- [A user in Skype for Business Online, with on-premises voice functionality](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-online-with-on-premises-voice) through Skype for Business on-premises or Cloud Connector Edition. The user’s upgrade to Teams needs to be coordinated with migration of the user to Direct Routing to ensure the TeamsOnly user has PSTN functionality.

- [A user in Skype for Business on-premises with Enterprise Voice](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-server-on-premises-with-enterprise-voice-to-direct-routing), who will be moving to online and keeping on-premises PSTN connectivity.  Migrating this user to Teams requires moving the user’s on-premises Skype for Business account to the cloud, and coordinating that move with migration of the user to Direct Routing. 

- [A user in Skype for Business on-premises with Enterprise Voice](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-server-on-premises-with-enterprise-voice-to-microsoft-calling-plan), who will be moving to online and using a Microsoft Calling plan.  Migrating this user to Teams requires moving the user’s on-premises Skype for Business account to the cloud, and coordinating that move with either A) the port of that user’s phone number to a Microsoft Calling Plan or B) assigning a new subscriber number from available regions.

For more information about these scenarios, see the following articles:

- [PSTN considerations when upgrading to Teams — for IT administrators](upgrade-to-teams-on-prem-pstn-considerations.md)

- [Contoso voice migration case study](voice-case-study-overview.md). The case study describes how a fictional multi-national corporation, Contoso, implemented a Teams voice solution for their organization.  It contains the following articles:

  - [Teams upgrade plan](voice-case-study-migration-plan.md)
  - [Phone System and PSTN connectivity options](voice-case-study-phone-system.md)
  - [Location-Based Routing implementation](voice-case-study-location-based-routing)
  - [Emergency calling](voice-case-study-emergency-calling.md)
  - [Auto attendants and call queues](voice-case-study-call-queues.md)
  - [Audio conferencing](voice-case-study-audio-conferencing.md)












