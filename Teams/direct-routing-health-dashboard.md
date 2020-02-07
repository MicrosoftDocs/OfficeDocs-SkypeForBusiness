---
title: "Health Dashboard for Direct Routing"
ms.reviewer: nmurav
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
description: "Learn how to use Health Dashboard to monitor the connection between your Session Border Controller and Direct Routing."
---

# Health Dashboard for Direct Routing

Health Dashboard for Direct Routing lets you monitor the connection between your Session Border Controller (SBC) and the Direct Routing interface. With Health Dashboard, you can monitor information about your SBC, the telephony service, the network parameters and Network Effectiveness Ratio details between your SBC and the Direct Routing interface. This information can help you identify issues, including the reason for dropped calls. For example, the SBC might stop sending calls if a certificate on the SBC has expired or if there are network issues.

Health Dashboard monitors two levels of information:
    •	Overall health of the connected SBCs
    •	Detailed information about the connected SBCs

You can view Health Dashboard in the Microsoft Teams and Skype for Business Admin Center under Voice -> Direct Routing.



## Overall health

Health Dashboard provides the following information related to overall health of the connected SBCs:

 ![Shows Health Dashboard statistics](media/SBCoverview.png)
 
 And it also provides geographic information related to overall health of the connected SBCs. (click the globe icon on the top right of the SBC list table):
 
 ![Shows Health Dashboard map view](media/map_overview.png)

- **Direct Routing summary** - Shows the total number of SBCs registered in the system. Registration means that the tenant administrator added an SBC by using the New-CsOnlinePSTNGateway command. If the SBC was added in PowerShell, but never connected, the Health Dashboard shows it in an unhealthy status.

- **SBC** - The FQDN of the paired SBC.

- **Network Effectiveness Ratio (NER)** - The NER measures the ability of a network to deliver calls by measuring the number of calls sent versus the number of calls delivered to a recipient.  

   The NER measures the ability of networks to deliver calls to the far-end terminal--excluding user actions resulting in call rejections.  If the recipient rejected a call or sent the call to voicemail, the call is counted as a successful delivery. This means that an answer message, a busy signal, or a ring with no answer are all considered successful calls. 
  
   For example, assume Direct Routing sent a call to the SBC and the SBC returns SIP code “504 Server Time-out - The server attempted to access another server in attempting to process the request and did not receive a prompt response”. This response indicates there is an issue on the SBC side, and this will decrease the NER on the Health Dashboard for this SBC. 
  
   Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter. If the number of calls is less than 100, the NER might be quite low, but still be normal. 

   The formula used to calculate NER is:

   NER = (Answered calls + User Busy + Ring no Answer + Terminal Reject Seizures)/Total Attempt Calls x 100

 
- **Average call duration** - Information about average call duration can help you monitor the quality of calls. The average duration of a 1:1 PSTN call is four to five minutes. However, for each company, this average can differ. Microsoft recommends establishing a baseline for the average call duration for your company. If this parameter goes significantly below the baseline, it might indicate that your users are having issues with call quality or reliability and are hanging up earlier than usual. If you start seeing extremely low average call duration, for example 15 seconds, callers might be hanging up because your service is not performing reliably. 

   Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter.

- **TLS connectivity status** - TLS (Transport Layer Security) connectivity shows the status of the TLS connections between Direct Routing and the SBC. Health Dashboard also analyzes the certificate expiration date and warns if a certificate is set to expire within 30 days so that administrators can renew the certificate before service is disrupted.

   By clicking the Warning message, you can see a detailed issue description in a popup window on the right and recommendations for how to fix the issue.

- **SIP options status** – By default, the SBC sends options messages every minute. This configuration can vary for different SBC vendors. Direct Routing warns if the SIP options are not sent or are not configured. For more information about SIP options monitoring, and conditions when an SBC can be marked as not functional, see [Monitor and troubleshoot Direct Routing](direct-routing-monitor-and-troubleshoot.md).

- **Detailed SIP options status** - In addition to showing that there is an issue with SIP options flow, the Health Dashboard also provides detailed descriptions of the errors. You can access the description by clicking the “Warning” message. A pop-up window on the right will show the detailed error description.

   Possible values for SIP options status messages are as follows:

    - Active – The SBC is active--Microsoft Direct Routing service sees the options flowing on a regular interval.

    - Warning, no SIP options - The Session Border Controller exists in the database (your administrator created it using the command New-CsOnlinePSTNGateway). It is configured to send SIP options, but the Direct Routing service never saw the SIP options coming back from this SBC.

    - Warning, SIP Messages aren't configured - Trunk monitoring using SIP options isn’t turned on. Microsoft Calling System uses SIP options and Transport Layer Security (TLS) handshake monitoring to detect the health of the connected Session Border Controllers (SBCs) at the application level. You’ll have problems if this trunk can be reached at the network level (by ping), but the certificate has expired or the SIP stack doesn’t work. To help identify such problems early, Microsoft recommends enabling sending SIP options. Check your SBC manufacturer documentation to configure sending SIP options. 

- **Concurrent calls capacity** - You can specify the limit of concurrent calls that an SBC can handle by using the New- or Set-CsOnlinePSTNGateway command with the -MaxConcurrentSessions parameter. This parameter calculates how many calls were sent or received by Direct Routing using a specific SBC and compares it with the limit set. Note:  If the SBC also handles calls to different PBXs, this number will not show the actual concurrent calls.

- **Enabled** - You can enable or disable individual SBCs using the button.


## Detailed information for each SBC

You can also view the detailed information for a specific SBC as shown in the following screenshot:

![Health dashboard SBC details](media/SBCdetail.png)

- **Status** – overall status of the SBC, based on all monitored parameters.
- **SBC sugnaling port** – he unique UDP/TCP port assigned to this SBC.
- **SIP options status** – the same metric as on the “Overall Health” page.
- **TLS connectivity status** –  this is the same metric as on the “Overall Health” page.
- **Average call duration(call count)** –  this is the average call duration for the total call count in minutes.
- **Network effectiveness ratio(NER)** – This is the same parameter that appears on the Overall Health dashboard. You can slide the data by number of days and check hourly NER number with affected calls summery for both call directions (inbound/outbound) on the Hourly network effectiveness ratio and call ending reason chart below.

If you want to investigate on affected calls, please go to Analytics & reports -> Usage reports to download detail call record. With the information, you can start with self-troubleshooting and report to Microsoft Service Desk.  

   - SIP response code- A three-digit integer response code shows the call status.
   - Microsoft response code-A response code sent out from Microsoft component.
   - Description – The reason phase that corresponding to the SIP response code and Microsoft response code.
   - Number of calls affected – The total number of calls got affected during the selected period.

For example:

![Health dashboard NER details](media/NERdetail.png)

The detailed view also shows the following additional parameters:

- **Concurrent call**- shows  how many concurrent calls the SBC handled. This information is useful to predict the number of concurrent channels you need and see the trend. You can slide the data by number of days and call direction (inbound/outbound/All streams).

  You can slide the data by number of days on the Network parameters chart below.

  For example:

![Health dashboard concurrent call details](media/concurrent_calls.png)

- **Network parameters** - All network parameters are measured from the Direct Routing interface to the Session Border Controller. For information about the recommended values, see [Prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/prepare-network), and look at the Customer Edge to Microsoft Edge recommended values.

   - Jitter – Is the millisecond measure of variation in network propagation delay time computed between two endpoints using RTCP (The RTP Control Protocol).

   - Packet Loss – Is a measure of packet that failed to arrive; it is computed between two endpoints.

   - Latency - (Also known as round trip time) is the length of time it takes for a signal to be sent plus the length of time it takes for the acknowledgment of that signal to be received. This time delay consists of the propagation times between the two points of a signal.

   You can slide the data by number of days and call direction (inbound/outbound/All streams).

  For example:

![Health dashboard network parameters details](media/Network_parameters.png)

