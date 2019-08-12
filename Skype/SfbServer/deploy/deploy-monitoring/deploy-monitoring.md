---
title: "Deploy monitoring in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 244df419-d0a8-4b1d-aedd-a92114172ab6
description: "Summary: Learn how to deploy monitoring in Skype for Business Server."
---

# Deploy monitoring in Skype for Business Server

**Summary:** Learn how to deploy monitoring in Skype for Business Server.

Before performing these tasks, review [Plan for monitoring in Skype for Business Server](../../plan-your-deployment/monitoring.md).

You will typically implement monitoring services within your topology by completing the following two steps:

1. Enabling monitoring at the same time you set up a new Skype for Business Server pool. (In Skype for Business Server, monitoring is enabled or disabled on a pool-by-pool basis.) Note that you can enable monitoring for a pool without actually collecting monitoring data, a process explained in the Configuring Call Detail Recording and Quality of Experience Settings section of this documentation.

2. Associating a monitoring store (that is, a monitoring database) with the new pool. Note that a single monitoring store can be associated with multiple pools. Depending on the number of users homed on your Registrar pools, that means that you do not have to set up a separate monitoring database for each of your pools. Instead, single monitoring store can be used by multiple pools.

Although it's often easier to enable monitoring at the same time that you create a new pool, it's also possible to create a new pool with monitoring disabled. If you do that, you can later use Topology Builder to enable the service: Topology Builder provides a way to enable or disable monitoring for a pool, or to associate a pool with a different monitoring store. Keep in mind that even though there is no longer a Monitoring Server role you will still need to create one or more monitoring stores: back-end databases used to store the data gathered by the monitoring service. These back-end databases can be created using Microsoft SQL Server 2008 R2, Microsoft SQL Server 2012., or Microsoft SQL Server 2014.

> [!NOTE]
> If monitoring has been enabled for a pool you can disable the process of collecting monitoring data without having to change your topology: Skype for Business Server provides a way for you to disable (and then later re-enable) Call Detail Recording (CDR) or Quality of Experience (QoE) data collection. For more information, see the Configuring Call Detail Recording and Quality of Experience Settings section of this document.

One other important enhancement to monitoring in Skype for Business Server is the fact that Skype for Business Server Monitoring Reports now support IPv6: reports that use the IP Address field will display either IPv4 or IPv6 addresses depending on : 1) the SQL query being used; and, 2) where or not the IPv6 address is stored in the monitoring database.

> [!NOTE]
> Ensure that the SQL Server Agent Service Startup Type is Automatic and the SQL Server Agent Service is running for the SQL Instance which is holding the Monitoring databases, so that the Default Monitoring SQL Server Maintenance Jobs can run on their scheduled basis under the control of the SQL Server Agent Service.

This documentation walks you through the process of installing and configuring monitoring and Monitoring Reports for Skype for Business Server. The documentation provides step-by-step instructions that will help you to:

- Enable monitoring in your topology and associate a monitoring store with a Front End pool.

- Install SQL Server Reporting Services and the Skype for Business Server Monitoring Reports. Monitoring Reports are preconfigured reports that provide different views into the information stored in a monitoring database.

- Configure Call Detail Recording (CDR) and Quality of Experience (QoE) data collection. Call detail recording provides a way for you to track usage of Skype for Business Server capabilities such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay).

- Manually purge CDR and/or QoE records from the monitoring database.

## Deployment checklist for monitoring

Although monitoring is already installed and activated on each Front End server, there are still several steps that you must undertake before you can actually being to collect monitoring data for Skype for Business Server. These steps are outlined in the following checklist:

|**Phase**|**Steps**|**Role and group membership**|**Documentation**|
|:-----|:-----|:-----|:-----|
|**Install prerequisite hardware and software** <br/> |Install a supported version of Microsoft SQL Server on the computer that will act as the backend data store for monitoring.  <br/> |Domain user who is also a member of the local administrators group.  <br/> |[Supported Hardware](https://technet.microsoft.com/library/5f9c085d-205e-4235-9061-9ad875283cb0.aspx) <br/> [Server Software and Infrastructure Support](https://technet.microsoft.com/library/4ee5fe38-0191-4710-9aa2-df8895e8c51b.aspx) <br/> |
|**Create the appropriate internal topology to support monitoring** <br/> |Use Skype for Business Server Topology Builder to add monitoring databases to the topology, then published the updated topology.  <br/> |To define a topology, a user who is a member of the local users group.  <br/> To publish the topology, a user who is a member if the domain administrators group and the RTCUniversalServerAdmins group.  <br/> |[Associate a monitoring store with a Front End pool in Skype for Business Server](associate-a-monitoring-store.md) <br/> |
|**Enable the appropriate monitoring settings** <br/> |Enable Call Detail Recording (CDR) and/or Quality of Experience (QoE) monitoring at the global and/or the site scopes.  <br/> |A user who is a member of the RTCUniversalServerAdmins group or who has been assigned an RBAC role that provides access to the CsCdrConfiguration and CsQoEConfiguration cmdlets.  <br/> |[Configure call detail recording and Quality of Experience settings in Skype for Business Server](call-detail-recording-and-qoe.md) <br/> |

## Enable monitoring

Although the unified data collection agents are automatically installed and activated on each Front End server, that does not mean that you will automatically begin to collect monitoring data the moment you finish installing Skype for Business Server. Instead, you must do two things: you must associate your Front End servers/Front End pools with a monitoring database, and you must enable Call Detail Recording (CDR) and/or Quality of Experience (QoE) monitoring at the global scope and/or the site scope.

For step-by-step instructions on associating Front End servers or Front End pools with a monitoring database, see the topic [Associate a monitoring store with a Front End pool in Skype for Business Server](associate-a-monitoring-store.md) in the Deployment guide. After these associations have been made, and after your new Skype for Business Server topology has been published, you will still not be able to collect monitoring data. That's because, by default, both CDR and QoE data collection is disabled when you install Skype for Business Server.

In order to begin data collection you will need to enable CDR and/or QoE monitoring. (Note that you do not have to enable both CDR and QoE monitoring; if you prefer, you can enable one type of monitoring while leaving the other type disabled.) To enable CDR monitoring at the global scope run the following command from within the Skype for Business Server Management Shell:

```
Set-CsCdrConfiguration -Identity "global" -EnableCDR $True
```

Alternatively, you can enable CDR monitoring from within the Skype for Business Server Control Panel. From within the Skype for Business Server Control Panel, complete the following procedure:

1. Click **Monitoring**.

2. On the **Call Detail Recording** tab, double-click the **Global** setting.

3. In the **Edit Call Detail Recording (CDR) Setting** pane, select **Enable monitoring of CDRs** and then click **Commit**.

To enable QoE monitoring at the global scope, run this command from within the Skype for Business Server Management Shell:

```
Set-CsQoEConfiguration -Identity "global" -EnableQoE $True
```

If you prefer, you can also enable QoE monitoring from within the Skype for Business Server Control Panel. From within the Control Panel, complete the following procedure:

1. Click **Monitoring**.

2. On the **Quality of Experience Data** tab, double-click the **Global** setting.

3. In the **Edit Quality of Experience (QoE) Setting** pane, select **Enable monitoring of QoE data** and then click **Commit**.

As noted, the preceding examples enable monitoring at the global scope; that is, they enable CDR and QoE monitoring throughout your organization. Alternatively, you can create separate CDR and QoE configuration settings at the site scope, and then selectively enable or disable monitoring for each site. For example, you could enable CDR monitoring for your Redmond site, yet disable CDR monitoring for your Dublin site. For more information on managing your monitoring configuration settings, see the Deployment guide topic [Configure call detail recording and Quality of Experience settings in Skype for Business Server](call-detail-recording-and-qoe.md).

## See also

[Plan for monitoring in Skype for Business Server](../../plan-your-deployment/monitoring.md)
