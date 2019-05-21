---
title: "Audio Conferencing subscription “Dial-Out”/“Call Me At” benefit"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, oscarr
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help 
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Licensing
description: "Customers have been provided a complimentary dial-out capability that will end on November 30, 2019.  Beginning December 1, 2019, each audio conferencing subscription provides 60 minutes per user per month to ANY of the Zone A countries as described in this document. "
---

# Audio Conferencing subscription “Dial-Out”/“Call Me At” minutes benefit

## Microsoft Teams and Skype for Business PSTN Audio Conferencing

Customers have been provided a [complimentary dial-out capability](complimentary-dial-out-period.md) that will end on November 30, 2019. Beginning December 1, 2019, each Audio Conferencing subscription provides 60 minutes per user per month that can be used to dial out to non-premium numbers in ANY of the Zone A countries as described in this document. Your tenant dial-out minute pool size is based on *assigned* licenses and not purchased licenses. This benefit is applicable to Audio Conferencing *monthly subscription* licenses and does not extend to Audio Conferencing pay-per-minute licenses. 

## Audio Conferencing “Dial Out From a Meeting” & “Call Me At” details

For customers adopting our Audio Conferencing service, Microsoft provides the ability to dial out from meetings organized by users assigned an Audio Conferencing subscription license. Dial-out calls to countries not included in the “Zone A” country list are charged per minute using Communications Credits. For dial-out calls that are billed per minute (calls exceeding the tenant dial-out minute pool or calls to destinations not in the Zone A country list), the calls and their associated rates are based on the destination of the call and not the organizer’s country of residence or the meeting participant initiating the dial-out call. For example, an audio conference dial-out call to a phone number in France, which is a Zone A country, will be billed at the same per-minute rate if it were initiated by a meeting participant in the United States, France, or Zimbabwe. 


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

Consider the following example. A customer has purchased 115 Audio Conferencing subscription licenses and has 10 users in the United States, 100 users in the United Kingdom, and 5 users in Zimbabwe, all with Audio Conferencing subscription licenses assigned. All 115 users share a pool of (115 users x 60 min = 6,900 conferencing dial-out out minutes per calendar month) to place outbound calls to non-premium numbers in any of the Zone A countries, *regardless* of where the meeting organizer is licensed or physically located. For example, a Zimbabwe meeting organizer will be able to dial out to any of the Zone A countries up to the minute pool limit. 

- All dial-out calls exceeding 6,900 minutes per calendar month are billed per minute using Communications Credits at our published rates to that destination. (Note: The customer must set up [Communications Credits](what-are-communications-credits.md) and assign the Communications Credits license to the meeting organizer.)
- All dial-out calls to destinations not in the Zone A country list are billed per minute using Communications Credits at our published rates to that destination (provided the customer has set up Communications Credits and assigned the Communications Credits license to the meeting organizer).

## How can I monitor minute pool usage?

- You can monitor the usage against your dial-out minute pool in the “legacy” Skype for Business Admin Center. In the Microsoft Teams Admin Center, navigate to **Legacy portal** > **Reports** > **PSTN Minute Pools**. The Zone A dial-out minute pool will be labeled in the report as “Outbound Calls to Zone A Countries.”
- Email notifications will be sent to all tenant administrators of a given customer when the utilization of the tenant’s dial-out minutes pool has reached 80% and 100%.

For additional information on Communication Credits, see [Communications Credits](what-are-communications-credits.md).


|Zone A countries |
|---------|
|Australia      |
|Austria     |
|Belgium     |
|Brazil     |
|Bulgaria     |
|Canada     |
|China     |
|Croatia     |
|Czech Republic      |
|Denmark     |
|Estonia     |
|Finland     |
|France     |
|Germany     |
|Greece     |
|Hong Kong     |
|Hungary     |
|India     |
|Ireland     |
|Italy     |
|Japan     |
|Luxembourg      |
|Malaysia     |
|Mexico     |
|Netherlands     |
|New Zealand     |
|Norway     |
|Poland     |
|Portugal     |
|Puerto Rico     |
|Romania     |
|Russia     |
|Singapore     |
|Slovak Republic     |
|Slovenia     |
|South Africa     |
|South Korea     |
|Spain     |
|Sweden     |
|Switzerland     |
|Taiwan     |
|Thailand     |
|United States     |
|United Kingdom|
||

## Related topics

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
