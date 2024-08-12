---
title: "Complimentary dial-out"
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: mikedav, OscarR
ms.date: 06/28/2024
ms.topic: conceptual
ms.assetid: dc6e95cd-51e8-49ca-bcd3-78dc9dae486a
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: Low
f1.keywords:
- CSH
ms.custom: 
  - Legal
  - seo-marvel-mar2020
description: Learn about the complimentary dial-out for a Microsoft 365 calling plan and Audio Conferencing in Microsoft Teams.
---

# Audio Conferencing complimentary dial-out

## Teams PSTN Services

Customers may use a Microsoft 365 or Calling Plan and Teams Audio Conferencing as permitted in the Teams PSTN Services Use Terms and Customer's volume licensing agreement. The PSTN Services Use Terms may be found at [Licensing Resources and Documents](https://www.microsoft.com/licensing/docs).

### Complimentary dial out availability

The complimentary dial-out is only available in Russia, South Korea, and Taiwan, where Audio Conferencing is available, but Communications Credits setup isn't currently supported.

### Complimentary dial out details

For Audio Conferencing customers in Russia, South Korea, and Taiwan, we provide an additional complimentary benefit related to dial out from meetings that licensed Audio Conferencing users create. With complimentary dial-out, Microsoft allows meeting organizers or authorized attendees, as defined in meeting policy settings, to make dial-out calls from within the meeting to non-premium phone numbers in the 44 [Zone A countries and regions](audio-conferencing-zones.md). This benefit is applicable to Audio Conferencing monthly subscription licenses and doesn't extend to Audio Conferencing pay-per-minute licenses.

In addition, there's a 900-minute limit during the complimentary dial out as such:

Users with a license usage location (the location is the user country or region location that is defined in the licensing area of the Microsoft 365 admin center) in _any__ country or region can dial out from a conference to any of the 44 [Zone A countries and regions](audio-conferencing-zones.md). Each user receives 900 minutes per user per month to _any_ of the [Zone A countries and regions](audio-conferencing-zones.md), which are pooled at the tenant level. For example, a customer has purchased 115 Audio Conferencing subscription licenses and has 10 users in the US, 100 users in the UK, and 5 users in India, all with Audio Conferencing subscription licenses assigned to their users.

- All 115 users share a pool of (115 users X 900 min) = 103,500 conferencing dial-out out minutes per calendar month, which can be used to place outbound calls to any of the [Zone A countries and regions](audio-conferencing-zones.md).

- All calls exceeding the 103,500 minutes per calendar month are billed per minute using Communications Credits at our published rates to that destination. (Note: Tenant must set up Communications Credits and assign the Communications Credits license to the meeting organizer).

- All outbound calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list are billed per minute using Communications Credits at our published rates to that destination (provided tenant has set up Communications Credits and assigned the Communications Credits license to the meeting organizer).

> [!NOTE]
> You can monitor the usage against dial-out minute pool in the Teams admin center. In the Microsoft Teams admin center, go to **Legacy portal** > **Reports** > **PSTN Minute Pools**. This complimentary minute pool will be labeled in the report as "Outbound Calls to Zone A countries and regions."

Email notifications are sent to all tenant administrators of a given customer when the utilization of the tenant's dial-out minutes pool has reached 80% and 100%.

For dial-out calls that are billed per minute (calls exceeding the tenant dial-out minute pool or calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list), the calls and their associated rates are based primarily on the destination of the call and not the country or region of the organizer or the participant initiating the dial-out call. For example, a call to a phone number in France will be billed with the same rate if it's initiated by a meeting participant in the United States or one in France.

For more information about Communication Credits, see [Communications Credits](what-are-communications-credits.md).

## Related topics

- [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
- [Country and region zones for Audio Conferencing](audio-conferencing-zones.md)
