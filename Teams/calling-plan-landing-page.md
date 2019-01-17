---
title: Calling Plan in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/16/2019
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
ms.reviewer: crowe
search.appverid: MET150
description: Calling Plan landing page
appliesto: 
- Microsoft Teams
---

# Phone System with Calling Plan 

You've completed the [Quick start](get-started-with-teams-quick-start.md). You've rolled out Teams with [chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md) across your organization. Maybe you've deployed [Meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md). Now you're ready to add cloud voice workloads, and you've decided to use Microsoft Phone System with Calling Plan to connect to the Public Switched Telephone Network (PSTN). 


This article describes core deployment decisions for Calling Plans as well as additional considerations you may want to configure, based on your organization's needs.


## Learn more about Calling Plans

The following articles provide more information about deploying and using Microsoft Caling Plans:

- [Phone System in Office 365](what-is-phone-system-in-office-365.md)
- [Calling Plans for Office 365](calling-plans-for-office-365.md)
- [Set up Calling Plans](set-up-calling-plans.md)


## Core deployment decisions

To use Microsoft as your telephony carrier, you need to obtain Calling Plan licenses and assign them to your Phone System users. 

There are two types of Calling Plans available:

- Domestic Calling Plans 
- Domestic and International Calling Plans

|Ask yourself|Action |
|------------|-------|
|<ul><li>Are Calling Plans available in my area?</li><li>Which user locations will have the Calling Plans service? </li><li>Do my users need international calling?</li><li>Do my users have Calling Plans licenses?</li><li>Do my users each have a direct inward dial (DID) phone number?</li></ul>|<ul><li> To find out if Calling Plans are available in your area, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).</li><li>To buy and assign licenses, see [Step 2: Buy and assign licenses](set-up-calling-plans.md#step-2-buy-and-assign-licenses).</li><li>To get phone numbers, see [Step 3: Get phone numbers](set-up-calling-plans.md#step-3-get-phone-numbers). </li></ul>|
|||


### Phone numbers and emergency locations

With Calling Plans in Office 365, every user in your organization needs to have a unique direct inward dial (DID) phone number and a corresponding validated emergency address. You can also specify an emergency location within the emergency address (for example, an office number or floor number). 

|Ask yourself|Action |
|------------|-------|
|How detailed do I want the emergency address and location information to be? |For more information, see [What are emergency locations, addresses, and call routing?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing)


### Calling identity

By default, all outbound calls use the assigned phone number as calling identity (caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call.

|Ask yourself|Action |
|------------|-------|
|Do I want to mask or disable caller ID? | To change or block the caller ID, see [Set the caller ID for a user](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/set-the-caller-id-for-a-user). |
|||


