---
title: Plan hybrid connect | Skype for Business Server 2019 Office 365 integration 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Planning considerations for implementing hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams."
---

# Plan hybrid connectivity between Skype for Business Server and Office 365

## Overview

Read this topic to learn how to plan hybrid connectivity between Skype for Business Server and Teams or Skype for Business Online. Setting up hybrid connectivity is the first step in moving your on-premises environment to the cloud.

If you have on-premises Skype for Business users that are also using Teams (side by side), those users do not have the ability to interoperate with Skype for Business users from their Teams client, nor communicate with users in federated organizations, from their Teams client. To gain this functionality in Teams, these users must be moved from Skype for Business on-premises to the cloud, which requires configuring Skype for Business hybrid mode. In addition, for the best experience, these users should be in Teams Only mode, which ensures all incoming calls and chats from any user land in the user’s Teams client.

Setting up hybrid connectivity and moving all users to the cloud is also required before you decommission your on-premises Skype for Business deployment.  With hybrid connectivity set up, you can choose to move your users to the cloud based on your schedule and business need. With Direct Routing, you can leverage your on-premises voice infrastructure while you move to the cloud and after your migration is complete.

This topic describes the infrastructure and system requirements you'll need to configure hybrid connectivity between your existing on-premises Skype for Business Server deployment and Teams or Skype for Business Online.

After you have read this topic and are ready to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md). The configuration topics provide step-by-step guidance for setting up hybrid connectivity between your on-premises deployment and Teams or Skype for Business Online.

## About Shared SIP Address Space functionality

<a name="BKMK_Overview"> </a>

 With hybrid connectivity set up between an on-premises deployment of Skype for Business Server and Teams or Skype for Business Online, you can have some users homed on-premises and some users homed online.

This type of configuration relies on shared SIP address space functionality, and is sometimes referred to as "split domain"--meaning users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Teams or Skype for Business Online, as shown in the following diagram:

![SfB Hybrid connectivity - split domain](../../sfbserver2019/media/plan-hybrid-connectivity-2019-1.png)

When shared SIP address space is configured:

- Azure Active Directory Connect is used to synchronize your on-premises directory with Office 365.
- Users who are homed on premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Skype for Business Online or Teams services.
- Users from both environments can communicate with each other.
- The on-premises Active Directory is authoritative. All users should be created in the on-premises Active Directory first, and then synchronized to Azure AD. Even if you intend for the user to be homed online, you must first create the user in the on-premises environment, and then move the user to online to ensure the user is discoverable by on-premises users.

Before a user can be moved online, the user must be assigned a Skype for Business Online (Plan 2) license. If the user will be using Teams, the user must also be assigned a Teams license (and the Skype for Business license must remain enabled). If your users want to take advantage of additional online features, such as Audio Conferencing or Phone System, you need to assign them the appropriate license in Office 365.

## Infrastructure requirements

<a name="BKMK_Infrastructure"> </a>

To implement hybrid connectivity between your on-premises environment and Office 365 communication services, you need to meet the following infrastructure requirements:

- A single on-premises deployment of Skype for Business Server or Lync Server that is deployed in a supported topology. See [Topology requirements](plan-hybrid-connectivity.md#BKMK_Topology) in this topic.
- A Microsoft Office 365 tenant with Skype for Business Online enabled.
    > [!NOTE]
    > You can use only a single tenant for a hybrid configuration with your on-premises deployment.
- Azure Active Directory Connect to synchronize your on-premises directory with Office 365. For more information, see [Azure AD Connect: Accounts and permissions](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).
- Skype for Business Server administrative tools.  These are required to move users from on-premises to the cloud. These tools must be installed on a server with access to both on-premises deployment and the internet.
- Online administrative tools.  You can use either the Teams admin center or Windows PowerShell to manage Teams and Skype for Business Online. To use PowerShell to manage either Teams or Skype for Business Online, download and install the Skype for Business Online Connector.
- Shared SIP address space must be enabled, and your on-premise deployment must be configured to use Office 365 as a hosting provider. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity](configure-hybrid-connectivity.md).

After you configure hybrid connectivity, you can move users to Teams or Skype for Business Online. For more information, see [Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md) and [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).

## Server version requirements

<a name="BKMK_Topology"> </a>

To configure your deployment for hybrid with **Teams or Skype for Business Online**, you need to have one of the following supported topologies:

- A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.
- A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.
- A Lync Server 2013 deployment with all servers running Lync Server 2013.  However, if hybrid voice connectivity is required, you must use a mixed version topology as noted below.
- A deployment with maximum of 2 different server versions as listed below:
  - Skype for Business Server 2015 and Skype for Business Server 2019
  - Lync Server 2013 and Skype for Business Server 2019
  - Lync Server 2013 and Skype for Business Server 2015

*If hybrid voice is desired in any topology*, both the edge server that is designated as the Federation Edge as well as the pool associated with SIP federation must be running Skype for Business 2015 or later. Users can remain on a Lync 2013 Pool if one exists. For more details, see [Plan Phone System with PSTN Connectivity in Skype for Business Server](https://docs.microsoft.com/en-us/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity).

The following topologies that include **Lync Server 2010 are supported with Skype for Business Online** for instant messaging and meetings.  Topologies that include **Lync Server 2010 are not supported for hybrid voice nor Teams**.

- A mixed Lync Server 2010 and Skype for Business Server 2015 deployment
- A mixed Lync Server 2010 and Lync Server 2013 deployment
- A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates.

The federation Edge Server and next hop server from the federation Edge Server must be running Lync Server 2010 with the latest cumulative updates. The Skype for Business Server 2015 or Lync Server 2013 Administrative Tools must be installed on at least one server or management workstation.

## Multi-forest support

<a name="BKMK_MultiForest"> </a>

Microsoft supports the following types of multi-forest hybrid scenarios:

- **Resource forest topology.** In this kind of topology, there is one forest that hosts Skype for Business Server (the resource forest), and there are one or more additional forests that host account identities, which access the Skype for Business Server in the resource forest. In general, users can access Skype for Business functionality in another forest if the following requirements are met:
  - Users are properly synchronized into the forest that hosts Skype for Business. In hybrid configurations, this means that users must be synchronized as disabled user objects.
  - The forest hosting Skype for Business must trust the forest containing the users.
    For details on resource forest hybrid scenarios, see [Deploy a resource forest topology for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid.md).
- **Multiple deployments of Skype for Business Server in multiple forests.** This configuration can arise as a result of merger and acquisition scenarios, as well as in more complex enterprises.  Consolidation of all users from on premises to the cloud in a single Office 365 tenant can be achieved for any organization with multiple Skype for Business deployments, provided that the following key requirements are met:

  - There must be at most one Office 365 tenant involved. Consolidation in scenarios with more than one Office 365 tenant is not supported.
  - At any given time, only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space). All other on-premises Skype for Business forests must remain fully on premises (and presumably federated with each other). Note that these other on-premises organizations can sync to AAD if desired with [new functionality to disable online SIP domains](https://docs.microsoft.com/en-us/powershell/module/skype/disable-csonlinesipdomain) available as of December 2018.

    Customers with deployments of Skype for Business in multiple forests must fully migrate each Skype for Business forest individually into the Office 365 tenant using split-domain (Shared SIP Address Space) functionality, and then disable hybrid with the on-premises deployment, before moving on to migrate the next on-premises Skype for Business deployment. Furthermore, prior to being migrated to the cloud, on-premises users remain in a federated state with any users that are not represented in the same user’s on-premises directory. For more details, see [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md).

## Federation requirements

<a name="BKMK_Federation"> </a>

When configuring hybrid, you must ensure that your on-premises and online environments can federate with each other.  The online environment has open federation by default; the on-premises environment often has closed federation by default.  

The following requirements must be met to successfully configure a hybrid deployment:

- Domain matching must be configured the same for your on-premises deployment and your Office 365 tenant. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online tenant. If partner discovery is not enabled, then closed federation must be configured for your online tenant.
- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.
- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.
- Federation must be enabled for the external communications for the online tenant.

## Network considerations

The following sections describe considerations for:

- DNS settings
- Firewall considerations

### DNS settings

<a name="BKMK_DNS"> </a>

When creating DNS records for hybrid deployments, all Skype for Business external DNS records should point to the on-premises infrastructure. For details on required DNS records, please refer to [DNS requirements for Skype for Business Server](../../sfbserver/plan-your-deployment/network-requirements/dns.md).

Additionally, you need to ensure that the DNS resolution described in the following table works in your on-premises deployment. (If you already configured federation for on-premises, then you most likely already have these.)

|DNS record  <br/> |Resolvable by  <br/> |DNS requirement  <br/> |
|:-----|:-----|:-----|
|DNS SRV record for _sipfederationtls._tcp.\<sipdomain.com\> for all supported SIP domains resolving to Access Edge external IP(s)  <br/> |Edge server(s)  <br/> |Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.  <br/> Must use strict DNS name matching between the domain in the user name and the SRV record.  <br/> |
|DNS A record(s) for Edge Web Conferencing Service FQDN, e.g. webcon.contoso.com resolving to Web Conferencing Edge external IP(s)  <br/> |Internal corporate network connected users' computers  <br/> |Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.  <br/> |

Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.

### Firewall considerations

<a name="BKMK_Firewall"> </a>

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.

Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from \*.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.

For more information, including details about ports and protocol requirements, see [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/p/?LinkId=252942).
