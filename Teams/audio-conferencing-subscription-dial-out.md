---
title: Audio Conferencing Dial-Out/Call Me At minutes
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: mikedav, oscarr
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Licensing
  - seo-marvel-mar2020
description: Dial-Out and Call Me At minutes benefit. As of December 1, 2019 each audio conferencing subscription provides 60 minutes per-user per-month to Zone A countries.
---

# Audio Conferencing subscription "Dial-Out"/"Call Me At" minutes benefit

## Microsoft Teams and Skype for Business PSTN Audio Conferencing

Each Audio Conferencing standard subscription provides 60 minutes per user per month that can be used to dial out to non-premium numbers in ANY of the Zone A countries as described in this document. This benefit applies to Audio Conferencing *monthly subscription* licenses and doesn't extend to Audio Conferencing pay-per-minute licenses.

> [!NOTE]
> The dial-out minute pool size of the Audio Conferencing dial-out to USA and Canadian subscriptions is based on the number of licenses *assigned* to users. For example, if a customer has 100 licenses, and 20 of them are assigned to users, the dial-out minute pool of the Audio Conferencing dial-out to USA or Canadian subscription will be 1200 minutes (60 dial-out minutes to the subscription x 20 licenses assigned to users).

> [!NOTE]
> The end of the [complimentary dial-out period](complimentary-dial-out-period.md) did not take place on November 30, 2019, for countries where the Audio Conferencing subscription is available, but we do not currently provide the ability to set up Communications Credits. These specific countries are Russia, South Korea, and Taiwan.

## Audio Conferencing "Dial Out From a Meeting" & "Call Me At" details

For customers adopting our Audio Conferencing service, Microsoft provides the ability to dial out from meetings organized by users assigned an Audio Conferencing subscription license. Dial-out calls to countries not included in the [Zone A countries and regions](audio-conferencing-zones.md) list are charged per minute using Communications Credits. For dial-out calls that are billed per minute (calls exceeding the tenant dial-out minute pool or calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list), the calls and their associated rates are based on the destination of the call and not the organizer's country of residence or the meeting participant initiating the dial-out call. For example, an audio conference dial-out call to a phone number in France, which is a Zone A country, will be billed at the same per-minute rate if it were initiated by a meeting participant in the United States, France, or Zimbabwe.

|Meeting organizer license usage location |Destination dialed |Can I use my dial-out minute pool minutes?|Do I need Communications Credits?|
|---------|---------|---------|---------|
|United States |United States |Yes (Zone A country) |Yes *after* consuming the tenant minute pool         |
|United States |United Kingdom|Yes (Zone A country) |  Yes *after* consuming the tenant minute pool       |
|United States     |Zimbabwe|    No     |     Yes on *ALL* calls    |
|United Kingdom     |United Kingdom|Yes (Zone A country) |  Yes *after* consuming the tenant minute pool       |
|United Kingdom     |United States |Yes (Zone A country) |  Yes *after* consuming the tenant minute pool       |
|United Kingdom     |Zimbabwe|    No     |   Yes on *ALL* calls      |
|Zimbabwe     |Zimbabwe|    No     |    Yes on *ALL* calls     |
|Zimbabwe     |United States | Yes (Zone A country) | Yes *after* consuming the tenant minute pool        |
|Zimbabwe     |United Kingdom | Yes (Zone A country) | Yes *after* consuming the tenant minute pool        |
|Cook Islands     |Cook Islands |   No      |    Yes on *ALL* calls     |
|Cook Islands     |United States  | Yes (Zone A country) |  Yes *after* consuming the tenant minute pool       |
|Cook Islands     |United Kingdom | Yes (Zone A country) | Yes *after* consuming the tenant minute pool        |
|    |         |         |         |

## How are minute pools calculated?

Consider the following example. A customer has purchased 115 Audio Conferencing subscription licenses and has 10 users in the United States, 100 users in the United Kingdom, and 5 users in Zimbabwe, all with Audio Conferencing subscription licenses assigned. All 115 users share a pool of (115 users x 60 min = 6,900 conferencing dial-out out minutes per calendar month) to place outbound calls to non-premium numbers in any of the [Zone A countries and regions](audio-conferencing-zones.md), *regardless* of where the meeting organizer is licensed or physically located. For example, a Zimbabwe meeting organizer will be able to dial out to any of the [Zone A countries and regions](audio-conferencing-zones.md) up to the minute pool limit.

- All dial-out calls exceeding 6,900 minutes per calendar month are billed per minute using Communications Credits at our published rates to that destination.

   > [!NOTE]
   > The customer must set up [Communications Credits](what-are-communications-credits.md) and assign the Communications Credits license to the meeting organizer.

- All dial-out calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list are billed per minute using Communications Credits at our published rates to that destination (provided the customer has set up Communications Credits and assigned the Communications Credits license to the meeting organizer).

## How can I monitor minute my pool usage?

- You can monitor the usage against your dial-out minute pool in the Microsoft Teams admin center. In the left navigation, go to **Analytics & reports** > **Usage reports**, and then select **PSTN minute pools**. The Zone A dial-out minute pool will be labeled in the report as "Outbound Calls to Zone A Countries."
- Email notifications will be sent to the following admins when the utilization of your organization's dial-out minutes pool has reached 80 percent and 100 percent:

  - Billing Administrator
  - Skype for Business Administrator
  - Global Administrator
  - User Administrator
  - Helpdesk Administrator
  - Service Support Administrator
  - Azure AD Joined Device Local Administrator
  - Application Administrator
  - License Administrator
  - Cloud Device Administrator
  - Authentication Administrator
  - Privileged Authentication Administrator
  - Teams Communications Administrator
  - Teams Communications Support Engineer
  - Teams Communications Support Specialist
  - Teams Administrator

For additional information on Communication Credits, see [Communications Credits](what-are-communications-credits.md).

## Related topics

- [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
- [Country and region zones for Audio Conferencing](audio-conferencing-zones.md)
