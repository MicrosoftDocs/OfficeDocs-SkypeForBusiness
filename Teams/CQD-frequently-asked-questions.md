---
title: Call Quality Dashboard (CQD) Frequently asked questions (FAQ)
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords: 
  - NOCSH
ms.custom: 
  - Reporting
  - seo-marvel-apr2020
description: Read frequently asked questions (FAQ) and answers about Microsoft Teams Call Quality Dashboard (CQD).
---

# Call Quality Dashboard (CQD) Frequently asked questions (FAQ)

## Frequently asked questions

[Why does CQD mark a call as "Good" if one or more meeting participants had a poor experience?](#why-does-cqd-mark-a-call-as-good-if-one-or-more-meeting-participants-had-a-poor-experience)

[Why do I see up to 0.2% difference in call and user count values on measures and how to get most accurate volumes? ](#why-do-i-see-up-to-02-difference-in-call-and-user-count-values-on-measures-and-how-to-get-most-accurate-volumes)

[Why is CQD data from Skype for Business different than CQD data from Teams? ](#why-is-cqd-data-from-skype-for-business-different-than-cqd-data-from-teams)

[Why can't I see EUII in CQD?](#why-cant-i-see-euii-in-cqd)

[Why am I seeing Skype for Business information in CQD when I've filtered for Teams only?](#why-am-i-seeing-skype-for-business-information-in-cqd-when-ive-filtered-for-teams-only)

[Why do my custom reports only return a maximum of 10,000 rows when I know there should be more entries?](#why-do-my-custom-reports-only-return-a-maximum-of-10000-rows-when-i-know-there-should-be-more-entries)

[Why do WiFi VPN connections show as Wired instead of WiFi?](#why-do-wifi-vpn-connections-show-as-wired-instead-of-wifi)

### Why does CQD mark a call as "Good" if one or more meeting participants had a poor experience?

Check out the rules CQD uses for [stream classification](stream-classification-in-call-quality-dashboard.md).
 
For audio streams, any of the 5 classifiers, which are calculated for the average based on the length of the call, could all be within "good" parameters. It doesn't mean the users didn't experience something that contributed to an audio drop out, static, or glitch. 

To determine if it was a network problem, look at the delta between the average values for the session and the max values. Max values are the maximum detected and reported during the session.
 
Here's an example of how to troubleshoot this situation. Let's say you take a network trace during a call and the first 20 minutes there are no lost packets but then you have a gap of 1.5 seconds of packets and then good for the remainder of the call. The average is going to be <10% (0.1) Packet loss even in a Wireshark trace RTP analysis. What was the Max Packet Loss? 1.5 Seconds in a 5-second period would be 30% (0.3). Did that occur within the five second sampling period (maybe or it could be split over the sampling period)?
 
If network metrics look good in the averages and max values, then look to other telemetry data: 
- Check CPU Insufficient Event Ratio to see if the detected CPU resources available were insufficient and caused poor quality. 
- Was the audio device in Half Duplex mode to prevent feedback due to microphones that are to close to speakers? 
- Check the Device Half Duplex AEC Event Ratio. Was the device glitching or the microphone glitching introducing noise or static due to USB Audio Drop outs when plugged into a Hub or Docking Station:  
- Check the Device Glitches and Microphone glitches event ratios. Was the device itself functioning properly?  
- Check the Capture and Render Device Not Functioning Event Ratios.


For more on dimensions and measures available in CQD telemetry, read [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md).

For background noise, check mute event ratio to see the length of time participants were muted.
 
Create detailed reports in CQD and filter on Meeting ID to look at all users and streams in a meeting and add the fields you are interested in. A user reporting the issue may not be the one that was having the issue. They are just reporting the experience.
 
The telemetry will not necessarily call out the issue, but it can help you better understand where to look and inform your decisions. Is it network, device, driver or firmware updates, usage, or user?

### Why do I see up to 0.2% difference in call and user count values on measures and how to get most accurate volumes? 
To compute call count and user count measures, a distinct countif operation is performed against the call or user identifiers in the data set. On large data sets, there is an up to 0.2% error inherent with the distinct countif operation. For the most accurate volume, you should rely on stream count measures since they do not rely on this distinct countif operation. Filtering to reduce the data volume may reduce the error but may not eliminate this source of error in distinct call and user counts. Refer to [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md) for which measures are impacted.


### Why is CQD data from Skype for Business different than CQD data from Teams? 


> [!IMPORTANT]
> As of July 1, 2020, the older CQD (CQD.lync.com) uses data from the latest CQD (CQD.Teams.microsoft.com). The older CQD data is no longer available, and you can't export your building or report data. You can still use CQD.lync.com (available from the Skype for Business admin center), but we'll turn off access to CQD.lync.com soon, so you should move to CQD.Teams.microsoft.com if you haven't already done so.


If you're trying to compare data between the older CQD from the Skype for Business legacy portal (cqd.lync.com) and the latest CQD from the Teams admin center (cqd.teams.microsoft.com), you'll quickly notice that the data doesn't match. That's because the latest CQD reports on many additional calling scenarios. If you're still using reports from the older CQD, use this article to help you interpret those reports: [Call Quality Dashboard for Skype for Business Server](https://docs.microsoft.com/skypeforbusiness/management-tools/call-quality-dashboard/call-quality-dashboard).


  
### Why can't I see EUII in CQD?

These admin roles can access CQD, but they can't view EUII (end-user identifiable information):
- Microsoft 365 Reports Reader
- Teams Communications Support Specialist

To learn more about roles that can access CQD - including EUII - read [Assign roles for accessing CQD](turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd).

### Why am I seeing Skype for Business information in CQD when I've filtered for Teams only?

When you filter for Teams only in CQD reports (isTeams = 1), you're filtering for all calls where the *first endpoint* is Teams. If the *second endpoint* is Skype for Business, that information will show up in your CQD report.

CQDv2 and CQDv3 will always have different total counts since CQDv3 will have new scenarios that CQDv2 will not have. That’s why comparing Summary Total or Aggregated all-up numbers with no filters will have these expected differences.  

Depending on Customers’ scenario, CQDv3 will include SFB 2019 on-premises calls (if SFB 2019 is used with a data connector), Skype Bot calls (AA, CVI, VDI), Live Events and PSTN calls. Scenarios/Features which are available for the customers, but their data are not in CQD V2.

For instance, it is expected that your customers and you will see 200,000 audio streams, with 5000 failures in CQD V2 Summary Report; versus 300,000 audio streams with 5500 failures (coming from 2019 on-prem calls, CVI calls, PSTN calls etc) in CQD V3.

In order to determine, if there are any unexpected differences, you must look at various breakdowns of the overall data.  Compare with intent.  Slicing the data by User Agent Category Pair is one of the first things we recommend.  *First Product* and *Second Product* are also good slicers.  

### Why do my custom reports only return a maximum of 10,000 rows when I know there should be more entries?

CQD is designed for summarized data queries, and is not designed for data export. We recommend restructuring your reports, where possible, to prevent the 10,000 row limit from being exceeded. Start by looking at your KPIs using broader, lower-cardinality dimensions, such as Month, Year, Date, Region, Country, etc. From there, you can drill down into increasingly higher-cardinality dimensions. The Helpdesk and Location-Enhanced Reports both provide good examples of this drill down workflow.

### Why do WiFi VPN connections show as Wired instead of WiFi?

This is expected.  The VPN vendor created a virtual ethernet adapter which is treated like a wired connection.  Since it's not properly labeled, the operating system doesn't know it's a WiFi connection and reports it as wired.

## Related topics

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Set up Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](CQD-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)

[Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)
