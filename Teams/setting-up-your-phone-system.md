---
title: "Set up Teams Phone in your organization"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 03/07/2024
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
  - Tier1
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Phone System
  - intro-get-started
description: Learn how to set up Microsoft Teams Phone for your organization in Microsoft 365.
---

# Set up Teams Phone in your organization

This article provides a roadmap to content for setting up Microsoft Teams Phone--Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud. This article is for administrators and IT professionals.

If you're still planning your voice solution, start by reading [Plan your voice solution](cloud-voice-landing-page.md), which helps you decide which Microsoft voice solution is right for your organization.

**License and voice enablement** - To use Teams Phone features, your organization must have a Teams Phone license. For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

Most features require you to assign the Teams Phone license, and ensure that users are "voice enabled." To assign the license, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment) and set the **EnterpriseVoiceEnabled** parameter to $true. A few features, such as Auto attendant, do not require a user to be voice enabled. 

To learn more about Teams Phone features and requirements, including which features require a user to be voice enabled, see [What is Teams Phone](what-is-phone-system-in-office-365.md) and [Teams Phone features](here-s-what-you-get-with-phone-system.md).

**PSTN connectivity** - To enable your users to make and receive external calls, you'll need to connect Teams Phone to the Public Switched Telephone Network (PSTN). PSTN connectivity options are also introduced in this article.  

**Overview of steps** - This article introduces the following steps. Each step contains links to more detailed information.
 
- [Step 1: Buy and assign a Teams Phone license](#step-1-buy-and-assign-a-teams-phone-license)
- [Step 2: Choose a PSTN connectivity option](#step-2-choose-a-pstn-connectivity-option)
- [Step 3: Get and assign phone numbers for your users and services](#step-3-get-and-assign-phone-numbers-for-your-users-and-services)
- [Step 4: Set up emergency calling](#step-4-set-up-emergency-calling)
- [Step 5: If you want to set up an auto attendant](#step-5-if-you-want-to-set-up-an-auto-attendant)
- [Step 6: If you want to set up a call queue](#step-6-if-you-want-to-set-up-a-call-queue)
- [Step 7: Set up other Teams Phone features](#step-7-set-up-other-teams-phone-features)
- [Step 8: Manage your deployment](#step-8-manage-your-deployment)

> [!NOTE]
> Be aware that some steps will differ depending on the PSTN connectivity option you choose. For example, the steps and sequence for phone number management and emergency calling management might differ. These differences are described in detail in the associated articles.

## Step 1: Buy and assign a Teams Phone license

For each user who uses Teams Phone, you must assign a Teams Phone license to that user.

Don't assign the **Microsoft Teams Phone Resource Account** license to any user other than resource accounts.

You can assign a license to a single user or you can assign licenses to multiple users in bulk. For more information about available Teams Phone licenses and how to acquire and assign licenses, see [Teams add-on licenses](/microsoftteams//teams-add-on-licensing/microsoft-teams-add-on-licensing) and [Assign Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses).

The Teams Phone with Calling Plan license bundle is Microsoft’s all-in-the-cloud solution. This option provides Private Branch Exchange (PBX) capabilities and external calls to the Public Switched Telephone Network (PSTN) with Microsoft as your carrier. If the Teams Phone with Calling Plan bundle is available in your location, you should consider this option. But if your PSTN calling requirements are more complex, Microsoft offers several PSTN connectivity options for making external calls.

## Step 2: Choose a PSTN connectivity option

Microsoft options for making external calls to the PSTN include:

- [Microsoft Calling Plan](calling-plans-for-office-365.md). An all-in-the-cloud solution with Microsoft as your PSTN carrier. If you choose Microsoft Calling Plan as your connectivity option, you have a choice of Calling Plan options, including Domestic, International, and Pay-as-you-go plans.

- [Operator Connect](operator-connect-plan.md). If your existing carrier participates in the Microsoft Operator Connect program, they can manage PSTN calling for you.

- [Teams Phone Mobile](operator-connect-mobile-plan.md). If your existing carrier participates in the Microsoft Teams Phone Mobile program, they can manage the service for using SIM-enabled mobile phone numbers with Teams.

- [Direct Routing](direct-routing-plan.md). This option lets you use your own PSTN carrier by connecting your SBCs to Teams Phone.

For more information about all connectivity options and which one is the best solution for your organization, see [PSTN connectivity options](pstn-connectivity.md) and [Voice and PSTN connectivity license options](/microsoftteams//teams-add-on-licensing/microsoft-teams-add-on-licensing#voice-and-pstn-connectivity).


## Step 3: Get and assign phone numbers for your users and services

Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them.

In addition to getting phone numbers for your users, you can acquire toll or toll-free phone numbers for services such as auto attendants and call queues. A service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously.

How you acquire and manage phone numbers differs depending on your PSTN connectivity option.

For information on how to manage phone numbers for your users and services, see the following articles. 

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md) – Provides an overview of phone number types (user and service) with links to specific articles for acquiring and managing numbers.

- [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md) – Describes how to assign and manage the user phone numbers you've acquired.  

- [Manage resource accounts for service numbers](manage-resource-accounts.md) - Describes how to create resource accounts for auto attendants and call queues, and assign service numbers to those resource accounts.

- [How many telephone numbers can you get](how-many-phone-numbers-can-you-get.md) – Describes how many phone numbers you can get, depending on the types of telephone numbers and types of licenses you've bought and assigned.

## Step 4: Set up emergency calling

To set up emergency calling, you--or your PSTN carrier--must define emergency locations and ensure that emergency locations are assigned to each user.  

An emergency location is used when someone in your organization calls emergency services such as fire, police, or ambulance. When a person calls an emergency service, the address that's configured as your organization's emergency address is sent to the service. 

How you set up emergency locations and assign these locations to users differs depending on the PSTN connectivity option you choose. For some options, your carrier assumes much of the responsibility for setting up emergency calling.  For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

Dynamic emergency calling provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client. Setting up dynamic emergency calling also requires you to configure your network settings and topology. For more information, see [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md) and [Network settings for cloud voice features](cloud-voice-network-settings.md).

For information about assigning emergency locations to users, see [Assign an emergency location](assign-change-emergency-location-user.md).

## Step 5: If you want to set up an auto attendant

Auto attendants let people who call in to your organization navigate a menu system to get them to the right department, call queue, person, or operator.

For information about setting up auto attendants, see [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and [Set up an auto attendant](create-a-phone-system-auto-attendant.md).

## Step 6: If you want to set up a call queue

Call queues include greetings that are used when someone calls in to a phone number for your organization, the ability to automatically put the calls on hold, and the ability to search for the next available call agent to handle the call. You can create single or multiple call queues for your organization.

For more information about call queues, see [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and [Create a call queue](create-a-phone-system-call-queue.md).


## Step 7: Set up other Teams Phone features

There are numerous Teams Phone features, which are summarized in [Teams Phone features](here-s-what-you-get-with-phone-system.md). Some of these features require configuration, others do not. In addition to auto attendants and call queues, some of the more common features you might want to configure include:

- [Cloud voicemail](set-up-phone-system-voicemail.md)
- [Caller ID](caller-id-policies.md)
- [Call forwarding and delegation](user-call-settings.md)

Calling policies control which calling and call forwarding features are available to your users. For more information, see [Calling policies](teams-calling-policy.md).

## Step 8: Manage your deployment

A successful Teams Phone deployment also involves managing your devices and monitoring call quality and performance. For more information, see:

- [Manage devices](./devices/device-management.md)
- [Manage and monitor call quality](monitor-call-quality-qos.md)


## Related articles

- [What is Teams Phone](what-is-phone-system-in-office-365.md)

- [Teams Phone features](here-s-what-you-get-with-phone-system.md)

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
