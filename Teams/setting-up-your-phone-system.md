---
title: "Set up Phone System in your organization"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
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

This article provides a roadmap to content for setting up Phone System--Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Microsoft 365 cloud. Links to more detailed information are available at the end of each step.

Before reading this article, make sure you've read [What is Phone System](what-is-phone-system-in-office-365.md) and [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md). The latter two articles describe Phone System requirements and features.

This article describes the following steps:

- [Step 1: Buy and assign a Phone System license](#step-1-buy-and-assign-a-phone-system-license)
- [Step 2: Choose a PSTN connectivity option](#step-2-choose-a-pstn-connectivity-option)
- [Step 3: Get phone numbers for your users](#step-3-get-phone-numbers-for-your-users)
- [Step 4: Get phone numbers for services](#step-4-get-phone-numbers-for-services-call-queues-auto-attendants)
- [Step 5: If you want to set up a call queue](#step-5-if-you-want-to-set-up-a-call-queue)
- [Step 6: If you want to set up an auto attendant](#step-6-if-you-want-to-set-up-an-auto-attendant)
- [Step 7: Set up communication credits for toll-free numbers](#step-7-set-up-communications-credits-for-toll-free-numbers)

## Step 1: Buy and assign a Phone System license

To assign a Phone System license to a single user, the steps are the same as assigning a Microsoft 365 license. You can also assign licenses to multiple users in bulk. For more information about available Phone System licenses and how to acquire and assign licenses, see [Teams add-on licenses](/microsoftteams//teams-add-on-licensing/microsoft-teams-add-on-licensing) and [Assign Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses).

## Step 2. Choose a PSTN connectivity option

To enable your users to make and receive external calls, you'll need to connect Phone System to the Public Switched Telephone Network (PSTN). Microsoft provides multiple options for connecting to the PSTN, including:

- Calling Plan. An all-in-the-cloud solution with Microsoft as your PSTN carrier.

- Operator Connect. If your existing carrier participates in the Microsoft Operator Connect program, they can manage PSTN calling and Session Border Controllers (SBCs) for you.

- Direct Routing. Use your own PSTN carrier by connecting your SBCs to Phone System.

For more information about all connectivity options, see [PSTN connectivity options](pstn-connectivity.md).

## Step 3: Get phone numbers for your users

Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them.

For information on how to manage phone numbers for your users, see the following articles. How you manage numbers for a user depends on the PSTN connectivity option you choose.

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md) – Provides an overview of phone number types with links to specific articles for acquiring and managing numbers depending on your PSTN connectivity option.
Describes the two types of [user phone numbers](manage-phone-numbers-landing-page.md#user-telephone-numbers).

- [Assign, change, or remove a phone number for a user](assign-change-or-remove-a-phone-number-for-a-user.md) – Describes how to assign and manage the phone numbers you've acquired.

- [How many telephone numbers can you get](how-many-phone-numbers-can-you-get.md) – Describes how many phone numbers you can get, depending on the types of telephone numbers and types of licenses you've bought and assigned.

## Step 4: Get phone numbers for services (call queues, auto attendants)

In addition to getting phone numbers for your users, you can acquire toll or toll-free phone numbers for services such as auto attendants and call queues. A service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously.

You can obtain service numbers from Microsoft that are included in your licensing. If you have PSTN connectivity through Operator Connect or Direct Routing, you can use service numbers provided by your own carrier or operator.

For more information, see:

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md) – Provides an overview of phone number types with links to specific articles for acquiring and managing numbers depending on your PSTN connectivity option.
Describes [service phone numbers](manage-phone-numbers-landing-page.md#service-telephone-numbers) available from Microsoft that are included in your licensing. For information about service numbers provided by Operator Connect or Direct Routing, contact your provider.

- [How many telephone numbers can you get](how-many-phone-numbers-can-you-get.md) – Describes how many phone numbers you can get, depending on the types of telephone numbers and types of licenses you've bought and assigned.

## Step 5: If you want to set up a call queue

Call queues include greetings that are used when someone calls in to a phone number for your organization, the ability to automatically put the calls on hold, and the ability to search for the next available call agent to handle the call. You can create single or multiple call queues for your organization.

For more information about call queues, see [Create a call queue](create-a-phone-system-call-queue.md).

## Step 6: If you want to set up an auto attendant

Auto attendants let people who call in to your organization navigate a menu system to get them to the right department, call queue, person, or operator.

For information about setting up auto attendants, see [Set up an auto attendant](create-a-phone-system-auto-attendant.md).

## Step 7: Set up Communications Credits for toll-free numbers

If you'd like to use toll-free numbers with Microsoft Teams, you'll need to set up Communications Credits. Toll-free calls are billed per minute and require a positive Communications Credits balance.

Communications Credits are a convenient way to add toll-free numbers to use as follows:

- With service numbers for voice apps, such as auto attendants or call queues.

- To dial any international phone number when you have Domestic Calling Plan subscriptions or beyond what is included in a Domestic and International Calling Plan subscription.

- To dial out and pay per minute once you've exhausted your monthly minute allotment.

- To dial out and pay per minute for all outgoing calls, if you have a Pay-As-You-Go Calling Plan.

For more information, see [What are Communications Credits?](what-are-communications-credits.md) and [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

## Related articles

- [What is Phone System](what-is-phone-system-in-office-365.md)

- [Here's what you get with Phone System](here-s-what-you-get-with-phone-system.md)

- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)
