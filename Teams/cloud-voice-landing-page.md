---
title: Plan your voice solution in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 08/03/2023
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
  - highpri
  - Tier1
ms.reviewer: crowe
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboararticleautod.helparticle.cloudvoice
  - seo-marvel-apr2020
  - seo-marvel-may2020
search.appverid: MET150
description: Learn more about the Microsoft Teams cloud voice features and the deployment decisions that you'll make for your organization.
appliesto: 
  - Microsoft Teams
---

# Plan your Teams voice solution

This article helps you decide which Microsoft voice solution is right for your organization. After you've decided, the article provides a roadmap to content that will enable you to implement your chosen solution.

You might want the simplest solution&mdash;Microsoft Teams Phone with Calling Plan. This option is Microsoft's all-in-the-cloud solution that provides Private Branch Exchange (PBX) functionality and calls to the Public Switched Telephone Network (PSTN), as shown in the following diagram. With this solution, Microsoft is your PSTN carrier.

![Diagram 1 shows Teams Phone with Calling Plan.](media/voice-solutions-simple.png)

If you answer yes to the following, then Teams Phone with Calling Plan is the right solution for you:

- Calling Plan is available in your region.
- You don't need to retain your current PSTN carrier.
- You want to use Microsoft-managed access to the PSTN.

If you’re a small to medium business (300 or fewer people), Microsoft now bundles Teams Phone with a Domestic Calling Plan. 

However, your situation might be more complex. For example, you might have offices in locations where Calling Plan isn't available. Or you might need a combination solution that supports a complex, multi-national deployment, with different requirements for different geographic locations. Microsoft supports a combination of solutions:

- Teams Phone with Calling Plan
- Teams Phone with your own PSTN carrier with Operator Connect
- Teams Phone with your own PSTN mobile carrier with Teams Phone Mobile 
- Teams Phone  with your own PSTN carrier with Direct Routing
- A combination solution that uses Teams Phone with Calling Plan, Teams Phone with Operator Connect, and/or Teams Phone with Direct Routing

For a visual summary of all the voice solution options, see the voice solutions poster.

[![Microsoft Voice Solutions poster.](media/microsoft-voice-solutions-thumb.png)](https://download.microsoft.com/download/4/3/5/435cd4e9-ca56-4fd1-acb6-d1fda7952320/microsoft-voice-solutions.pdf) <br> [PDF](https://download.microsoft.com/download/4/3/5/435cd4e9-ca56-4fd1-acb6-d1fda7952320/microsoft-voice-solutions.pdf) <br>[Visio](https://download.microsoft.com/download/7/5/c/75c13012-e20c-48bd-a6dd-ea49d1a3420d/microsoft-voice-solutions.vsdx) 
<br>

If you're interested in PSTN conferencing for meetings, you'll want to read about Microsoft's Audio Conferencing service and licensing requirements. Note that Audio Conferencing does not require a Teams Phone license. For more information, see [Audio Conferencing](audio-conferencing-in-office-365.md).

## What do you need to read?

**Required for all.** Some of the sections in this article pertain to all organizations. For example, everyone should read about Teams Phone and understand the options for connecting to the Public Switched Telephone Network (PSTN).

| Required for all | Description |
| :------------|:-------|
| [**Teams Phone**](#teams-phone) | Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud with Microsoft Teams. |
| [**Public Switched Telephone Network (PSTN) connectivity options**](#public-switched-telephone-network-connectivity-options) | Choose Microsoft as your telephony carrier or connect your own telephony carrier to Microsoft Teams by using Operator Connect or Direct Routing. Combined with Teams Phone, PSTN connectivity options enable your users to make phone calls all over the world.|

**Depending on your requirements.** Some of the sections in this and related articles are pertinent depending on your existing deployment and requirements. For example, Location-Based Routing is only required for Direct Routing customers in geographic locations that do not allow toll bypass.

Consider which of these other configurations you might need:

![Diagram 2 shows other voice components, such as Phone numbers from Microsoft, Dial plans and call routing, and so on.](media/voice-consider-additional-components.png)

| Depending on your requirements | Description |
| :------------|:-------|
| [**Phone number management**](pstn-connectivity.md#phone-number-management) | How to get and manage phone numbers differs depending on your PSTN connectivity option. Read this section if you need to obtain phone numbers, transfer existing numbers, obtain service numbers, and so on. |
| [**Call routing and dial plans**](pstn-connectivity.md#call-routing-and-dial-plans) | How to configure and manage dial plans that translate dialed phone numbers into an alternate format (typically E.164 format) for call authorization and call routing. Read this section if you need to understand what dial plans are and whether you need to specify dial plans for your organization.|
| [**Emergency calling**](pstn-connectivity.md#emergency-calling) | How to manage and configure emergency calling differs depending on your PSTN connectivity option. Read this section if you need to understand how to manage emergency calling for your organization. |
| [**Location-Based Routing for Direct Routing**](pstn-connectivity.md#location-based-routing-for-direct-routing) |How to use Location-Based Routing (LBR) to restrict toll bypass for Microsoft Teams users based on their geographic location. Read this section if your organization is using Direct Routing at a location that doesn't allow toll bypass.
| [**Network topology for cloud voice features**](pstn-connectivity.md#network-topology-for-voice-features) | If your organization is deploying Location-Based Routing (LBR) for Direct Routing or dynamic emergency calling, you must configure network settings for these features in Microsoft Teams. Read this section if you're implementing LBR for Direct Routing, or if you're implementing dynamic emergency calling with Calling Plan or Direct Routing. |
| [**Migrate your existing voice solution**](#migrate-your-existing-voice-solution-to-teams) | What you need to think about when migrating your voice solution to Teams.  Read this section if you're migrating from an existing voice solution to Teams. 


## Teams Phone

Teams Phone is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud with Microsoft Teams.

Teams Phone works with Teams clients and certified devices. Teams Phone allows you to replace your existing PBX system with a set of features directly delivered from Microsoft 365. 

Calls between users in your organization--regardless of geographical area--are handled internally within Teams Phone. These internal calls never go to the Public Switched Telephone Network (PSTN), so your company avoids long-distance charges.

This article introduces the following Teams Phone key features and functionality, and the deployment decisions you'll need to consider:

- [Auto attendants and Call queues](#auto-attendants-and-call-queues)
- [Cloud Voicemail](#cloud-voicemail)
- [Calling identity](#calling-identity)

![Diagram 3 shows Teams Phone contains Auto attendants and call queries, Cloud voicemail, and Calling identity.](media/phone-system-contains.png)

For information about all Teams Phone features, and how to set up Teams Phone, see the following articles:

- [Teams Phone features](here-s-what-you-get-with-phone-system.md)
- [Set up Teams Phone in your organization](setting-up-your-phone-system.md)<br>
  Describes how to buy and assign Teams Phone licenses, manage phone numbers, and set up communication credits for toll-free numbers. 

For information about managing supported devices, see [Manage your devices in Microsoft Teams](devices/device-management.md) and [Teams Marketplace](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).

### Auto attendants and Call queues

Auto attendants allow you to set up menu options to route calls based on caller input. Call queues are waiting areas for callers. Used together, Auto attendants and Call queues can easily route callers to the appropriate person or department in your organization.

For information about Auto attendants and Call queues, see the following articles:

- [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)
- [Set up an Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue](create-a-phone-system-call-queue.md) 
- [Contoso case study: Auto attendants and Call queues](voice-case-study-call-queues.md)<br>
  Describes how a fictional multi-national corporation, Contoso, implemented Auto attendants and Call queues for their voice solution.

### Cloud Voicemail

Cloud Voicemail, powered by Azure Voicemail services, supports voicemail deposits to Exchange mailboxes only. It doesn't support third-party email systems. 

Cloud Voicemail includes voicemail transcription, which is enabled for all users in your organization by default. Your business needs might require that you disable voicemail transcription for specific users or everyone throughout the organization.

Cloud Voicemail is automatically set up and provisioned for Teams users.  

For more information about Cloud Voicemail and its configuration, see the following articles:

- [Set up Cloud Voicemail](set-up-phone-system-voicemail.md)
- [Manage voicemail policies](manage-voicemail-policies.md)

### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. For information about configuring caller ID or to change or block the caller ID, see [Manage caller ID policies for users](caller-id-policies.md). 

## Public Switched Telephone Network connectivity options

Teams Phone provides complete PBX capabilities for your organization. However, to enable users to make calls outside your organization, you need to connect Teams Phone to the Public Switched Telephone Network (PSTN). To connect Teams Phone to the PSTN, you can choose one of the following options:

- [**Teams Phone with Calling Plan**](pstn-connectivity.md#teams-phone-with-calling-plan). An all-in-the-cloud solution with Microsoft as your PSTN carrier.

- [**Teams Phone with your own PSTN carrier by using Operator Connect**](operator-connect-plan.md). With Operator Connect, if your existing operator participates in the Microsoft Operator Connect program, they can manage the service for bringing PSTN calling to Teams. 

- [**Teams Phone with your own PSTN mobile carrier by using Teams Phone Mobile**](operator-connect-mobile-plan.md). With Teams Phone Mobile, if your existing operator participates in the Microsoft Teams Phone Mobile program, they can manage the service for using SIM-enabled mobile phone numbers with Teams. 

- [**Teams Phone with your own PSTN carrier by using Direct Routing**](pstn-connectivity.md#teams-phone-with-direct-routing) to connect your on-premises environment to Teams.

You can choose a combination of options, which enables you to design a solution for a complex environment, or manage a multi-step migration. You'll read more about migration later.

Most Teams Phone features are the same regardless of the PSTN connectivity option you choose. There are some differences in functionality, however, that affect how you configure certain Teams Phone features, such as call routing and emergency calling. For more information about PSTN connectivity options and configuration considerations, see [PSTN connectivity options](pstn-connectivity.md).

## Migrate your existing voice solution to Teams

For an organization that is upgrading to Teams, the ultimate goal is to move all users to TeamsOnly mode. Using Teams Phone is only supported when the user is in TeamsOnly mode. If you need basic information about upgrading to Teams, start here:

- [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md)
- [About the upgrade framework](upgrade-framework.md)
- [Upgrade strategies for IT administrators](upgrade-to-teams-on-prem-implement.md)

For guidance on planning a Teams voice solution as part as your overall plan to upgrade to Teams, see [PSTN considerations for upgrading to Teams from Skype for Business on-premises](upgrade-to-teams-on-prem-pstn-considerations.md).

For more information about how to implement your voice migration, see the [Contoso voice migration case study](voice-case-study-overview.md). The case study describes how a fictional multi-national corporation, Contoso, implemented a Teams voice solution for their organization. 

 
