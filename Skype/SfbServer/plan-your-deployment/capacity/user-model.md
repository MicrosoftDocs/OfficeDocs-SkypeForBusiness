---
title: "Capacity planning user model usage for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 902ab23e-94d6-482a-9d6e-c0b28dc3e03d
description: "This article provides guidance on how many servers you need at a site for the number of users at that site, according to the usage described in User models in Skype for Business Server."
---

# Capacity planning user model usage for Skype for Business Server

This article provides guidance on how many servers you need at a site for the number of users at that site, according to the usage described in [User models in Skype for Business Server](user-models.md).

> [!NOTE]
> All recommendations in this article assume that you have installed Skype for Business Cumulative Update, November 2015, or later on your servers.

## Tested Hardware Platform

We've done our performance testing on the hardware described in the table below. All our recommendations and results are based on this hardware. If you decide to try using less powerful hardware than what you see listed here, please be aware that you may face functionality problems or poor performance. These hardware recommendations are the same as Lync Server 2013, if that's helpful (and in upgrade scenarios, it may be).

**Hardware Used in Performance Testing**

|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> |64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher.  <br/> Intel Itanium processors are not supported for Skype for Business Server server roles.  <br/> |
|Memory  <br/> |32 gigabytes (GB).  <br/> |
|Disk  <br/> |8 or more 10,000-RPM hard disk drives with at least 72 GB free disk space. Two of the disks should use RAID 1, and six should use RAID 10.  <br/> - OR - <br/>Solid state drives (SSDs) that provide performance similar to 8 10,000-RPM mechanical disk drives. <br/> |
|Network  <br/> |1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address).  <br/> |

## Summary of Results

The following table summarizes our recommendations.

|**Server role**|**Maximum number of users supported**|
|:-----|:-----|
|Front End pool with twelve Front End Servers and one Back End Server or a mirrored pair of Back End Servers.  <br/> |80,000 unique users simultaneously logged in, plus 50% multiple points of presence (MPOP) representing non-mobile instances, plus 40% of users enabled for Mobility for a total of 152,000 endpoints.  <br/> |
|A/V Conferencing  <br/> |The A/V Conferencing service provided by a Front End pool supports the pool's conferences assuming a maximum conference size of 250 users, and only one such large conference running at a time.  <br/> **Note:** Additionally, you can support large conferences of between 250 and 1000 users by deploying a separate Front End pool with two Front End Servers to host the large conferences. For details, see [Plan for large meetings in Skype for Business Server](../../plan-your-deployment/conferencing/large-meetings.md).  <br/> |
|One Edge Server  <br/> |12,000 concurrent remote users.  <br/> |
|One Director  <br/> |12,000 concurrent remote users.  <br/> |
|Monitoring and Archiving  <br/> |The Monitoring and Archiving front end services run on each Front End Server, instead of on separate server roles.  <br/> Monitoring and Archiving each still require their own database stores. If you also run Exchange 2013 or later, you can keep your Archiving data in Exchange, rather than in a dedicated SQL database.  <br/> |
|One Mediation Server  <br/> |Mediation Server collocated with Front End Server runs on every Front End Server in a pool, and should provide enough capacity for the users in the pool. For stand-alone Mediation Server, see the "Mediation Server" section later in this topic.  <br/> |
|One Standard Edition server  <br/> |We strongly recommend that if you use Standard Edition servers to host users, you always use two servers, paired using the recommendations in [Planning for High Availability and Disaster Recovery](https://technet.microsoft.com/library/15a72073-0336-45dd-b2a0-35e7522c6000.aspx). Each server in the pair can host up to 2,500 users, and if one server fails the remaining server can support 5,000 users in a failover scenario.  <br/>  If your deployment includes a significant amount of audio or video traffic, server performance may suffer with more than 2,500 users per server. In this case, you should consider adding more Standard Edition servers or moving to Skype for Business Server Enterprise Edition. <br/> |

## Front End Server

> [!NOTE]
> Stretched pools aren't supported for this server role.

In a Front End pool, you should have one Front End Server for every 6,660 users homed in your pool, assuming that hyper-threading is enabled on all servers in the pool, and that the server hardware meets the recommendations in [Server requirements for Skype for Business Server 2015](../requirements-for-your-environment/server-requirements.md) or  [System requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md). The maximum number of users in one Front End pool is 80,000, again assuming that hyper-threading is enabled on all the servers in your pool. If you have more than 80,000 users at a site, you can deploy more than one Front End pool.

When you account for the number of users in a Front End pool, include any users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with this Front End pool.

When an active server is unavailable, its connections are transferred automatically to the other servers in the pool. In a scenario where you have 30,000 users and five Front End Servers, if one server is unavailable, the connections of 6000 of your users need to be transferred to your other four remaining servers. These four remaining servers will then each have 7500 users, which is a larger number than recommended.

If instead you had started with six Front End Servers for your 30,000 users and one becomes unavailable, a total of 5000 users need to move to the remaining five servers. These five remaining servers will then each host 6000 users, which is in the recommended range.

The maximum number of users in a Front End pool is 80,000. The maximum number of Front End Servers in a pool is 12.

For a Front End pool with 80,000 users, twelve Front End Servers will be good for performance, in typical deployments that follow the [User models in Skype for Business Server](user-models.md). Deployments designed to support disaster recovery failover assume that a maximum of 40,000 users can be hosted in each of two paired Front End pools, in which each pool has enough Front End Servers to contain the users in both pools, should one pool need to be failed over to the other.

The number of users supported with good performance by a particular Front End pool may differ from these numbers for the following reasons:

- The hardware for your Front End Servers doesn't meet the recommendations.

- Your organization's usage is very different from the user models, for example, if you have a lot more conferencing traffic.

The following table shows the average bandwidth for IM and presence, given the user model, as defined in [User models in Skype for Business Server](user-models.md).

|**Average bandwidth per user**|**Bandwidth requirements per Front End Server with 6,660 users**|
|:-----|:-----|
|1.3 Kpbs  <br/> |13 Mbps  <br/> |

> [!NOTE]
> To improve the media performance of the co-located A/V Conferencing and Mediation Server functionality on your Front End Servers, you should enable receive-side scaling (RSS) on the network adapters on your Front End Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, see [Receive Side Scaling (RSS) in the Windows Server 2012 documentation](https://go.microsoft.com/fwlink/p/?LinkId=620365). For details about how to enable RSS, you'll need to refer to your network adapter documentation.

## Conferencing Maximums

Given the user model that 5% of users in a pool may be in a conference at any one time, a pool of 80,000 users could have about 4,000 users in conferences simultaneously. These conferences are expected to be a mix of media (some IM-only, some IM with audio, some audio/video, for example) and number of participants. There isn't a hard limit for the actual number of conferences allowed, and actual usage determines the actual performance. For example, if your organization has many more mixed-mode conferences than are assumed in the user model, you might need to deploy more Front End Servers or A/V Conferencing Servers than the recommendations found in this article. For details about the assumptions in the user model, see [User models in Skype for Business Server](user-models.md).

The maximum supported conference size hosted by a regular Skype for Business Server Front End pool which also hosts users is 250 participants. While a 250-user conference is happening, the pool still supports other conferences as well, such that a total of 5% of pool users are in concurrent conferences. For example, in a pool of twelve Front End Servers and 80,000 users, while the 250-user conference is happening, Skype for Business Server supports 3,750 other users participating in smaller conferences.

Regardless of the number of users homed on the Front End pool or Standard Edition server, Skype for Business Server supports a minimum of 125 other users participating in smaller conferences on the same pool or server which is hosting a 250-user conference.

To enable conferences that have between 250 and 1000 users, you can set up a separate Front End pool just to host those conferences. This Front End pool won't host any users. For details, please see [Plan for large meetings in Skype for Business Server](../../plan-your-deployment/conferencing/large-meetings.md).

If your organization has a lot more mixed-mode conferences than are assumed in the user model, you might need to deploy more Front End Servers than we recommendation in this document (up to a limit of 12 Front End Servers). For details about the assumptions in the user model, see [User models in Skype for Business Server](user-models.md).

## Edge Server

> [!NOTE]
> Stretched pools aren't supported for this server role.

You should deploy one Edge Server for every 12,000 remote users who will access a site concurrently. At a minimum we recommend two Edge Servers for high availability. These recommendations assume that the hardware for your Edge Servers meets the recommendations in [Server Hardware Platforms](https://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx).

When you account for the number of users for the Edge Servers, include the users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with a Front End pool at this site.

> [!NOTE]
> To improve the performance of the A/V Conferencing Edge service on your Edge Servers, you should enable receive-side scaling (RSS) on the network adapters on your Edge Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, check "[Receive Side Scaling (RSS)
in Windows Server 2012](https://go.microsoft.com/fwlink/p/?linkId=268731)". For details about how to enable RSS, you'll need to refer to your network adapter documentation.

## Director

> [!NOTE]
> Stretched pools aren't supported for this server role.

If you deploy the Director server role, we recommend that you deploy one Director for every 12,000 remote users who will access a site concurrently. At a minimum we recommend two Directors for high availability. These recommendations assume that the hardware for your Edge Servers meets the recommendations in [Server Hardware Platforms](https://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx).

When you account for the number of users for the Directors, include the users homed on Survivable Branch Appliances and Survivable Branch Servers at branch offices that are associated with a Front End pool at this site.

## Mediation Server

> [!NOTE]
> Stretched pools aren't supported for this server role.

If you collocate Mediation Server with Front End Server, Mediation Server runs on every Front End Server in the pool, and should provide enough capacity for the users in the pool.

If you deploy a stand-alone Mediation Server pool, then how many Mediation Servers to deploy depends on many factors, including the hardware used for Mediation Server, the number of VoIP users you have, the number of gateway peers that each Mediation Server pool controls, the busy hour traffic through those gateways, and the percentage of calls with media that bypasses the Mediation Server.

The following tables provide a guideline for how many concurrent calls a Mediation Server can handle, assuming that the hardware for the Mediation Servers meets the requirements in [Server Hardware Platforms](https://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx) and that hyper-threading is enabled. For details about Mediation Server scalability, see [Estimating voice usage and traffic for Skype for Business Server](estimating-voice-traffic.md) and [Deployment guidelines for Mediation Server in Skype for Business Server](mediation-server-deployment-guidelines.md).

All the following tables assume usage as summarized in [User models in Skype for Business Server](user-models.md).

**Stand-alone Mediation Server Capacity: 70% Internal Users, 30% External users with non-bypass call capacity (media transcoding performed by Mediation Server)**

|**Server hardware**|**Maximum number of calls**|**Maximum number of T1 lines**|**Maximum number of E1 lines**|
|:-----|:-----|:-----|:-----|
|Dual processor, hex core, 2.26 GHz hyper-threaded CPU **with hyper-threading disabled**, with 32 GB memory and one dual-port network adapter card.  <br/> |1100  <br/> |46  <br/> |35  <br/> |
|Dual processor, hex core, 2.26 GHz hyper-threaded CPU, with 32 GB memory and one dual-port network adapter card.  <br/> |1500  <br/> |63  <br/> |47  <br/> |

> [!NOTE]
> Although servers with 32 GB of memory were used for performance testing, servers with 16 GB of memory are supported for stand-alone Mediation Server, and are sufficient to provide the performance shown in this table.

**Mediation Server Capacity (Mediation Server Collocated with Front End Server) 70% Internal Users, 30% External Users, Non-Bypass Call Capacity (Media Processing Performed by Mediation Server)**

|**Server hardware**|**Maximum number of calls**|
|:-----|:-----|
|Dual processor, hex core, 2.26 GHz hyper-threaded CPU, with 32 GB memory and 2 1GB network adapter cards.  <br/> |150  <br/> |

> [!NOTE]
> This number is much smaller than the numbers for the stand-alone Mediation Server. That's because the Front End Server has to handle other features and functions for the 6600 users homed on it, in addition to the transcoding needed for voice calls.

> [!NOTE]
> To improve the performance of the Mediation Server, you should enable receive-side scaling (RSS) on the network adapters on your Mediation Servers. RSS enables incoming packets to be handled in parallel by multiple processors on the server. For details, see "[Receive-Side Scaling in Windows Server 2012](https://go.microsoft.com/fwlink/p/?linkId=268731)". For details about how to enable RSS, you'll need to refer to your network adapter documentation.

## Back End Server

Although much of the database information is stored primarily on the Front End Servers, you should make sure your Back End Servers meet the hardware recommendations listed earlier in this section and in [Server Hardware Platforms](https://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx).

To provide high availability of your Back End Server, we recommend deploying AlwaysOn Availability Groups or server mirroring. For more information, see [Back End Server high availability in Skype for Business Server](../../plan-your-deployment/high-availability-and-disaster-recovery/back-end-server.md).

## Monitoring and Archiving

If you deploy Monitoring or Archiving, the front end functionality of these services runs on the Front End Servers, Monitoring and Archiving each use their own database store, separate from the Back End store. Alternatively, if you have Exchange 2013 deployed, you can store instant message Archiving data in Exchange instead of in a dedicated SQL store.

The following table indicates approximately how much database storage is required per user per day for Monitoring and Archiving data.

||**CDR (Monitoring)** <br/> |**QoE (Monitoring)** <br/> |**Archiving** <br/> |
|:-----|:-----|:-----|:-----|
|Disk space required per user per day  <br/> |49 KB  <br/> |28 KB  <br/> |57 KB  <br/> |

Microsoft used the hardware in the following table for the database server for Monitoring and Archiving during its performance testing. The testing collected the data of two Front End pools, each of which contained 80,000 users.

**Hardware Used in Monitoring and Archiving Performance Testing**

|**Hardware component**|**Recommended**|
|:-----|:-----|
|CPU  <br/> |64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher  <br/> |
|Memory  <br/> |48 gigabytes (GB)  <br/> |
|Disk  <br/> |25 10,000-RPM hard disk drives with 300 GB on each disk, with the configuration in the following table  <br/> |
|Network  <br/> | 1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address)  <br/> |

**Recommended Disk configurations**

|**Drive** <br/> |**RAID Configuration** <br/> |**Number of disks** <br/> |
|:-----|:-----|:-----|
|CDR, QoE, and Archiving database data files, on a single drive  <br/> |1+0  <br/> |16  <br/> |
|CDR database log file  <br/> |1  <br/> |2  <br/> |
|QoE database log file  <br/> |1  <br/> |2  <br/> |
|Archiving database log file  <br/> |1  <br/> |2  <br/> |

## Video Interop Server capacity

If you deploy Video Interop Server and you need to determine capacity, you look at the maximum number of Video Teleconferencing Systems (VTCs) that will be in concurrent calls. For example, if you have 250 VTCs in your organization and your user model estimates that at most, 20% of them might be in concurrent calls, you base your capacity planning on 50 concurrent VTCs.


