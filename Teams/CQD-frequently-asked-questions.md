---
title: Call Quality Dashboard (CQD) Frequently asked questions (FAQ)
author: CarolynRowe
ms.author: crowe
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
ms.localizationpriority: medium
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

[Why can't I see EUII in CQD?](#why-cant-i-see-euii-in-cqd)

[I'm trying to use CQD for usage-type reports and find that some of the data is incomplete -- why is that?](#im-trying-to-use-cqd-for-usage-type-reports-and-find-that-some-of-the-data-is-incomplete----why-is-that)

[Why am I seeing Skype for Business information in CQD when I've filtered for Teams only?](#why-am-i-seeing-skype-for-business-information-in-cqd-when-ive-filtered-for-teams-only)

[Why do my custom reports only return a maximum of 10,000 rows when I know there should be more entries?](#why-do-my-custom-reports-only-return-a-maximum-of-10000-rows-when-i-know-there-should-be-more-entries)

[Why do Wi-Fi VPN connections show as Wired instead of Wi-Fi?](#why-do-wi-fi-vpn-connections-show-as-wired-instead-of-wi-fi)

[I turned on Policy-based Recording in Teams and now Peer-to-Peer calls are being marked as Conferences -- what happened?](#i-turned-on-policy-based-recording-in-teams-and-now-peer-to-peer-calls-are-being-marked-as-conferences----what-happened)

### Why does CQD mark a call as "Good" if one or more meeting participants had a poor experience?

Check out the rules CQD uses for [stream classification](stream-classification-in-call-quality-dashboard.md).
 
For audio streams, any of the five classifiers (which are calculated for the average based on the length of the call) could all be within "good" parameters. It doesn't mean the users didn't experience something that contributed to an audio drop out, static, or glitch. 

To determine if it was a network problem, look at the delta between the average values for the session and the max values. Max values are the maximum detected and reported during the session.
 
Here's an example of how to troubleshoot this situation. Let's say you take a network trace during a call and the first 20 minutes there are no lost packets but then you have a gap of 1.5 seconds of packets and then good for the remainder of the call. The average is going to be <10% (0.1) Packet loss even in a Wireshark trace RTP analysis. What was the Max Packet Loss? 1.5 Seconds in a 5-second period would be 30% (0.3). Did that occur within the 5-second sampling period (maybe or it could be split over the sampling period)?
 
If network metrics look good in the averages and max values, then look to other telemetry data: 
- Check CPU Insufficient Event Ratio to see if the detected CPU resources available were insufficient and caused poor quality. 
- Was the audio device in Half Duplex mode to prevent feedback because of microphones that are too close to speakers? 
- Check the Device Half Duplex AEC Event Ratio. Was glitching from a device, such as a microphone, introducing noise or static because of USB Audio drop outs when plugged into a Hub or Docking Station?  
- Check the Device Glitches and Microphone glitches event ratios. Was the device itself functioning properly?  
- Check the Capture and Render Device Not Functioning Event Ratios.


For more on dimensions and measures available in CQD telemetry, read [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md).

For background noise, check mute event ratio to see the length of time participants were muted.
 
Create detailed reports in CQD and filter on Meeting ID to look at all users and streams in a meeting and add the fields you're interested in. A user reporting the issue may not be the one that was having the issue. They are just reporting the experience.
 
The telemetry won't necessarily call out the issue, but it can help you better understand where to look and inform your decisions. Is it network, device, driver or firmware updates, usage, or user?

### Why do I see up to 0.2% difference in call and user count values on measures and how to get most accurate volumes? 

To compute call count and user count measures, a distinct countif operation is performed against the call or user identifiers in the data set. On large data sets, there's an up to 0.2% error inherent with the distinct countif operation. For the most accurate volume, you should rely on stream count measures since they don't rely on this distinct countif operation. Filtering to reduce the data volume may reduce the error but may not eliminate this source of error in distinct call and user counts. Refer to [Dimensions and measurements available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md) for which measures are affected.

  
### Why can't I see EUII in CQD?

These admin roles can access CQD, but they can't view EUII (end-user identifiable information):

- Microsoft 365 Reports Reader
- Teams Communications Support Specialist

To learn more about roles that can access CQD - including EUII - read [Assign roles for accessing CQD](turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd).

### I'm trying to use CQD for usage-type reports and find that some of the data is incomplete -- why is that?

Call quality management tools like CQD, Call Analytics, CallRecord Graph API, and Real-time Analytics are based on diagnostic telemetry. The information we show in Teams call quality management tools is only as complete as the telemetry data we receive from clients participating in a call. There are several reasons why we may not receive complete telemetry such as network outages, or [firewall or proxy misconfigurations](/microsoft-365/enterprise/urls-and-ip-address-ranges). We're continuing to work to improve the reliability and resiliency with which Teams clients deliver telemetry to the service.

With that in mind, we don't support the use of call quality management tools for usage reporting. They aren't designed to accommodate nor intended for these types of reporting scenarios, and many usage statistics are not and will not be available within these tools. Teams Admin Center offers a series of [Usage Reports](teams-analytics-and-reports/teams-reporting-reference.md), and a [Meeting Attendance Report](teams-analytics-and-reports/meeting-attendance-report.md) is available directly from the Teams client.

### Why am I seeing Skype for Business information in CQD when I've filtered for Teams only?

When you filter for Teams only in CQD reports (isTeams = 1), you're filtering for all calls where the *first endpoint* is Teams. If the *second endpoint* is Skype for Business, that information will show up in your CQD report. Depending on customers’ scenarios, CQD may include Skype for Business Server 2019 calls when [Call Data Connector](/skypeforbusiness/hybrid/plan-call-data-connector) is configured. It may also include Skype Bot calls (AA, CVI, VDI), Live Events, and PSTN calls.

It's possible to remove Skype for Business information from your queries by filtering on dimensions such as *First User Agent Category* and *Second User Agent Category*. You can also use *User Agent Category Pair* which combines the First and Second dimensions into a single filter.

### Why do my custom reports only return a maximum of 10,000 rows when I know there should be more entries?

CQD is designed for summarized data queries, and isn't designed for data export. We recommend restructuring your reports, where possible, to prevent the 10,000 row limit from being exceeded. Start by looking at your KPIs using broader, lower-cardinality dimensions, such as Month, Year, Date, Region, Country, and so on. From there, you can drill down into increasingly higher-cardinality dimensions. The Helpdesk and Location-Enhanced Reports both provide good examples of this drill down workflow.

### Why do Wi-Fi VPN connections show as Wired instead of Wi-Fi?

This is expected behavior. The VPN vendor created a virtual ethernet adapter that is treated like a wired connection. Since it's not properly labeled, the operating system doesn't know it's a Wi-Fi connection and reports it as wired.

### I turned on Policy-based Recording in Teams and now Peer-to-Peer calls are being marked as Conferences -- what happened?

This is expected behavior when Policy-based Recording is enabled in Microsoft Teams. Policy-based Recording uses a Teams Recorder Bot deployed in Microsoft Azure to capture meeting contents for compliance purposes. In call quality management, "peer-to-peer" is a description of the flow of media traffic, not the interaction between the users. Because a Recorder Bot is itself a party to the call, the call is no longer peer-to-peer, but a multi-party call. Multi-party calls are classified as Conferences by Microsoft Teams, and so they'll be indicated as such when you view these calls in CQD and other call quality tools.

## Related articles

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Set up Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](CQD-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
