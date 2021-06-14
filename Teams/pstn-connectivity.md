---
title: PSTN connecivity options in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/29/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
ms.reviewer: crowe
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.cloudvoice
  - seo-marvel-apr2020
  - seo-marvel-may2020
search.appverid: MET150
description: Learn more about the Microsoft Teams PSTN connectivity options and the decisions that you will make for your organization.
appliesto: 
  - Microsoft Teams
---


# PSTN connectivity options

Microsoft provides complete PBX capabilities for your organization through Phone System. However, to enable users to make calls outside your organization, you need to connect Phone System to the Public Switched Telephone Network (PSTN).

For information about Microsoft voice solutions, incuding details about Phone System features and which PSTN connectivity option is right for your organization, see [Plan your Teams voice solution](cloud-voice-landing-page.md).

This article focuses on the differences in the PSTN configuration options and how it affects configuration of features such as phone number management and emergency calling.  



To connect Phone System to the PSTN, you can choose one of the following options:

- **Phone System with Calling Plan**. An all-in-the-cloud solution with Microsoft as your PSTN carrier. This is the simplest option that connects Microsoft Phone System to the Public Switched Telephone Network (PSTN).

- **Phone System with your own PSTN carrier by using Direct Routing**(#phone-system-with-own-pstn-carrier-with-direct-routing) to connect your on-premises environment to Teams. With this option, you connect your own supported SBC to Microsoft Phone System and you can use virtually any telephony carrier with Phone System.  For more information, see [Phone System Direct Routing](direct-routing-landing-page.md)

- **Phone System with your own PSTN carrier by using Operator Connect**, which is currently available only in **public preview.**  With Operator Connect, if your existing operator is a participant in the Microsoft Operator Connect program, they can manage the service for bringing PSTN calling to Teams. For more information about Operator Connect, and for a list of operators participating in this program, see [Plan Operator Connect](operator-connect-plan.md).

You can also choose a combination of options, which enables you to design a solution for a complex environment, or manage a multi-step migration (more about migration later).



## Phone number management




## Emergency calling

How you configure emergency calling differs depending on your PSTN connectivity option: Microsoft Calling Plan or Direct Routing. Dynamic emergency calling for Microsoft Calling Plan and Phone System Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client. For more information about emergency calling concepts and terminology, and how to configure dynamic emergency calling, see the following articles:

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [Contoso case study: Emergency calling](voice-case-study-emergency-calling.md)<br>
  Describes how a fictional multi-national corporation, Contoso, implemented emergency calling for their organization.

## Location-Based Routing for Direct Routing

In some countries and regions, it's illegal to bypass the Public Switched Telephone Network (PSTN) provider to decrease long-distance calling costs. Location-Based Routing for Direct Routing enables you to restrict toll bypass for Microsoft Teams users based on their geographic location. For more information about how to plan and configure Location-Based Routing (LBR), see the following articles:

- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
- [Contoso case study: Location-Based Routing](voice-case-study-location-based-routing.md)<br>
  Describes how a fictional multi-national corporation, Contoso, implemented Location-Based Routing for their organization.

## Network topology for voice features

If you are deploying dynamic emergency calling or Location-Based Routing for Direct Routing, you must configure network settings for use with these features in Microsoft Teams. To learn how to configure network settings for network regions, network sites, network subnets, and trusted IP addresses, see the following articles:

- [Network settings for cloud voice features in Microsoft Teams - Concepts and terminology](cloud-voice-network-settings.md)
- [Manage your network topology for cloud voice features in Microsoft Teams](manage-your-network-topology.md)


