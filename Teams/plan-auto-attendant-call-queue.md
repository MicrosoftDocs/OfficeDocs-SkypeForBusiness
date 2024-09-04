---
title: Plan for Teams Auto attendants and Call queues
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 01/31/2024
ms.topic: article
ms.assetid: ab9f05a2-22cb-4692-a585-27f82d1b37c7
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.autoattendants.overview
  - Phone System
  - seo-marvel-apr2020
description: Learn about Auto attendants and Call queues, and how to use them to help callers move through a menu system to reach people or departments in your organization.
---

# Plan for Teams Auto attendants and Call queues

Auto attendants allow you to set up menu options to route calls based on caller input. Menu options for an Auto attendant--such as "For Sales, press 1--For Services press 2"--let an organization provide a series of choices that guide callers to their destination quickly, without relying on a human operator to handle incoming calls.

Call queues are waiting areas for callers. For situations where callers need to reach someone with a particular specialty--such as sales or service--rather than a specific person, you can use Call queues to connect callers to the group of agents who can assist them. Callers are put on hold until an agent assigned to the queue is available to take their call.

Used together, Auto attendants and Call queues can easily route callers to the appropriate person or department in your organization.

## Auto attendants

The primary purpose of an Auto attendant is to direct a caller to an appropriate person or department based on the caller's input to the provided menu options. Callers can be directed to:

- Specific people within your organization.
- Call queues where they wait to talk to the next available agent.
- External phone numbers.
- Other Auto attendants.
- Voicemail.

Different call routing options can be specified for business hours, off hours, and holidays.

Menu prompts can be created by using text-to-speech (system-generated prompts) or by uploading a recorded audio file. Speech recognition accepts voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.

Each Auto attendant has a specific language and time zone. If you do business in multiple languages or multiple parts of the world, you can create as many different Auto attendants as you need to accommodate your callers.

For each Auto attendant, you can configure an operator. While you can configure operator calls to go to various destinations, the operator feature is designed to allow callers to talk to a specific person in your organization who can help them.

Auto attendants can be configured to allow callers to search your organization's directory, either by name or by extension number. Within an Auto attendant, you can specify who is available for the directory search by choosing groups of users to include or exclude. (This is known as *dial scope*.)

Internal callers, using their Teams client, can reach an Auto attendant by calling the Resource account assigned to the Auto attendant.  External callers can reach an Auto attendant by dialing the phone number assigned to the Resource account or via the web if click-to-call is configured.

## Call queues

A Call queue is analogous to a waiting room in a physical building. Callers wait on hold while calls are routed to the agents in the queue. Call queues are commonly used for sales and service functions. However, Call queues can be used for any situation where the number of calls exceeds your internal capacity, such as a receptionist in a busy facility.

Call queue exception handling allows you to redirect calls in cases where there are no agents logged in and where the total number of callers or wait time exceeds limits that you specify. Calls can be routed to specific people, voicemail, other Call queues, or Auto attendants.

Like Auto attendants, Call queues each have a language setting. You can use different Call queues if you do business in multiple languages. Agents can be members of more than one queue if they're multi-lingual.

For each Call queue, you can specify if agents in the queue can opt out of taking calls and if calls should be routed to them based on their presence indication in Teams.

Internal callers, using their Teams client, can reach a Call queue by calling the Resource account assigned to the Call queue.  External callers can reach a Call queue by dialing the phone number assigned to the Resource account or via the web if click-to-call is configured.

Call queues don't provide separate call routing for off hours and holidays. Even if your Call queue is staffed 24/7 we recommend using an Auto attendant to direct calls to the call queue.

## Prerequisites

To configure Auto attendants and Call queues, you need the following resources:

- A [Resource Account](manage-resource-accounts.md) for each Auto attendant and each Call queue.
- A free [Microsoft Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md) for each resource account.
- External phone calls:
  - At least one [Microsoft service number](getting-service-phone-numbers.md), [Operator Connect number](operator-connect-plan.md), [Direct Routing number](direct-routing-plan.md), or a hybrid number for each resource account that you want to be directly dialable from external phone numbers.
    - The service number may be a toll or toll-free number.
- Web click-to-call:
  - [Contact centers with Azure Communication Services](/azure/communication-services/tutorials/contact-center)
  - [Quickstart: Join your calling app to a Teams auto attendant](/azure/communication-services/quickstarts/voice-video-calling/get-started-teams-auto-attendant)
  - [Quickstart: Join your calling app to a Teams call queue](/azure/communication-services/quickstarts/voice-video-calling/get-started-teams-call-queue)

> [!NOTE]
> Resource accounts are disabled for sign in and must remain so. Chat and presence are not available for these accounts.
>
> A **User Administrator** or higher role is required to create and license Resource Accounts. For more information, see [Using Microsoft Teams administrator roles to manage Teams](using-admin-roles.md).

Agents who receive calls from a Call queue must be Enterprise Voice enabled online or on-premises users. For more information, see [Assign, change, or remove a phone number for a user](/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user) and [Enable users for Direct Routing](/microsoftteams/direct-routing-enable-users). In addition, if the Call queue is using Direct Routing or Operator Connect numbers, agents who need to conference or transfer calls also require:

- An [online voice routing policy](manage-voice-routing-policies.md) assigned if the Call queue uses transfer mode.
- An [Audio Conferencing license](set-up-audio-conferencing-in-teams.md) or [online voice routing policy](manage-voice-routing-policies.md) assigned if the Call queue uses conference mode.

If your agents are using the Microsoft Teams app for Call queue calls, they need to be in TeamsOnly mode.

When using a resource account for calling line ID purposes in Call queues, the resource account must have a Teams Phone Resource Account license and one of the following assigned:

- A [Calling Plan](calling-plans-for-office-365.md) license and a phone number assigned.
- An [Operator Connect](operator-connect-plan.md) phone number assigned.
- An [online voice routing policy](manage-voice-routing-policies.md).
  - Phone number assignment is optional when using Direct Routing.

When an Auto attendant or Call queue is transferring calls to an external number, specific resource accounts as outlined below must have a Teams Phone Resource Account license and one of the following assigned:

- A [Calling Plan](calling-plans-for-office-365.md) license and a phone number assigned.
- An [Operator Connect](operator-connect-plan.md) phone number assigned.
- An [online voice routing policy](manage-voice-routing-policies.md).
  - Phone number assignment is optional when using Direct Routing.

Which resource account to license:

- All resource accounts must have a free [Microsoft Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md).
- License the resource account on the first Auto attendant receiving the call when that Auto attendant transfers to other Auto attendants or Call queues that transfer calls externally.
- In all other calling scenarios, license the resource account of the Auto attendant or Call queue performing the external transfer.

> [!NOTE]
> If the Calling Plan assigned to the resource account becomes disabled or is removed, [Communications Credits](what-are-communications-credits.md), if available in the tenant (without being assigned to the resource account), will be consumed. If there is no Calling Plan or Communications Credits, the call will fail.
>
> Direct Routing service numbers for Auto attendant and Call queues are supported for Microsoft Teams users and call agents only.
> 
> Transfers between Calling Plan, Operator Connect, and Direct Routing trunks aren't supported.
> 
> In a Hybrid scenario, the resource account must be created on-premises. For more information, see [Plan Cloud call queues](/skypeforbusiness/hybrid/plan-call-queue).
> 
> New Commerce Experience customers are not yet supported for resources accounts when an auto attendant or call queue needs to transfer calls to an external number.

## Business decisions

Before you set up your Auto attendants and Call queues, there are some decisions that you should make about how to use these features in your business. These decisions determine the settings you choose when configuring your Auto attendants and Call queues.

Document your answers to these questions and provide the information to the administrator doing the configuration.

- How will callers reach you? Internally only? Externally? Click-to-call on the web?
- What languages do you need? Where are these languages needed - which department or group?
- Do you want to allow voice inputs from callers or only dialing inputs?
- Do you need separate call routing for off hours or holidays? What are the hours and holidays?
- Do you want to allow agents in a Call queue to opt out of taking calls?
- Do you want agents in your Call queues or your operator to have a specific caller ID if they dial out?
- Do you want to enable [call parking and retrieval](call-park-and-retrieve.md) in your organization to help with call handoffs between people or departments?
- For the voice prompts, do you want to record your own or use the system-generated voice?
  - The system-generated voice is easy to update.

## Technical decisions

When using Auto attendants and Call queues to connect callers to people in your organization, there are some technical decisions to make before you start the configuration.

Agents can be added to Call queues in the following ways:

- Individual users
- Distribution lists
- Security groups, including mail-enabled security groups
- Microsoft 365 Groups or Teams

You can use a combination of these options for each queue if needed. Groups that have an email address can be used for voicemail. Using Teams offers many advantages, including shared file storage and chat between agents, a common mailbox where voicemails can be received, and an extensible platform that can include integration with your line-of-business applications or Power Apps.

We recommend choosing a strategy for adding call agents to queues before you start your configuration.

If you have existing Auto attendants and Call queues that you're migrating to Teams, you need a plan to transfer your existing phone numbers to the new Auto attendants and Call queues. You might need to create a [port order](phone-number-calling-plans/port-order-overview.md) to move your numbers from another providers. We recommend that you temporarily acquire one or more new phone numbers and test your Auto attendant and Call queue flows before switching them over the numbers you currently have in service.

**Conference mode** is an option in Call queues that significantly reduces the amount of time it takes to connect Teams VoIP calls and external PSTN (Public Switched Telephone Network) calls to an agent. For conference mode to work, agents in the Call queue must use one of the following clients:

- The latest version of the Microsoft Teams desktop client, Android app, or iOS app.
- Microsoft Phone System version 1449/1.0.94.2020051601 or later.
  
Set Agents' Teams accounts to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list.

Conference mode is enabled by default. If you have agents who don't meet the requirements, then conference mode must be manually disabled during Call queue configuration.

**Call routing flow** plans help determine the most efficient routing for people calling into your organization. To learn how to plan your call routing flow, see [Plan your call routing flow](plan-your-call-routing-flow.md).

## Click-to-call restrictions

In order to help prevent a denial of service attack from web based click-to-call applications, there's a maximum of 40 click-to-call calls per minute across all auto attendants and call queues in the tenant.

## Supported audio file formats

When using a recorded audio file for prompts or music the supported formats are WAV (uncompressed, linear PCM (Pulse-code modulation) with 8/16/32-bit depth in mono or stereo), WMA (mono only), and MP3. 

The audio file content cannot be more 5MB.

## Getting started

Once you complete the planning tasks in this article, follow these steps to get your Auto attendants and Call queues set up:

1. Get a [Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md) for each resource account that you plan to create. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your resource accounts in the future.
1. [Create a resource account](manage-resource-accounts.md) for each Auto attendant and Call queue that you want to create.
1. Assign a Teams Phone Resource Account license to each resource account.
1. Get service numbers for the Auto attendants and Call queues that you want phone callers from outside your organization to call. This might include [transferring numbers from another provider](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [requesting new service numbers](getting-service-phone-numbers.md).
1. Create click-to-call configurations for the [Auto attendants](/azure/communication-services/quickstarts/voice-video-calling/get-started-teams-auto-attendant) and [Call queues](/azure/communication-services/quickstarts/voice-video-calling/get-started-teams-call-queue) that you want users on your website or in your mobile applications to call.
1. [Create the holidays](set-up-holidays-in-teams.md) for which you want to have separate call routing in your Auto attendants.
1. Create the groups or Teams channels that you want to use to contain the call agents for the Call queues.
1. If you plan to allow dial by extension, ensure that you add your users' extension number to their Azure Active Directory (Azure AD) profile.
1. Optionally, [set up call parking and retrieval](call-park-and-retrieve.md) if you want to use this feature to help with call transfers.

Once you completed the steps above, you're ready to create your Auto attendants and Call queues. Because Auto attendants and Call queues can redirect calls to each other, refer to the workflow diagram that you created to determine which Auto attendant or Call queue should be created first. In the example in the diagram above, you would create the sales and support Call queues before you create the Contoso main Auto attendant because the main Auto attendant needs to direct callers to the sales and support Call queues.

See the following articles for information on how to create Auto attendants and Call queues:

- [Set up an Auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a Call queue](create-a-phone-system-call-queue.md)

> [!IMPORTANT]
> A user's Azure AD GUID token is stored as part of the Auto attendant or Call queue configuration when the user is configured as:
>
>  - an Auto attendant or Call queue **Authorized user**.
>  - an Auto attendant **Operator**.
>  - a **Person in Organization** transfer point.
>  - an individual member of a Call queue.
> 
> The Auto attendant and Call queue configurations aren't synchronized with Azure AD lifecycle events.  Teams administrators need to manually update Auto attendant and Call queue configurations to remove this personal data when a user included in the configuration leaves the organization.
>
> This doesn't apply to Call queue agent memberships that are configured via distribution lists or channels. It also doesn't apply to users who are reached through the **Dial by Name** or **Dial by Number** feature of Auto attendants.

If you need more extensive capabilities, such as integration with workflows, bots, and SMS (Short Message Service), consider [Azure Communication Services](/azure/communication-services/overview).

## Related topics

[Plan Direct Routing](direct-routing-plan.md)

[Routing calls with Auto attendants and Call queues](plan-your-call-routing-flow.md)

[Set up a Microsoft Teams Auto attendant](create-a-phone-system-auto-attendant.md)

[Create a Call queue in Microsoft Teams](create-a-phone-system-call-queue.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
