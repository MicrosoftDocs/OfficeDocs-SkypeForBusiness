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

- **Public Switched Telephone Network (PSTN)** connectivity options - A choice between using Microsoft as your telephony carrier or connecting your own telephony carrier to Microsoft Teams.

- **Migrating your existing voice solution** - What you need to think about when migrating your existing voice solution to Teams.

> [!Important]
> This article focuses on voice solutions with Microsoft Teams.  While solutions with Skype for Business Online are still available, it's important to understand that Skype for Business Online will be retired on July 31, 2021 after which the service will no longer be accessible. In addition, PSTN connectivity between your on-premises environment whether through Skype for Business Server or Cloud Connector Edition and Skype for Business Online will no longer be supported. Learn how to connect your on-premises telephony network to Teams using Direct Routing.

, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).


## Phone System

Phone System is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 or Office 365 cloud with Microsoft Teams.

Phone System works with Teams or Skype for Business clients and certified devices. Phone System allows you to replace your existing PBX system with a set of features directly delivered from Microsoft or Office 365 and tightly integrated into the company’s cloud productivity experience. 

This article introduces several key features and functionality related to Phone System and the deployment decisions you will meed to consider. For more information, see the following articles:

- For information about all Phone System features and functionality, see [What is Phone System](what-is-phone-system-in-office-365.md) and [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md).

- For information about setting up Phone System, see [Set up Phone System in your organization](setting-up-your-phone-system.md).

- For information about managing supported devices, see [Manage your devices in Microsoft Teams](devices/device-management.md) and [Teams Marketplace] (https://www.microsoft.com/en-us/microsoft-365/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1)

The following features are discussed in greater detail:

- Auto attendants and call queues
- Voicemail
- Calling identity
- Dial plans and call routing
- Emergency calling
- Phone numbers from Microsoft



### Auto attendants and Call queues

Auto attendants allow you to set up menu options to route calls based on caller input.  Call queues are waiting areas for callers. Used together, auto attendants and call queues can easily route callers to the appropriate person or department in your organization.

For information about auto attendants and call queues, see the following articles:

- [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md).
- [Set up an auto attendant](create-a-phone-system-auto-attendant.md). 
- [Create a call queue](create-a-phone-system-call-queue.md) 


### Voicemail

Cloud Voicemail, powered by Azure Voicemail services, supports voicemail deposits to Exchange mailboxes only and doesn't support third-party email systems. For online only users, cloud voicemail is automatically set up and provisioned for users after they are assigned a Phone System license. For Phone System users with an Exchange mailbox, you will need to perform extra configuration steps. 

Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs might require that you disable voicemail transcription for specific users or everyone throughout the organization.

For information about Cloud Voicemail, see the following articles:

- [Set up Cloud Voicemail](set-up-phone-system-voicemail.md)
- [Set voicemail policies in your organization](set-up-phone-system-voicemail.md#setting-voicemail-policies-in-your-organization)



### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. For information about configuring caller ID or to change or block the caller ID, see  [Set the caller ID for a user](set-the-caller-id-for-a-user.md). 


### Dial plans

A dial plan in the Phone System feature of Microsoft 365 or Office 365 is a set of normalization rules that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing.

You will need to decide the following: 

- Does my organization need a customized dial plan?
- Which users require a customized dial plan, and which tenant dial plan should be assigned to each user?

For more information, see the following articles: 

- [What are dial plans?](what-are-dial-plans.md)
- [Plan for tenant dial plans](what-are-dial-plans.md#planning-for-tenant-dial-plans)
- [Create and manage dial plans](create-and-manage-dial-plans.md). 



### Phone numbers from Microsoft

Microsoft has two types of telephone numbers available: *subscriber* (user) numbers, which can be assigned to users in your organization, and *service* numbers, available as toll and toll-free service numbers, which have higher concurrent call capacity than subscriber numbers and can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues.

You will need to determine:

- Which user locations need new phone numbers from Microsoft?
- Which type of telephone number (subscriber or service) do I need? 
- How do I port existing phone numbers to Teams?

For more information about managing phone numbers in your organization, including getting new numbers or transferring exsiting numbers, see the following articles:

- [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) 
- [Getting phone numbers for your users](getting-phone-numbers-for-your-users.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Transfer phone numbers to Microsoft Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md)


### Devices

For more information about managing devices and supported devices, see the following:

- [Manage your devices in Microsoft Teams](devices/device-management.md)
- [IP Phones](https://docs.microsoft.com/skypeforbusiness/certification/devices-ip-phones?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json)
- [USB audio and video devices](https://docs.microsoft.com/skypeforbusiness/certification/devices-usb-devices?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json)
- [Intelligent communications for devices](https://products.office.com/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1)



## Public Switched Telephone Network (PSTN) connectivity options

To connect Phone System to the Public Switched Telephone Network (PSTN), you can choose Microsoft’s Calling Plan or your own telephony carrier. You can choose to connect to the Public Switched Telephone Network (PSTN) by:

- **Using Microsoft as your PSTN carrier** by signing up for Microsoft Calling Plan

- **Using your own PSTN carrier** by using Direct Routing to connect your own telephony carrier to Teams

### Calling Plan (Microsoft 365 or Office 365)

This option connects the Microsoft 365 or Office 365 Phone System to the Public Switched Telephone Network (PSTN) to enable calls to landlines and mobile phones around the world. With Calling Plan, Microsoft is your PSTN carrier.

For more information, see Calling Plans for Microsoft 365 or Office 365.


To connect Phone System to the Public Switched Telephone Network (PSTN) so that users can make phone calls around the world, you have options based on your business need.  Ask yourself the following:


|Ask yourself|Action |
| :------------|:-------|
| Do I want to use Microsoft Calling Plan as my telephony carrier? | For more information, see [Phone System with Calling Plans](calling-plan-landing-page.md).|
| Do I need to use my own telephony carrier? | For more information, see [Phone System with Direct Routing](direct-routing-landing-page.md).
|||


### Direct Routing

This option connects either Phone System in Microsoft 365 or Office 365 or Enterprise Voice system in Skype for Business on-premises to your telephony network. This option requires a supported Session Border Controller (SBC). In some cases, this option might require additional Microsoft software deployed on-premises.

## Considerations for migrating your voice solution to Teams













