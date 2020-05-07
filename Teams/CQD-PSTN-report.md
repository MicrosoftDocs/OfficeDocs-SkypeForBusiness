---
title: "Using the CQD PSTN Direct Routing Report"
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: siunies
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
description: "Use the CQD PSTN Direct Routing report to monitor and troubleshoot PSTN calling in Microsoft Teams."
---

# Using the CQD PSTN Direct Routing Report

New in March 2020, we've added a CQD PSTN Direct Routing Report to our downloadable [Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). 


The CQD PSTN Direct Routing Report helps customers to understand the usage patterns and quality of their PSTN services monitor information about your SBC, the telephony service, the network parameters, and Network Effectiveness Ratio details and usage of the service. This information can help you identify issues, including the reason for dropped calls. For example, you will be able to know when volume drops, how many calls get affected by what reason.

The CQD PSTN Direct Routing Report has four sections:

  - [PSTN Overview](#pstn-overview)

  - [Service Details](#service-details)

  - [Network Effectiveness Ratio](#network-effectiveness-ratio)

  - [Network Parameters](#network-parameters)

## PSTN Overview

The CQD PSTN Direct Routing Report provides the following information related to overall health of the service for the past 180 days.
![Screenshot: PSTN CQD report](media/CQD-PSTN-report1.png)

For example, if you are interested in the overall usage and health about all inbound calls going through SBC abc.bca.adatum.biz with US as the internal country:

| **Call Out** | **Description**                                                                                                                                                 |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1            | You can use the filters at the top to drill down and select ByotIn as call type, abc.bca.contoso.com as Session Boarder Controller, and US as internal country. |
| 2            | Usage trend for the past 180 days. You can find usage detail report on Service Detail page.                                                                     |
| 3            | Post Dial Delay, Latency, Jitter, and Packet Loss trend for the past 180 days. You can find detail report on Network Parameters page.                           |
| 4            | Concurrent Call and Daily Active User trend for the past 180 days. This chart can help you understand the max volume of the service.                            |
| 5            | Top Call End Reason affected service quality for the past 180 days. You can find service health detail on Network Effective Ratio(NER) page.                    |

## Service Details

This page provides service usage trends per day and user feedback breakdown by geographic.

  - **Total Attempt Calls –** Total attempt calls in that time range, including both success and failed calls

  - **Total Connected Calls -** Total connected calls in that time range

  - **Total Minutes –** Total minute usage in that time range

  - **Daily Active Users(DAU) –** Count of daily active user who made at least one connected call in that day

  - **Concurrent Calls –** Max of simultaneous active calls in a minute

  - **User Feedback –** "Rate My Call" score comes from the user. 3-5 is considered as a good call. 1-2 is considered as a bad call.

![Screenshot: PSTN CQD report](media/CQD-PSTN-report2.png)

For example:

1.  If you see average call duration drops to 0 at 02/14/2020, you can first check if the call volume looks normal and see if there is a big discrepancy between total connect calls and total attempt calls. Then go to Network Effectiveness Ratio page to invest on call failure reasons.

2.  If you see increasing red spots on the user feedback map, you could go to Network Effectiveness Ratio page and Network Parameter to see if there are any anomalies and you could raise a ticket using MS Service Desk.

## Network Effectiveness Ratio

This is the same metric that appears on the Overall Health dashboard. You can check hourly NER number with affected calls detail for both call directions (inbound/outbound) on the Hourly network effectiveness ratio and call ending reason chart below.

  - **NER** - The ability (%) of a network to deliver calls by measuring the number of calls sent versus the number of calls delivered to a recipient.

  - **SIP response code**- A three-digit integer response code shows the call status.

  - **Microsoft response code**-A response code sent out from Microsoft component.

  - **Description** – The reason phase that corresponding to the SIP response code and Microsoft response code.

  - **Number of calls affected** – The total number of calls got affected during the selected time range.

> ![Screenshot: PSTN CQD report](media/CQD-PSTN-report3.png)
> 
For example:

![Screenshot: PSTN CQD report](media/CQD-PSTN-report4.png)

If Daily NER has a dip on 02/05/2020, you can click on the date and other charts will zoom to that specific date.

![Screenshot: PSTN CQD report](media/CQD-PSTN-report5.png)

From the NER Good Percentage Hourly Trend, you can find the dip happens around 21:00. Then click again to zoom to hour 21 and check Effected Call Details to see how many calls failed in that hour and what are the call end reasons. You can start with self-trouble shooting on any SBC problems or report to Service Desk if the problem is not related to SBC.

## Network Parameters

All network parameters are measured from the Direct Routing interface to the Session Border Controller. For information about the recommended values, see [Prepare your organization's network for Microsoft Teams](prepare-network.md), and look at the Customer Edge to Microsoft Edge recommended values.

  - **Jitter** – Is the millisecond measure of variation in network propagation delay time computed between two endpoints using RTCP (The RTP Control Protocol).

  - **Packet Loss** – Is a measure of packet that failed to arrive; it is computed between two endpoints.

  - **Latency** - (Also known as round trip time) is the length of time it takes for a signal to be sent plus the length of time it takes for the acknowledgment of that signal to be received. This time delay consists of the propagation times between the two points of a signal.

> ![Screenshot: PSTN CQD report](media/CQD-PSTN-report6.png)

For example:

If you see a spike on any of the four charts (Latency, Jitter, Package Loss Rate, Post Dial Delay) for a specific date, for example, Latency on 02/14/2020, click on the date point. And the hourly trend chart at the bottom will refresh to show the hourly number. You can check the SBCs or raise a ticket with MS Service Desk.

![Screenshot: PSTN CQD report](media/CQD-PSTN-report7.png)



## Related topics

[Use Power BI to analyze CQD data for Microsoft Teams](CQD-PSTN-report.md)