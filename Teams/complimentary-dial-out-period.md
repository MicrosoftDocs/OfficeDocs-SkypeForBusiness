---
title: "Complimentary dial-out period"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: mikedav, OscarR
ms.topic: conceptual
ms.assetid: dc6e95cd-51e8-49ca-bcd3-78dc9dae486a
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: null
f1.keywords:
- CSH
ms.custom: 
  - Legal
  - seo-marvel-mar2020
description: Learn about the complimentary dial-out period for a Microsoft 365 calling plan and Audio Conferencing in Microsoft Teams.
---

# Audio Conferencing complimentary dial-out period

## Teams PSTN Services

Customers may use a Microsoft 365 or Calling Plan and Teams Audio Conferencing as permitted in the Teams PSTN Services Use Terms and Customer's volume licensing agreement. The PSTN Services Use Terms may be found at [Licensing Resources and Documents](https://www.microsoft.com/licensing/docs).

### End of complimentary dial out period

The complimentary dial-out capability ended on December 1, 2019. For more information, see [Audio Conferencing subscription dial out and call me at benefit](audio-conferencing-subscription-dial-out.md).

This change did not take place for countries where the Audio Conferencing subscription is available, but we do not currently enable setting up Communications Credits. These specific countries are Russia, South Korea, and Taiwan.

### Complimentary dial out period details

For customers who are adopting our Microsoft 365 Audio Conferencing service, Microsoft is providing an additional complimentary benefit related to dial out from meetings that are organized by users who are assigned a Microsoft 365 Audio Conferencing subscription license through November 2019. During this complimentary period, Microsoft allows meeting organizers or authorized attendees, as defined in meeting policy settings, to make dial-out calls from within the meeting to non-premium phone numbers in the 44 [Zone A countries and regions](audio-conferencing-zones.md). This benefit is applicable to Audio Conferencing monthly subscription licenses and does not extend to Audio Conferencing pay-per-minute licenses.

In addition, there is a 900-minute limit during the complimentary dial out period as such:

Users with a license usage location (the location is the user country location that is defined in the licensing area of the Microsoft 365 admin center) in _any__ country can dial out from a conference to any of the 44 [Zone A countries and regions](audio-conferencing-zones.md). Each user receives 900 minutes per user per month to _any_ of the [Zone A countries and regions](audio-conferencing-zones.md), which are pooled at the tenant level. For example, a customer has purchased 115 Audio Conferencing subscription licenses and has 10 users in the US, 100 users in the UK, and 5 users in India, all with Audio Conferencing subscription licenses assigned to their users.

- All 115 users share a pool of (115 users X 900 min) = 103,500 conferencing dial-out out minutes per calendar month, which can be used to place outbound calls to any of the [Zone A countries and regions](audio-conferencing-zones.md).

- All calls exceeding the 103,500 minutes per calendar month are billed per minute using Communications Credits at our published rates to that destination. (Note: Tenant must set up Communications Credits and assign the Communications Credits license to the meeting organizer).

- All outbound calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list are billed per minute using Communications Credits at our published rates to that destination (provided tenant has set up Communications Credits and assigned the Communications Credits license to the meeting organizer).

> [!NOTE]
> You can monitor the usage against dial-out minute pool in the Teams admin center. In the Microsoft Teams admin center, go to **Legacy portal** > **Reports** > **PSTN Minute Pools**. This complimentary minute pool will be labeled in the report as "Outbound Calls to Zone A countries and regions."

Email notifications will be sent to all tenant administrators of a given customer when the utilization of the tenant's dial-out minutes pool has reached 80% and 100%.

For dial-out calls that are billed per minute (calls exceeding the tenant dial-out minute pool or calls to destinations not in the [Zone A countries and regions](audio-conferencing-zones.md) list), the calls and their associated rates are based primarily on the destination of the call and not the country or region of the organizer or the participant initiating the dial-out call. For example, a call to a phone number in France will be billed with the same rate if it is initiated by a meeting participant in the United States or one in France.

For more information about Communication Credits, see [Communications Credits](what-are-communications-credits.md).

## Related topics

- [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
- [Country and region zones for Audio Conferencing](audio-conferencing-zones.md)
