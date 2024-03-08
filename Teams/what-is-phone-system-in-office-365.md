---
title: "What is Teams Phone"
ms.reviewer: roykuntz
ms.date: 03/07/2024
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-apr2020
  - intro-overview
description: "In this article, you'll learn about Microsoft Teams Phone System technology in Microsoft 365."
---

# What is Teams Phone

This article is for administrators and IT professionals who are evaluating Microsoft Teams Phone--Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud.

Teams Phone works with Teams clients and certified devices. Teams Phone allows you to replace your existing PBX system with a set of features directly delivered from Microsoft 365.

Calls between users in your organization are handled internally within Teams Phone, and never go to the Public Switched Telephone Network (PSTN)--thereby removing long-distance costs on internal calls. 

For making external calls, Teams Phone provides add-on options for connecting to the PSTN. For more information about voice solutions and PSTN connectivity options, see [Plan your Teams voice solution](cloud-voice-landing-page.md) and [Connect to the PSTN](#connect-to-the-public-switched-telephone-network-pstn). 

**Licenses and voice enablement** - To use Teams Phone features, your organization must have a Teams Phone license. For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

Most features require you to assign the Teams Phone license and ensure that users are "voice enabled." To assign the license, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment) and set the **EnterpriseVoiceEnabled** parameter to $true. A few features, such as Auto attendant, do not require a user to be voice enabled (more about features in the next section).

## Teams Phone features

With Teams Phone, users in your organization can use Teams to place and receive calls, transfer calls, and mute or unmute calls. Teams Phone users can click a name in their address book, and place Teams calls to that person. To place and receive calls, Teams Phone users can use their mobile devices, a headset with a laptop or PC, or one of many IP phones that work with Teams. 

For more information about Teams Phone features, including which features require a user to be voice enabled, see [Teams Phone features](here-s-what-you-get-with-phone-system.md).

You can manage calling options and settings by using the Teams admin center and by using PowerShell.

## Connect to the Public Switched Telephone Network (PSTN)
  
For external calling, Teams Phone can be connected to the PSTN in one of several ways:
  
- Purchase a Microsoft Calling Plan (domestic or domestic and international). Microsoft Calling Plan is an all-in-the-cloud solution with Microsoft as your PSTN carrier. For more information, see [Teams Phone and Calling Plans](calling-plan-landing-page.md).

- Use your existing telephony infrastructure for on-premises PSTN connectivity.

  You can connect your on-premises telephony infrastructure to Teams Phone by using Operator Connect or Direct Routing. 

For more information about all PSTN Connectivity options, see [PSTN connectivity options](pstn-connectivity.md).


## Teams Phone with services

Teams Phone can be used for services and voicemail, such as:

- **Auto attendants** -  Auto attendants can be used to create a menu system for your organization that lets external and internal callers move through the system to locate and place or transfer calls to company users or departments in your organization. See [What are Cloud auto attendants?](what-are-phone-system-auto-attendants.md).

- **Call queues** -  Call queue greetings can be used when someone calls in to a phone number for your organization. These greetings include the ability to automatically put the calls on hold and to search for the next available call agent to handle the call. The people on hold can also listen to music while on hold. You can create single or multiple call queues for your organization. See [Create a Cloud call queue](create-a-phone-system-call-queue.md).

- **Voicemail** - Cloud Voicemail is automatically set up and provisioned for all Teams users. See [Set up Cloud Voicemail](set-up-phone-system-voicemail.md).

For more information about features, see [Here's what you get with Teams Phone](here-s-what-you-get-with-phone-system.md). If you're ready to get started, see [Set up Teams Phone in your organization](setting-up-your-phone-system.md).

## Related topics

- [Teams Phone features](here-s-what-you-get-with-phone-system.md)
- [Set up Teams Phone](setting-up-your-phone-system.md)
- [Plan your Teams voice solution](cloud-voice-landing-page.md)
- [PSTN connectivity options](pstn-connectivity.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
