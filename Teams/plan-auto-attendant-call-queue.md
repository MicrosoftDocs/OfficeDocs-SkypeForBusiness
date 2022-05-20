---
title: Plan for Teams auto attendants and call queues
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: ab9f05a2-22cb-4692-a585-27f82d1b37c7
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
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
description: Learn about auto attendants and call queues and how to use them to help callers move through a menu system to reach people or departments in your organization.
---

# Plan for Teams auto attendants and call queues

Auto attendants allow you to set up menu options to route calls based on caller input. Menu options, such as "For Sales, press 1.  For Services press 2", for an auto attendant let an organization provide a series of choices that guide callers to their destination quickly, without relying on a human operator to handle incoming calls.

Call queues are waiting areas for callers. For situations where callers need to reach someone with a particular specialty - such as sales or service - rather than a specific person, you can use call queues to connect callers to the group of agents who can assist them. Callers are put on hold until an agent assigned to the queue is available to take their call.

Used together, auto attendants and call queues can easily route callers to the appropriate person or department in your organization.

## Auto attendants

The primary purpose of an auto attendant is to direct a caller to an appropriate person or department based on the caller's input to the provided menu options. Callers can be directed to specific people within your organization, to call queues where they wait to talk to the next available agent, or to voicemail. Different call routing options can be specified for business hours, off hours, and holidays.

Menu prompts can be created by using text-to-speech (system-generated prompts) or by uploading a recorded audio file. Speech recognition accepts voice commands for hands-free navigation, but people calling in can also use the phone keypad to navigate menus.

Each auto attendant has a specific language and time zone. If you do business in multiple languages or multiple parts of the world, you can create as many different auto attendants as you need to accommodate your callers.

For each auto attendant, you can configure an operator. While you can configure operator calls to go to various destinations, the operator feature is designed to allow callers to talk to a specific person in your organization who can help them.

Auto attendants can be configured to allow callers to search your organization's directory, either by name or by extension number. Within an auto attendant, you can specify who is available for the directory search by choosing groups of users to include or exclude. (This is known as *dial scope*.)

Callers can reach an auto attendant either by direct phone number, if configured, or by being redirected from another auto attendant or a call queue.

## Call queues

A call queue is analogous to a waiting room in a physical building. Callers wait on hold while calls are routed to the agents in the queue. Call queues are commonly used for sales and service functions. However, call queues can be used for any situation where the number of calls exceeds your internal capacity, such as a receptionist in a busy facility.

Call queues allow for specific routing of calls in cases where the total number of callers in the queue or the wait time exceeds the limits that you specify. Calls can be routed to specific people, voicemail, other call queues, or auto attendants.

Like auto attendants, call queues each have a language setting. You can use different call queues if you do business in multiple languages. Agents can be members of more than one queue if they're multi-lingual.

For each call queue, you can specify if agents in the queue can opt out of taking calls and if calls should be routed to them based on their presence indication in Teams.

You can assign a phone number to a call queue, however call queues do not provide separate call routing for off hours and holidays. Unless your call queue is staffed 24/7, we recommend assigning the phone number to an auto attendant that redirects to the call queue during business hours.

## Prerequisites

To configure auto attendants and call queues, you need the following resources:

- A resource account for each auto attendant and each call queue
- A free Microsoft Phone System - Virtual User license for each resource account that will be directly dialable from Teams users or external phone numbers
- At least one [Microsoft service number](getting-service-phone-numbers.md), Operator Connect number, Direct Routing number, or a hybrid number for each resource account that you want to be directly dialable from extenal phone numbers
 - The service number may be a toll or toll-free number

> [!NOTE]
> Resource accounts are disabled for sign in and must remain so. Chat and presence are not avaialble for these accounts.

Agents who receive calls from the call queues must be Enterprise Voice enabled online or on-premise users. In addition, if the call queues are using Direct Routing numbers, agents who need to conference or transfer calls also require:

- An online voice routing policy assigned if the call queue uses transfer mode
- An Audio Conferencing license or online voice routing policy assigned if the call queue uses conference mode

If your agents are using the Microsoft Teams app for call queue calls, they need to be in TeamsOnly mode.

When using a resource account for calling line ID purposes in call queues the resource account must have a Phone System Virtual User license and one of the following assigned:

- A [Calling Plan](calling-plans-for-office-365.md) license and a phone number assigned
- An [Operator Connect](operator-connect-plan.md) phone number assigned
- An [online voice routing policy](manage-voice-routing-policies.md) (phone number assignment is optional when using Direct Routing)

When an auto attendant or call queue is transferring calls to an external number specific resource accounts as outlined below must have a Phone System Virtual User license and one of the following assigned:

- A [Calling Plan](calling-plans-for-office-365.md) license and a phone number assigned
- An [Operator Connect](operator-connect-plan.md) phone number assigned
- An [online voice routing policy](manage-voice-routing-policies.md) (phone number assignment is optional when using Direct Routing)

- License the resource account on the first auto attendant receiving the call when that auto attendant transfers to other auto attendants or call queues that transfer calls externally
- In all other calling scenarios, license the resource account of the auto attendant or call queue performing the external transfer

> [!NOTE]
> If the Calling Plan assigned to the resource account becomes disabled or is removed, [Communications Credits](what-are-communications-credits.md), if available in the tenant (without being assigned to the resource account), will be consumed. If there is no Calling Plan or Communications Credits then the call will fail.
>
> Direct Routing service numbers for auto attendant and call queues are supported for Microsoft Teams users and call agents only.
> 
> Transfers between Calling Plan, Operator Connect, and Direct Routing trunks aren't supported.
> 
> In a Hybrid scenario, the resource account must be created on-premises. For more information, see [Plan Cloud call queues](/skypeforbusiness/hybrid/plan-call-queue).

## Business decisions

Before you set up your auto attendants and call queues, there are some decisions that you should make about how to use these features in your business. These decisions will determine the settings that you choose when you configure your auto attendants and call queues.

Document your answers to these questions and provide the information to the administrator doing the configuration.

- What languages do you need? Where are these languages needed - which department or group?
- Do you want to allow voice inputs from callers or only dialing inputs?
- Do you need separate call routing for off hours or holidays? What are the hours and holidays?
- Do you want to allow agents in a call queue to opt out of taking calls?
- Do you want agents in your call queues or your operator to have a specific caller ID if they dial out?
- Do you want to enable [call parking and retrieval](call-park-and-retrieve.md) in your organization to help with call handoffs between people or departments?
- For the voice prompts, do you want to record your own or use the system-generated voice? (The system-generated voice is easy to update.)

## Technical decisions

When using auto attendants and call queues to connect callers to people in your organization, there are some technical decisions to make before you start the configuration.

Agents can be added to call queues in the following ways:

- Individual users
- Distribution lists
- Security groups, including mail-enabled security groups
- Microsoft 365 Groups or Teams

You can use a combination of these options for each queue if needed. Groups that have an email address can be used for voicemail. Using Teams offers many advantages, including shared file storage and chat between agents, a common mailbox where voicemails can be received, and an extensible platform that can include integration with your line-of-business applications or Power Apps.

We recommend choosing a strategy for adding call agents to queues before you start your configuration.

If you have an existing auto attendant and call queue infrastructure and you're migrating to Teams, you'll need a plan to transfer your existing phone numbers to the new auto attendants and call queues. You might need to create a [port order](phone-number-calling-plans/port-order-overview.md) to move your numbers from another providers. We recommend that you temporarily acquire one or more new phone numbers and test your auto attendant and call queue flows before switching them over the numbers you currently have in service.

*Conference mode* is an option in call queues that significantly reduces the amount of time it takes to connect Teams VOIP calls and PSTN calls to an agent. For conference mode to work, agents in the call queue must use one of the following clients:

- The latest version of the Microsoft Teams desktop client, Android app, or iOS app
- Microsoft Phone System version 1449/1.0.94.2020051601 or later
  
Set Agents' Teams accounts to Teams-only mode. Agents who don't meet the requirements aren't included in the call routing list.

We recommend enabling conference mode for your call queues if your agents are all using compatible clients.

## Plan your call routing flow

As part of the planning process, we recommend that you work out the call routing for your organization in a diagram. The diagram helps determine the most efficient routing for people calling in to your organization. You can also use the diagram to determine the auto attendants and call queues that you need to create, along with related requirements such as service numbers, licenses, and resource accounts.

Let's look at how auto attendants and call queues route calls.

Auto attendants route all calls in one of the following ways:

- **Redirect immediately** - calls can be redirected to one of the call routing destinations (listed below) immediately upon answering or after an initial greeting.
- **Redirect based on dial options** - callers can be directed to choose between options that are assigned to the numbers on their telephone keypad, 0-9. Each dial key can be assigned a call routing destinations.
- **Dial people by name or extension** - callers can be directed to dial the extension number of the person they're trying to reach in your organization's directory, or by spelling the person's name.
- **Disconnect** - an auto attendant can hang up the call.

> [!NOTE]
> A single Auto attendant can only support a single "dial by" method.  To allow callers to dial by name and by number, you will need to create an auto attendant that has an option for dial by name and the another for dial by extension.  Each of these options will route to separate auto attendants configured for these "dial by" scenarios.

When calls are redirected by an auto attendant or call queue, you can choose from the following call routing destinations:

- **Person in the organization** - a person in your organization who is able to receive voice calls. This can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another auto attendant or a call queue. Choose the resource account associated with the destination.
- **External phone number** - any phone number. (See [external transfer technical details](create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details)).
- **Voicemail** - the voice mailbox associated with a Microsoft 365 group that you specify. You can choose if you want voicemail transcriptions and the "Please leave a message after the tone." system prompt.
- **Operator** (auto attendant only) - the operator defined for the auto attendant. Defining an operator is optional. An operator can be any of the other destinations in this list.

Auto attendants offer separate call routing options for calls received outside of business hours and on holidays. 

Call queues place the caller on hold until an agent assigned to the queue is available to take their call. There are two situations where a caller might be directed out of the queue:

- **Call overflow** - if the number of calls in the queue exceeds the limit that you set, then new callers are redirected out of the queue.
- **Call timeout** - if a caller has been in the queue longer than the configured timeout setting, they're redirected out of the queue.

Calls redirected out of a queue can be sent to any of the call routing destinations listed above except for an operator. (Call queues don't have operators, but you can redirect callers to the same destination as an operator that you've configured for an auto attendant.)

The example below shows an example of call routing using auto attendants and call queues.

![Diagram of call routing using auto attendants and call queues.](media/attendant-and-queue-call-routing.png)

In the example above:

- The zero (0) key redirects callers to an operator. The operator for that auto attendant has been configured as a **Person in the organization**.
- The one (1) key redirects callers to the sales call queue. This call queue is connected to a team that contains the sales team assigned to the queue.
- The two (2) key redirects callers to the support call queue. This call queue is connected to a team that contains the support team assigned to the team.
- The support call queue has a direct phone number via an intervening auto attendant. Having an auto attendant answer the support line allows for separate off hours and holiday call routing.
- The three (3) key redirects users to another auto attendant for the company directory. The company directory auto attendant allows callers to call individuals in the organization by dialing their name or extension.

We recommend that you create one or more diagrams similar to the one above to map out your call routing. Be sure to include the following in your diagram or accompanying documentation:

- Which auto attendants will have direct access via phone numbers?
- What are the off-hours and holiday routing requirements for each auto attendant?
- The membership for each call queue. (You can add users individually or map the queue to different kinds of groups. Mapping a queue to a team provides the most versatile experience.)

Here are some call routing best practices:

- Look at your existing calling system and analyze the types and frequency of incoming calls. Use this information to help inform your auto attendant and call queue structure.
- Put the most common options earliest in the menu to route calls as quickly as possible.
- Avoid connecting service numbers directly to call queues unless the queues are available 24/7. Call queues don't allow for separate call handling for off hours or holidays. If you want to have a queue with a direct number, assign the number to an auto attendant that automatically redirects to the queue during business hours.
- If you receive numerous calls requesting basic information about your company, such as business hours, location, or web site address, consider creating an auto attendant to answer these questions with recorded messages.
- Keep the list of menu items to five or fewer. Callers can have trouble remembering more than five options. Use nested auto attendants if more options are needed to properly route a call.
- Describe the service first, followed by the option to press (eg: For Sales press 1) rather than the other way around (eg. Press 1 for Sales).
- User terminology your callers will understand rather than what you may use internally.
- Avoid frequent updates to call routing. If you change your menu options for an auto attendant in the future, call that out in the voice prompts for the first 30 days.

## Getting started

Once you've completed the planning tasks in this article, follow these steps to get your auto attendants and call queues set up:

1. Get the service numbers that you need for the auto attendants and call queues that you want to be accessible by direct dialing from outside your organization. This might include [transferring numbers from another provider](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [requesting new service numbers](getting-service-phone-numbers.md).

2. Get a [Phone System - Virtual User license](teams-add-on-licensing/virtual-user.md) for each resource account that you plan to create. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your resource accounts in the future.

3. [Create a resource account](manage-resource-accounts.md) for each auto attendant and call queue that you want to create. Assign each account a Phone System - Virtual User license and, optionally, a service number.

4. [Create the holidays](set-up-holidays-in-teams.md) for which you want to have separate call routing in your auto attendants.

5. Optionally, [set up call parking and retrieval](call-park-and-retrieve.md) if you want to use this feature to help with call transfers.

6. Create the groups that you want to use to contain the call agents for the call queues.

7. If you plan to allow dial by extension, ensure that you've added your users' extension number to their Azure Active Directory profile.

Once you've completed the steps above, you're ready to create your auto attendants and call queues. Because auto attendants and call queues can redirect calls to each other, refer to the workflow diagram that you created to determine which auto attendant or call queue should be created first. In the example in the diagram above, you would create the sales and support call queues before you create the Contoso main auto attendant because the main auto attendant needs to direct callers to the sales and support call queues.

See the following articles for information on how to create auto attendants and call queues:

- [Set up an auto attendant](create-a-phone-system-auto-attendant.md)
- [Create a call queue](create-a-phone-system-call-queue.md)

If you need more extensive capabilities, such as integration with workflows, bots, and SMS, consider [Azure Communication Services](/azure/communication-services/overview).

## Related topics

[Plan Direct Routing](direct-routing-plan.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)

[Create a call queue - small business tutorial](business-voice/create-a-phone-system-call-queue-smb.md)

[Set up an auto attendant - small business tutorial](business-voice/create-a-phone-system-auto-attendant-smb.md)
