---
title: Routing calls with Auto attendants and Call queues for Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 12/05/2023
ms.topic: article
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: Learn how to plan your call routing flow for Auto attendants and Call queues in Microsoft Teams.
--- 

# Routing calls with Auto attendants and Call queues

As part of the planning process, we recommend that you work out the call routing for your organization in a diagram. The diagram helps determine the most efficient routing for people calling in to your organization. You can also use the diagram to determine the Auto attendants and Call queues that you need to create, along with related requirements such as service numbers, licenses, and resource accounts.

Let's look at how Auto attendants and Call queues route calls.

Auto attendants route all calls in one of the following ways:

- **Redirect immediately** - calls can be redirected to one of the call routing destinations (listed below) immediately upon answering or after an initial greeting.
- **Redirect based on dial options** - callers can be directed to choose between options that are assigned to the numbers on their telephone keypad, 0-9, \* and \#. Each dial key can be assigned a call routing destinations.
- **Dial people by name or extension** - callers can be directed to dial the extension number of the person they're trying to reach in your organization's directory, or by spelling the person's name.
- **Disconnect** - an Auto attendant can hang up the call.

> [!NOTE]
> A single Auto attendant can only support a single "dial by" method.  To allow callers to dial by name and by number, you need to create an Auto attendant that has an option for dial by name and the another for dial by extension.  Each of these options route to separate Auto attendants configured for these "dial by" scenarios.

An Auto attendant or Call queue can redirect calls to the following destinations:

- **Person in the organization** - a person in your organization who is able to receive voice calls. This person can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another Auto attendant or a Call queue. Choose the resource account associated with the destination.
- **External phone number** - any phone number. See [external transfer technical details](create-a-phone-system-auto-attendant.md?tabs=additional-resources).

- **Voicemail** - the voice mailbox associated with a Microsoft 365 group, distribution list, or mail-enabled security group that you specify. You can choose if you want voicemail transcriptions and the "Please leave a message after the tone." system prompt.
- **Operator** (Auto attendant only) - the operator defined for the Auto attendant. Defining an operator is optional. An operator can be any of the other destinations in this list.

Auto attendants offer separate call routing options for calls received outside of business hours and on holidays.

Call queues place the caller on hold until an agent assigned to the queue is available to take their call. There are two situations where a caller might be directed out of the queue:

- **Call overflow** - if the number of calls in the queue exceeds the limit that you set, then new callers are redirected out of the queue.
- **Call timeout** - if a caller stays in the queue longer than the configured timeout setting, they're redirected out of the queue.

Calls redirected out of a queue can be sent to any of the call routing destinations listed above except for an operator. Call queues don't have operators, but you can redirect callers to the same destination as an operator that's configured for an Auto attendant.

The following diagram shows an example of call routing using Auto attendants and Call queues.

![Diagram of call routing using Auto attendants and Call queues.](media/attendant-and-queue-call-routing.png)

In this example:

- The zero (0) key redirects callers to an operator. The operator for the Auto attendant is configured as a **Person in the organization**.
- The one (1) key redirects callers to the sales Call queue. This Call queue is connected to a team that contains the sales team assigned to the queue.
- The two (2) key redirects callers to the support Call queue. This Call queue is connected to a team that contains the support team assigned to the team.
- The support Call queue has a direct phone number via an intervening Auto attendant. Having an Auto attendant answer the support line allows for separate off hours and holiday call routing.
- The three (3) key redirects users to another Auto attendant for the company directory. The company directory Auto attendant allows callers to call individuals in the organization by dialing their name or extension.

We recommend that you create one or more diagrams similar to the example given to map out your call routing. Be sure your diagram or accompanying documentation includes the following:

- The Auto attendants that have direct access via phone numbers.
- The off-hours and holiday routing requirements for each Auto attendant.
- The membership for each Call queue. (You can add users individually or map the queue to different kinds of groups. Mapping a queue to a team provides the most versatile experience.)

Here are some call routing best practices:

- Look at your existing calling system and analyze the types and frequency of incoming calls. Use this information to help inform your Auto attendant and Call queue structure.
- Put the most common options earliest in the menu to route calls as quickly as possible.
- Avoid connecting service numbers directly to Call queues unless the queues are available 24/7. Call queues don't allow for separate call handling for off hours or holidays. If you want to have a queue with a direct number, assign the number to an Auto attendant that automatically redirects to the queue during business hours.
- If you receive numerous calls requesting basic information about your company, such as business hours, location, or web site address, consider creating an Auto attendant to answer these questions with recorded messages.
- Keep the list of menu items to five or fewer. Callers can have trouble remembering more than five options. Use nested Auto attendants if more options are needed to properly route a call.
- Describe the service first, followed by the option to press (for example: For Sales press 1) rather than the other way around (for example: Press 1 for Sales).
- User terminology your callers understand rather than what you might use internally.
- Avoid frequent updates to call routing. If you change your menu options for an Auto attendant in the future, call that out in the voice prompts for the first 30 days.

> [!IMPORTANT]
> The maximum number of transitions a single call is permitted to make through Auto attendants and Call queues is twenty-five (25). After this, the call is disconnected. This is done to prevent a call from infinitely looping through a series of Auto attendants and Call queues.
>  
> For example, if a call arrives on Auto attendant #1 and the caller selects an option that sends them to Auto attendant #2, this counts as one transition. If the caller selects an option on Auto attendant #2 that returns them to Auto attendant #1 or sends them to Call queue #1, then this would count as a second transition.
>  
> Calls that remain in the same Auto attendant but return to the main menu multiple times, for example when an announcement is played or there is a configured menu option to repeat, are also counted as a transition and are impacted by this maximum transition limit.

## Related articles

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)

[Set up Auto attendants](create-a-phone-system-auto-attendant.md)

[Set up Call queues](create-a-phone-system-call-queue.md)
