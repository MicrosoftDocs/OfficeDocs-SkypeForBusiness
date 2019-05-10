---
title: "Plan for monitoring in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5d5eb658-7fe0-42e6-acaf-700051d0a823
description: "Summary: Review this topic while planning for the monitoring service in Skype for Business Server."
---

# Plan for monitoring in Skype for Business Server

**Summary:** Review this topic while planning for the monitoring service in Skype for Business Server.

The monitoring service in Skype for Business Server provides a way for administrators to collect usage and quality data for the communication sessions that take place in their organization, which allows them to identify trends and problems. Ongoing monitoring of your deployment allows you to catch problems early and keep your organization's users satisfied.

Monitoring in Skype for Business Server does not require a separate server role (as was the case in earlier Lync versions); instead, the monitoring service is built into each Front End server. Monitoring is not enabled by default in Skype for Business Server. This article will help you determine whether to enable Monitoring during or after your initial Skype for Business Server configuration, and what SQL resources you'll need to support Monitoring activities. If you're not sure exactly what is or is not monitored and how monitoring can be helpful, go to [Basics about Monitoring](monitoring.md#Basics). To begin your planning process, go to [Define your requirements for monitoring](monitoring.md#requirements). For more details on the SQL requirements for monitoring, go to [SQL requirements for monitoring](monitoring.md#topologies).

## Basics about Monitoring
<a name="Basics"> </a>

A session is a generic term for a user's connection to a:

- Conference

- Conferencing tool such as Audio/Video or Application Sharing

- Another user via a peer-to-peer conversation such as instant messaging or an audio call

> [!NOTE]
> Skype for Business Server keeps track of information about each session: who called who; which endpoints were used in the session; how long did the session last; what was the perceived quality of the session; and so on. Skype for Business Server does not record and store the actual call itself. That includes instant messaging sessions: although Skype for Business Server records information about instant messaging sessions, it does not maintain a record of each instant message that was sent during the session.

The basic call detail information collected by Skype for Business Server for each session can be used for:

- **Return on Investment (ROI)** analysis. Administrators can compare the usage data to similar data collected for their previous telephony system in order to show cost savings and help justify the deployment of Skype for Business Server.

- **Device Inventory Management**. Asset management information helps administrators identify old devices still in use that need to be replaced, and identify expensive devices that are unused or under-used.

- **Help Desk**. Troubleshooting data helps support engineers determine why a user's call failed, without having to collect server or client side logs. This information can be readily accessed and understood by support personnel who do not have a deep technical knowledge of the Skype for Business client and Skype for Business Server.

- **System Troubleshooting**. Enables administrators to detect major issues that might prevent end users from performing basic tasks like joining a conference, establishing a call, or sending an instant message.

Monitoring also provides a mechanism that allows SIP endpoints (such as Skype for Business) to provide troubleshooting information that the administrator would not otherwise have access to:

- **Media Metrics that Impact Quality**. These metrics deal with the actual transmission of the call itself; they provide a sort of travelogue as the call journeys across the network. These metrics (which include such things as packet loss, jitter, and round trip times) provide information on what happened to the call from the time it left one person's endpoint to the time it arrived at the other person's endpoint.

- **Issues Reported to the End User**. These metrics include poor quality notifications that Skype for Business presents to end users in cases where they are too far from a microphone, speaking too softly, have a poor network connection, or are experiencing poor quality because another program on the computer is consuming the available resources.

- **Environment Information**. These metrics detail call quality factors such as the type of microphone and speakers being used, whether the user is connected through a VPN connection, and whether the user is on a wireless connection.

At the end of each call, SIP-compliant endpoints transmit this information to the Front End server that facilitated the call. You don't have to do anything to get endpoints to transmit that information; that behavior is built into the SIP protocol. However, if you want to collect and store that information, then you need to install and enable monitoring. If you do install and enable monitoring, then call information is gathered by agents running on the Front End server and relayed to a pair of SQL Server databases. The monitoring service (in the form of "unified data collection agents") is collocated into all Front End servers.

## Define your requirements for monitoring
<a name="requirements"> </a>

There are still several key issues that should be addressed before you begin to install and configure monitoring with Skype for Business Server:

 **When do you want to install monitoring?** Monitoring can be installed and configured at the same time you install and configured Skype for Business Server; the Skype for Business Server Deployment Wizard will provide you with the opportunity to associate your Front End pools with a monitoring database during setup. Alternatively, you can install monitoring after Skype for Business Server itself has been installed; this can be done by using Topology Builder to associate your Front End pools and servers with a monitoring database, and then publishing the revised topology.

Keep in mind that SQL Server must be installed and configured before you deploy and configure monitoring. However, you only need to deploy SQL Server itself; the monitoring databases will be created for you when you publish your Skype for Business Server topology.

 **What type of data do you want to monitor?** Skype for Business Server enables you to monitor two general types of data: call detailing recording (CDR) data and Quality of Experience (QoE) data. Call detail recording provides a way for you to track the usage of Skype for Business Server features such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. This information helps you know which Skype for Business Server features are being used (and which ones are not) and also provides information as to when these features are being used. Quality of Experience data allows you to maintain a record of the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay).

If you choose to enable monitoring in Skype for Business Server you can enable both CDR monitoring and QoE monitoring, or you can choose to enable one type of monitoring while leaving the other type disabled. For example, suppose your users only use instant messaging and file transfers, and do not make audio or video calls. In that case, there might be little reason to enable QoE monitoring. Likewise, Skype for Business Server makes it easy to enable and disable monitoring after monitoring has been deployed. For example, you might choose to deploy monitoring but initially leave QoE monitoring disabled. If your users begin to experience problems with audio or video calls you could then enable QoE monitoring and use that data to help you troubleshoot and resolve those problems.

There is no particular advantage (or disadvantage) to installing monitoring at the same time you install Skype for Business Server vs. installing monitoring after Skype for Business Server has been installed. The one point to keep in mind is that, before you install monitoring, you must select a computer to host the backend monitoring store, and a supported version of SQL Server must be installing and configured on that computer before that computer can be used for monitoring. If you have already installed SQL Server on a computer and that computer is ready for use then you can install monitoring at the same time you install Skype for Business Server. If you do not have a backend computer ready then you can proceed to install Skype for Business Server by itself, then install monitoring whenever the backend computer is ready for use.

 **How many backend monitoring databases do you need?** It was estimated that a collocated database for both monitoring and archiving could support 240,000 Skype for Business Server users). In addition, a single monitoring database can be used by multiple Front End pools; if you have three Front End pools in your organization then you could associate all three of those pools with the same backend store.

For many organizations, database capacity will not be the deciding factor when determining the number of backend monitoring databases that will be required. Instead, a more important consideration could be network speed. Suppose you have three Front End pools, but one of those pools is located across a slow network connection. In that case, you might want to use two monitoring databases: one database to service the two pools with the good network connection, and a separate database to service the pool with the slower network connection.

You should also take into account that Skype for Business Server supports the use of mirror databases. "Database mirroring" provides a way for you to simultaneously maintain two copies of a database, with each database residing on a different server. Any time data is written to a primary database that same data is also written to the mirror database. If the primary database should fail or otherwise become unavailable, you can "fail over" to the mirror database by using a simple Skype for Business Server PowerShell command. For example:

```
Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "Monitoring" -NewPrincipal "Mirror"
```

This is important for planning purposes simply because mirroring will require you to double your required number of databases: in addition to each primary database you will need a second database to act as the mirror.

 **Do your Skype for Business Server sites need their own custom monitoring configurations?** When you install Skype for Business Server you also install global collections of CDR and QoE configuration settings; these global collections give you the ability to apply the same CDR and QoE settings to your entire organization. In many cases, this will be sufficient: often-times you will want, say, to have CDR monitoring enabled for all of your users.

However, there might also be times when you want to apply different settings to different sites. For example, perhaps you want to use both CDR and QoE monitoring in your Redmond site, but only use CDR monitoring in your Dublin site. Likewise, you might want to retain monitoring data for 60 days in the Redmond site but only need to maintain this type of data for 30 days in the Dublin site. Skype for Business Server allows you to create separate collections of CDR and QoE configuration settings at the site scope; that enables you to manage each site differently. (This includes both enabling and disabling monitoring as well as configuring management settings such as how long data is to be retained.)

Note that you can make this decision before you deploy monitoring or after you deploy monitoring. For example, you can deploy monitoring and then manage the entire organization by using the global settings. If you later change your mind, you can create a separate collection of settings for, say, the Redmond site, and then use those settings to manage monitoring for Redmond. (Settings applied at the site scope always take precedence over settings applied at the global scope.) If you change your mind again, you can simply delete the configuration settings applied to the Redmond site. When a collection of site settings is removed then the global collection of settings will automatically be applied to that site.

## SQL requirements for monitoring
<a name="topologies"> </a>

The unified data collection agents are automatically installed and activated on each Front End server when you enable Monitoring. For supported versions of SQL Server and other details, see [Server requirements for Skype for Business Server 2015](requirements-for-your-environment/server-requirements.md)

Monitoring data can share a SQL Server instance with other types of data. Typically, the call detail recording database (LcsCdr) and the Quality of Experience database (QoEMetrics) share the same SQL instance; it is also common for the two monitoring databases to be in the same SQL instance as the archiving database (LcsLog). About the only real requirement with SQL Server instances is that any one instance of SQL Server is limited to the following:

- One instance of the Skype for Business Server 2015 backend database. (As a general rule, it is not recommended that your monitoring database be collocated in the same SQL instance, or even on the same computer, as the backend database. Although technically possible, you run the risk of the monitoring database using up disk space needed by the backend database.)

- One instance of the call detail recording database.

- One instance of the Quality of Experience database.

- One instance of the archiving database.

In other words, you can't have two instances of the LcsCdr database in the same instance of SQL Server. If you need multiple instances of the LcsCdr database then you need to configure multiple instances of SQL Server.

## See also


[Deploying Monitoring](https://technet.microsoft.com/library/117f4a3e-0670-4388-a553-b9854921145f.aspx)
