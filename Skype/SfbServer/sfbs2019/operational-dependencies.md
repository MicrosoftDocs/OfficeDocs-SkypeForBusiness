---
title: "Operational dependencies in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 5/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 450b6be2-7fb3-47d7-8b0b-c05faa331e14
description: "The Reference Architecture discussed in this document will help ensure that you have a Lync Server 2013 deployment that not only scales to the organization's requirements but is architected as per Microsoft best practices. Be that as it may the Lync Server 2013 implementation is a dynamic service and like any other service in the enterprise still requires monitoring and proactive management to maintain high level of service availability and service quality to the business."
---

# Operational dependencies in Lync Server 2013
[]
The Reference Architecture discussed in this document will help ensure that you have a Lync Server 2013 deployment that not only scales to the organization's requirements but is architected as per Microsoft best practices. Be that as it may the Lync Server 2013 implementation is a dynamic service and like any other service in the enterprise still requires monitoring and proactive management to maintain high level of service availability and service quality to the business. 
  
As Lync Server 2013 becomes deeply ingrained in the organization's everyday business it is important that the service be managed by accurate and tangible service level management. The Lync system architecture can become complex and very integrated and in order to maintain effective service level management and establish SLAs for Lync Server 2013 it becomes critical to understand the system's dependencies on other platforms and servers. Equally important is to note which business services, such as voice and UC integrated applications, become dependent on Lync. 
  
 Lync Server 2013 must be established noting all the said dependencies. The service map will allow you to formulate a SLA between Lync and its dependent service and provide a starting place for SLA negotiation. 
  
The following table lists the typical dependency services for a Lync infrastructure. Each of these technologies should have its own proactive monitoring.
  
**Typical dependency services**

|**Dependency Service**||
|:-----|:-----|
|Operating systems  <br/> ||
|Server Hardware  <br/> ||
|Active Directory  <br/> ||
|Public Key Infrastructure  <br/> ||
|Domain Naming Service  <br/> ||
|Database Services  <br/> ||
|Storage Services  <br/> ||
|System Management - Monitoring and distribution  <br/> ||
|Security Services - Antivirus  <br/> ||
|Network Infrastructure - Internet  <br/> ||
|Network Infrastructure - Internal (LAN/WAN)  <br/> ||
|Telephony Infrastructure - IP-PBX and Gateways  <br/> ||
|Cloud Services  <br/> ||
   
It is assumed that the organization is operationally mature in exercising basic service level management functions such as change, incident and release management as prescribed by the MOF. The Lync solution should be adopted by these functions and become subject to the same operational management processes.
  
Building on the information obtained above we now have a greater understanding of what can impact the Lync service in the enterprise. To help ensure Lync Server 2013 service availability and quality, the following monitoring tools must accompany the reference architecture deployment:
  
**Monitoring tools**

|**Component**|**Description**|**Applicable Site**|
|:-----|:-----|:-----|
|Lync Server 2013 Monitoring Server  <br/> |Deploy at least one Lync Server 2013 Monitoring Server role per Central site and configure Quality of Experience (QoE) Reporting Pack.  <br/> Refer to the Lync Server 2013 Deployment documentation for further details:  <br/> [Deploying monitoring in Lync Server 2013](deploying-monitoring.md) <br/> |Central sites  <br/> |
||Tether each pool to its nearest instance of the Monitoring Server role.  <br/> |Central sites  <br/> Branch sites  <br/> |
|System Center Operations Manager 2012  <br/> |System Center Operations Manager 2012 with the Microsoft Lync Server 2013 Management Pack (MP) imported.  <br/> The Management Pack implements traditional Event Log and Performance counter based instrumentation is utilized as well as enabling newly available instrumentation in Lync Server 2013.  <br/> |Central sites  <br/> |
||Make sure that Central Discovery to discovery of roles and components that need to be monitored are automatically completed based on a central discovery script that reads the topology document published in Central Management Database.  <br/> |Central Site  <br/> Branch Site  <br/> Edge Site  <br/> |
||Deploy System Centre Operations Manager 2007 agents to all deployed servers running Lync Server.  <br/> |Central Site  <br/> Branch Site  <br/> Edge Site  <br/> |
||Make sure Prioritized Alerts are configured for notification:  <br/> High Priority Alerts  <br/> Medium Priority Alerts  <br/> Other Alerts.  <br/> |Central Site  <br/> Branch Site  <br/> Edge Site  <br/> |
||Configure Port monitoring for your deployment.  <br/> |Central Site  <br/> Branch Site  <br/> Edge Site  <br/> |
||Configure URL monitoring for your deployment  <br/> |Central Site  <br/> |
|Lync and System Center Operations Manager integration  <br/> |Deploy Call Reliability and Media Quality MonitoringCall reliability and media quality monitoring use the Monitoring Server computer as their watcher node to monitor call reliability and media quality of Lync Server. Both of these features query the Monitoring Server databases to do analysis.  <br/> |Central Site  <br/> Branch Site  <br/> |
||Ensure Media Quality warning thresholds are accurately configured. The following table indicates the maximum Network Mean Opinion Scores by Codec. In production these scores should be monitored for a set period and acceptable thresholds must be established based on the organization specific NMOS scores.  <br/> |Central Site  <br/> Branch Site  <br/> |
|Lync Server 2013 Synthetic Transaction Watcher  <br/> |Deploy a dedicated Lync Server to be a synthetic transaction watcher.  <br/> Synthetic transactions are Lync Server 2013 Windows PowerShell cmdlets that are automatically triggered by the management pack on a predefined interval. These are executed on a synthetic transaction watcher node which is an administrator designated server responsible for discovery and execution of STs for each pool.  <br/> We do not recommend that you use an existing Microsoft Lync Server 2013 server as a synthetic transaction watcher node. This is due to the high CPU/memory usage requirements for running STs. Use a new server computer (or a virtual server) for the synthetic transaction watcher node.  <br/> |Central Site  <br/> |
||Deploying synthetic transactions watcher node.  <br/> Refer to the MonitoringCS_withSCOM.docx document from UCTAP connect documentation.  <br/> |Central Site  <br/> |
   
**Maximum Network MOS scores per codec**

|**Scenario**|**Codec**|**Max NMOS**|
|:-----|:-----|:-----|
|UC-UC call  <br/> |RTAudio WB  <br/> |4.10  <br/> |
|UC-UC call  <br/> |RTAudio NB  <br/> |2.95  <br/> |
|Conference call  <br/> |Siren  <br/> |3.72  <br/> |
|UC-PSTN call  <br/> |RTAudio NB  <br/> |2.95  <br/> |
|UC-PSTN call  <br/> |G-711  <br/> |3.61  <br/> |
   
Over and above the previous pro-active monitoring activities, maintenance tasks should be executed for Central, Edge and Branch sites on a recurring daily, weekly and monthly basis as defined in the Lync RA Operations Guide.
  

