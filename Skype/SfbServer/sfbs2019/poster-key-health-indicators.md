---
title: "Key Health Indicators in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8367dccf-adaa-4a0b-a4ed-bc9570cc5e24
description: "In this articleWhat are Key Health Indicators?To Collect KHI DataRemediation Flow for all Server RolesGlossaryFront-end ServersBackend SQL ServersMediation ServersEdge Servers"
---

# Key Health Indicators in Lync Server 2013
[]
 **In this article**
  
[What are Key Health Indicators?](#WhatIs)
  
[To Collect KHI Data](#ToCollect)
  
[Remediation Flow for all Server Roles](#Remidiation)
  
[Glossary](#Glossary)
  
[Front-end Servers](#Front)
  
[Backend SQL Servers](#BackEnd)
  
[Mediation Servers](#Mediation)
  
[Edge Servers](#Edge)
  
This article is a companion to the [Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers](https://go.microsoft.com/fwlink/?LinkId=391838) poster, which you can download from the Download Center. 
  
![Poster describing troubleshooting using KHI data](media/KHI-final.jpg)
  
You can use this poster to learn about Key Health Indicators (KHIs), performance counters with thresholds aimed at revealing user experience issues. Gathering KHI data is usually the first step to implementing the Call Quality Methodology (CQM), which is focused on ensuring a quality audio experience for Lync users.
  
If you have questions about how to use CQM, you can submit your questions to cqmfeedback@microsoft.com.
  
The poster explains the following areas:
  
- [What are Key Health Indicators?](poster-key-health-indicators.md#WhatIs)
    
- [To Collect KHI Data](poster-key-health-indicators.md#ToCollect)
    
- [Remediation Flow for all Server Roles](poster-key-health-indicators.md#Remidiation)
    
- [Glossary](poster-key-health-indicators.md#Glossary)
    
- [Front-end Servers](poster-key-health-indicators.md#Front)
    
- [Backend SQL Servers](poster-key-health-indicators.md#BackEnd)
    
- [Mediation Servers](poster-key-health-indicators.md#Mediation)
    
- [Edge Servers](poster-key-health-indicators.md#Edge)
    
## What are Key Health Indicators?
<a name="WhatIs"> </a>

Key Health Indicators are performance counters with thresholds aimed at revealing user experience issues. Gathering KHI data is usually the first step to implementing the Call Quality Methodology (CQM), which is focused on ensuring a quality audio experience for Lync users. 
  
KHIs are used in addition to standard Lync Monitoring Solutions (e.g. System Center Operations Manager, Synthetic Transactions, Monitoring Server) and not instead of those solutions. 
  
Collect the KHI performance counters and populate the KHI spreadsheet accompanying the Networking Guide to produce a scorecard that will help you determine the server health of a Lync deployment. Once populated, it guides you in repairing the environment and gives additional insight to other stakeholders. Evaluate KHIs on a monthly basis and incorporate them into any deployment's ongoing operational processes. 
  
Download the [Lync Server Networking Guide](https://go.microsoft.com/fwlink/p/?LinkID=390677) to see the full list of KHIs and to get the related spreadsheets. 
  
## To Collect KHI Data
<a name="ToCollect"> </a>

1. Run the KHI script included with the Lync Server Networking Guide on each Lync Server. This will create a Data Collector inside of Performance Monitor and name it KHI. By default, data will be polled every 15 seconds.
    
2. Before the start of your company's business day, go to each Lync Server and start the KHI Data Collector. 
    
3. At the end of that day, stop the KHI Data Collector and copy the data to a central location.
    
4. After using Performance Monitor to fill in the KHI spreadsheet included with the Lync Server Networking Guide download, compare the results to the recommended targets.
    
## Remediation Flow for all Server Roles
<a name="Remidiation"> </a>

For each server in your Lync implementation, begin by verifying that the server's component health and system performance is at or above the desired level. Only after that should you look at the indicators relating to the server's role in the overall Lync implementation.
  
Begin by collecting KHI  Performance Data for all servers. For each of the system roles (details discussed later in this document) determine whether the basic system components meet the recommended targets. If they do not, remediate the system performance then re-collect KHI data and ensure system health before looking at the metrics specific to the server's role in the Lync implementation. Component health for all roles is defined as:
  
- CPU Utilization \< 80%
    
- Avg. Disk Write \< 10 ms
    
- Avg. Disk Read \< 10 ms
    
- Available memory  \>20% System Total MB
    
- Network Queue Length \< 2
    
- Discarded Packets (in / out) = 0
    
## Glossary
<a name="Glossary"> </a>

The following terms and acronyms are used in this poster: 
  
AS MCU = Application Sharing Multi-point Control Unit
  
AV MCU = Audio/Video MCU
  
IM MCU = Instant Messaging MCU
  
UCWA = Unified Communications Web API
  
AV Edge = Traversal of audio/video via edge
  
AV Auth = Audio/Video Authentication
  
SIP Stack = Contains Lync's core SIP implementation
  
Data Proxy = Used for edge conferencing
  
LySS = Lync Storage Service
  
## Front-end Servers
<a name="Front"> </a>

The following recommended KHI targets are specific to front-end servers in addition to basic component health: 
  
****

|**Functional area**|**Target Metrics**|
|:-----|:-----|
|AS/AV/IM MCU  <br/> |MCU Health State \<2  <br/> |
|Web Components  <br/> |Distribution List expansion AD timeouts \<0  <br/> ABWQ failures = 0  <br/> LIS failures = 0  <br/> Authentication Errors \< 1/sec  <br/> ASP.NET v4 Requests Rejected = 0  <br/> |
|SIP Stack  <br/> |Avg. Incoming Message Processing \< 1 sec  <br/> Incoming Responses Dropped \< 1/sec Incoming Requests Dropped \< 1/sec  <br/> Queue Latency \< 100 ms  <br/> Sproc Latency \< 100 ms  <br/> Throttled Requests = 0  <br/> Authentication Errors \< 1/sec  <br/> Incoming Messages Timed Out \< 2  <br/> Avg. Incoming Message Hold \< 1 sec  <br/> Flow Controlled Connections \< 2  <br/> Avg. Out Queue Delay \< 2 sec  <br/> |
|LySS  <br/> |% of space used by Storage Service DB \< 80  <br/> # of replica replication failures = 0  <br/> # of data loss events = 0  <br/> |
|SQL  <br/> |Page life expectancy \> 300 Sec.  <br/> Batch requests / sec \< 2500  <br/> |
   
## Backend SQL Servers
<a name="BackEnd"> </a>

The following recommended KHI targets are specific to SQL servers in addition to basic component health:
  
****

|**Functional area**|**Target Metrics**|
|:-----|:-----|
|SQL  <br/> |Page life expectancy \> 300 Sec.  <br/> Batch requests / sec \< 2500  <br/> |
   
## Mediation Servers
<a name="Mediation"> </a>

The following recommended KHI targets are specific to mediation servers in addition to basic component health:
  
****

|**Functional area**|**Target Metrics**|
|:-----|:-----|
|Mediation Server Service  <br/> |Load Call Failure Index = 0  <br/> Failed Calls due to Proxy \<10  <br/> Failed Calls due to Gateway \<10  <br/> Calls (in or out) rejected = 0  <br/> Media Candidates missing = 0  <br/> Media Connectivity Check Failures = 0  <br/> |
   
## Edge Servers
<a name="Edge"> </a>

The following recommended KHI targets are specific to edge servers in addition to basic component health:
  
****

|**Functional area**|**Target Metrics**|
|:-----|:-----|
|AV Auth  <br/> |Bad Requests \< 20/sec  <br/> |
|AV Edge  <br/> |Auth. Failures \<20/sec  <br/> Allocation Failures \<20/sec  <br/> Packets Dropped \<300/sec  <br/> |
|Data Proxy  <br/> |Throttled Server connections \< 3  <br/> System is Throttling \<1  <br/> |
|SIP Stack  <br/> |Connections over limit dropped \< 1  <br/> Sends timed out \<10  <br/> Flow Controlled Connections \<100  <br/> Incoming requests dropped \< 1/sec  <br/> Avg. Message Processing \< 3 sec  <br/> |
   
## See also
<a name="Edge"> </a>

#### 

[Lync Server Networking Guide](https://go.microsoft.com/fwlink/p/?LinkID=390677)
  
[Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers](https://go.microsoft.com/fwlink/?LinkId=391838)
  
[Lync Call Quality Methodology](https://go.microsoft.com/fwlink/?LinkId=391841)

