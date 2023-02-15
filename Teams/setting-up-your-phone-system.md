---
title: "Set up Phone System in your organization"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.date: 02/27/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
  - highpri
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Phone System
  - seo-marvel-apr2020
  - intro-get-started
description: Step-by-step guide detailing how to set up Teams Phone System for your organization in Microsoft 365.
---

# Set up Phone System in your organization

This article provides a roadmap to content for setting up Phone System--Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud. 

To learn more about Phone System features and requirements, see [What is Phone System](what-is-phone-system-in-office-365.md) and [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md). 

To enable your users to make and receive external calls, you'll also need to connect Phone System to the Public Switched Telephone Network (PSTN). PSTN connectivity options are also introduced in this article.  

If you're still planning your voice solution, start by reading [Plan your voice solution](cloud-voice-landing-page.md), which helps you decide which Microsoft voice solution is right for your organization. 


This article describes the following steps:
 
- [Step 1: Buy and assign a Phone System license](#step-1-buy-and-assign-a-phone-system-license)
- [Step 2: Choose a PSTN connectivity option](#step-2-choose-a-pstn-connectivity-option)
- [Step 3: Set up emergency locations for emergency calling](#step-3-set-up-emergency-locations-for-emergency-calling)
- [Step 4: Get phone numbers for your users and services](#step-4-get-phone-numbers-for-your-users-and-services)
- [Step 5: If you want to set up a call queue](#step-5-if-you-want-to-set-up-a-call-queue)
- [Step 6: If you want to set up an auto attendant](#step-6-if-you-want-to-set-up-an-auto-attendant)
- [Step 7: Set up other Phone System features](#step-7-set-up-other-phone-system-features)
- [Step 8: Manage your deployment](#step-8-manage-your-deployment)


Links to more detailed information are available at the end of each step.

## Step 1: Buy and assign a Phone System license

For each user who uses Phone System, you must assign a Phone System license to that user.   

You can assign a license to a single user or you can assign licenses to multiple users in bulk. For more information about available Phone System licenses and how to acquire and assign licenses, see [Teams add-on licenses](/microsoftteams//teams-add-on-licensing/microsoft-teams-add-on-licensing) and [Assign Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses).

The Microsoft Teams Phone System with Calling Plan license bundle is Microsoft’s all-in-the-cloud solution. This option provides Private Branch Exchange (PBX) capabilities and external calls to the Public Switched Telephone Network (PSTN) with Microsoft as your carrier. If the Phone System with Calling Plan bundle is available in your location, you should consider this option. But if your PSTN calling requirements are more complex, Microsoft offers several PSTN connectivity options for making external calls.

## Step 2: Choose a PSTN connectivity option

Microsoft provides multiple options for making external calls to the PSTN, including:

- [Microsoft Calling Plan](calling-plans-for-office-365.md). An all-in-the-cloud solution with Microsoft as your PSTN carrier. If you choose Microsoft Calling Plan as your connectivity option, you have a choice of Calling Plan options, including Domestic, International, and Pay-as-you-go plans.

- [Operator Connect](operator-connect-plan.md). If your existing carrier participates in the Microsoft Operator Connect program, they can manage PSTN calling for you.

- [Teams Phone Mobile](operator-connect-mobile-plan.md). If your existing carrier participates in the Microsoft Teams Phone Mobile program, they can manage the service for using SIM-enabled mobile phone numbers with Teams.

- [Direct Routing](direct-routing-plan.md). This option lets you use your own PSTN carrier by connecting your SBCs to Phone System.

For more information about all connectivity options and which one is the best solution for your organization, see [PSTN connectivity options](pstn-connectivity.md) and [Voice and PSTN connectivity license options](/teams-add-on-licensing/microsoft-teams-add-on-licensing?branch=crowe-phone-system#voice-and-pstn-connectivity.md).


## Step 3: Set up emergency locations for emergency calling

An emergency location is used when someone in your organization calls emergency services such as fire, police, or ambulance. When a person calls an emergency service, the address that's configured as your organization's emergency address is sent to the service. 

How you set up emergency locations differs depending on the PSTN connectivity option you choose.  For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

Dynamic emergency calling provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client. Setting up dynamic emergency calling also requires you to configure your network settings and topology.  For more inforation, see [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md) and [Network settings for cloud voice features](cloud-voice-network-settings.md).

## Step 4: Get phone numbers for your users and services

Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them.

In addition to getting phone numbers for your users, you can acquire toll or toll-free phone numbers for services such as auto attendants and call queues. A service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously.

How you acquire and manage phone numbers differs depending on your PSTN connectivity option.

For information on how to manage phone numbers for your users and services, see the following articles. 

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md) – Provides an overview of phone number types (user and service) with links to specific articles for acquiring and managing numbers.

- [Assign, change, or remove a phone number for a user](assign-change-or-remove-a-phone-number-for-a-user.md) – Describes how to assign and manage the user phone numbers you've acquired.  

- [Manage resource accounts for service numbers](manage-resource-accounts.md) - Describes how to create resource accounts for auto attendants and call queues, and assign service numbers to those resource accounts.

- [How many telephone numbers can you get](how-many-phone-numbers-can-you-get.md) – Describes how many phone numbers you can get, depending on the types of telephone numbers and types of licenses you've bought and assigned.


## Step 5: If you want to set up a call queue

Call queues include greetings that are used when someone calls in to a phone number for your organization, the ability to automatically put the calls on hold, and the ability to search for the next available call agent to handle the call. You can create single or multiple call queues for your organization.

For more information about call queues, see [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and [Create a call queue](create-a-phone-system-call-queue.md).

## Step 6: If you want to set up an auto attendant

Auto attendants let people who call in to your organization navigate a menu system to get them to the right department, call queue, person, or operator.

For information about setting up auto attendants, see [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and [Set up an auto attendant](create-a-phone-system-auto-attendant.md).

## Step 7: Set up other Phone System features

There are numerous Phone System features, which are summarized in [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md). Some of these features require configuration, others do not.  In addition to cloud queues and auto attendants, some of the more common features you might want to configure include:

- [Cloud voicemail](set-up-phone-system-voicemail.md)
- [Caller ID](caller-id-policies.md)
- [Call forwarding and delegation](user-call-settings.md)

Calling policies control which calling and call forwarding features are available to your users. For more information, see [Calling policies](teams-calling-policy.md).

## Step 8: Manage your deployment

A successful Phone System deployment also involves managing your devices and monitoring call quality and performance. For more information, see:

- [Manage devices](/devices/device-management.md)
- [Manage and monitor call quality](monitor-call-quality-qos.md)


## Related articles

- [What is Phone System](what-is-phone-system-in-office-365.md)

- [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)
