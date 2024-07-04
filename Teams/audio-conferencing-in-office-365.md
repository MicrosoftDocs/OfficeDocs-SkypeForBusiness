---
title: Plan Audio Conferencing for Teams meetings
ms.reviewer: 
description: 
ms.topic: article
ms.author: jenz
author: jenzamora
manager: pamgreen
audience: admin
ms.date: 2/21/2024
ms.service: msteams
ms.subservice: teams-audio-conferencing
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
  - m365initiative-meetings
ms.custom: 
  - seo-marvel-mar2020
f1.keywords: 
  - NOCSH
ms.localizationpriority: high
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---

# Plan Audio Conferencing for Microsoft Teams meetings

This article is for administrators and IT professionals who are evaluating Audio Conferencing for Teams meetings. 

Audio Conferencing enables users to join a Teams meeting from a phone using a Public Switched Telephone Network (PSTN) phone number. Audio Conferencing is sometimes called dial-in conferencing or PSTN conferencing. 

Audio Conferencing requires an additional Teams add-on license for each person in your organization who is going to schedule/host an Audio Conferencing meeting. Meeting attendees who dial in don't need any additional licenses assigned to them. For more information, see [Audio Conferencing add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md#audio-conferencing-licenses). (Note that Audio Conferencing doesn't require a Teams Phone license.)  

This article describes Audio Conferencing concepts, scenarios, and prerequisites. After reading this article, for step-by-step instructions on how to set up Audio Conferencing, see [Set up Audio Conferencing](set-up-audio-conferencing-in-teams.md).


## Audio Conferencing scenarios

Calling in (dialing in) to meetings is useful for users who are on the road and can't attend a meeting using the Microsoft Teams app on their laptops or mobile devices. But there are other scenarios in which using a phone to attend a Teams meeting can be a better option than using an app on a computer:
  
- Internet connectivity is limited.
- A meeting is audio only.
- The person tried to join a Teams meeting and it failed.
- The call quality is better when dialing in.
- People can join a meeting "hands free" using Bluetooth devices.
- People find it's easier and more convenient for their situation.

You only need to set up Audio Conferencing for people who plan to schedule or lead meetings. You don't need to set up Audio Conferencing for attendees. 

After attendees join the meeting, they can also dial out and invite other callers into a Teams meeting.
For more information, see [Dial out from a Teams meeting so other people can join it](dialing-out-from-a-teams-meeting-so-other-people-can-join-it.md).


## Audio Conferencing prerequisites

Before you can roll out Audio Conferencing for Teams meetings, consider these questions:

| Ask yourself | Action |
| :------------| :-------|
| Is Audio Conferencing available in my country/region?| To find out if Audio Conferencing is available in your country/region, see [Country and region availability for Audio Conferencing](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).|
| Do my users have the proper licensing for Audio Conferencing? |  Audio Conferencing licenses are available as part of a Microsoft 365 or Office 365 E5 plan. Audio conferencing licenses are also available as an add-on service for a Microsoft 365 Business Standard, E1, or E3 subscription. <br><br>For more information, see [Audio Conferencing add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md#audio-conferencing-licenses) and [Assign add-on licenses](./teams-add-on-licensing/assign-teams-add-on-licenses.md). |
| Do I need to purchase Communications Credits for the users who are assigned Audio Conferencing licenses?| To learn more, read [What are Communications Credits](what-are-communications-credits.md), then check out the [Communications Credits](#communications-credits) section.|

For pricing information, see [Pricing for Audio Conferencing](https://go.microsoft.com/fwlink/?linkid=799762&clcid=0x409).


## Audio Conferencing bridges

When you set up Audio Conferencing for Teams meetings, you get an Audio Conferencing bridge. The bridge answers the call for users who are dialing in to the meeting using a phone. The bridge answers the caller with voice prompts from an Auto attendant, and then, depending on your settings, can play notifications, ask callers to record their name, and so on.  

A conferencing bridge can contain one or more *service* phone numbers. A service phone number is a number assigned to a service, such as Audio Conferencing, rather than to an individual user. The phone number you set is included on the meeting invites for Teams. 

In addition to the phone numbers already assigned to your conferencing bridge, you can get additional service numbers (toll and toll-free) from other locations. You can assign these numbers to the conferencing bridge so you can expand coverage for your users. For more information, see [Manage phone numbers for your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md). 


| Ask yourself| Action |
| :------------| :-------|
| Do I need to add new conferencing bridge numbers?| To add new numbers, see [Get service phone numbers](./getting-service-phone-numbers.md).|
| Will I need to modify the bridge settings?|To modify the bridge settings, see [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).|
| Do I need to port numbers to use with Audio Conferencing?| To learn about porting phone numbers, read [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).|


There are numerous settings that you can manage for your conferencing bridge and for your users. You can use the default settings or change settings. 

For example, you might want to change the PIN that meeting organizers use to start meetings if they can't join the meeting using the Teams app. You might want to manage entry and exit announcements for meetings. You might want to manage settings for users, such as notify users of setting changes, or disable toll-free numbers for users. For more information, see the Manage section of the Audio Conferencing articles and [Manage settings for users](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).


### Phone numbers for Audio Conferencing bridges

With Audio Conferencing, your users can use toll and toll-free servive numbers to dial in to meetings. 

- With toll numbers, invitees pay when calling the number.
- With toll-free numbers, invitees don't pay when calling the number.

Toll-free phone numbers are available, but only in some countries/regions. To see what is available in your country or region, see [Country and region availability for Audio Conferencing](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).


In addition to toll and toll-free, phone numbers can be **dedicated** or **shared.** 

- [**Dedicated numbers**](#dedicated-phone-numbers) are available only to users within your organization. You *can* change the languages that are used when someone calls in to a dedicated number. 

- [**Shared numbers**](#shared-phone-numbers) are numbers that can be shared with users in *other* Microsoft 365 organizations. You *cannot* change the languages that are used when a user calls in to a shared number.

The default Audio Conferencing number assigned to a meeting organizer is included in the meeting invite. However, a caller can use any of the phone numbers assigned to your conferencing bridge to join a meeting. Users can find the list of phone numbers available for joining a meeting using the **Find a local number** link included on every meeting invite.

For more information, see [Phone numbers for Audio Conferencing in Teams meetings](phone-numbers-for-audio-conferencing-in-teams.md).


#### Dedicated phone numbers
  
Dedicated Audio Conferencing phone numbers are service numbers that you can get and then assign to your organization. 

You can change the languages that are used when someone calls in to a dedicated number. For more information, see [Set auto attendant languages for Audio Conferencing in Microsoft Teams](set-auto-attendant-languages-for-audio-conferencing-in-teams.md).

You can get dedicated toll and toll-free phone numbers for your conferencing bridges in one of three ways:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your conference bridges using the Teams admin center. See [Get service phone numbers](./getting-service-phone-numbers.md).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365. for more information on porting existing numbers, see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
  
- **Use a request form for new numbers.** Sometimes (depending on your country/region) you aren't able to get your new phone numbers using the Teams admin center, or you need specific phone numbers or area codes. If so, you need to download a form and send it back to us. For more information, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).



#### Shared phone numbers
  
Shared Audio Conferencing phone numbers are service numbers that can be shared with other Microsoft 365 organizations. Shared numbers are automatically assigned to organizations when they're enabled for Audio Conferencing. You can't change the languages that are used when someone calls in to a shared number.

When you assign shared phone numbers, you assign one number as the default number of the conferencing bridge. The default number must be from the country/region of the organization. The country or region location of the organization can be found by signing in to the **Microsoft 365 admin center** and looking under **Organization Profile**.

For most countries and regions, shared numbers are automatically assigned as toll numbers. However, there are exceptions as noted below.

> [!IMPORTANT]
> Due to limited availability of toll phone numbers in Venezuela, Indonesia, and United Arab Emirates (UAE), organizations from these countries/regions won't have an Audio Conferencing toll number automatically assigned to them. Toll-free numbers from these locations are available depending on available inventory.

To see which countries/regions have phone numbers automatically assigned to organizations, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).


## Communications Credits

To provide toll-free conference bridge phone numbers, and to support conferencing dial-out to international phone numbers, you must set up Communications Credits for your organization. For more information, see [What are Communications Credits?](what-are-communications-credits.md).

|Ask yourself|Action |
|------------|-------|
|Are Communications Credits required for my Audio Conferencing implementation? |To find out if you need to set up Communications Credits, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|
|If they're required, how much should I purchase?|To determine the Communications Credits amount, see [Recommended funding amounts](what-are-communications-credits.md#recommended-funding-amounts).|
|Do I want to configure an auto-recharge amount?|To configure an auto-recharge amount, see [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).|


## Meeting and call quality

Teams provides several tools to monitor and manage call quality. For more information, see [Manage call quality](monitor-call-quality-qos.md).


## Related articles

- [Set up Audio Conferencing](set-up-audio-conferencing-in-teams.md)




