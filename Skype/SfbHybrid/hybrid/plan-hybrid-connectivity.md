---
title: Plan hybrid connect | Skype for Business Server 2019 and Teams 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: Plan to implement hybrid connectivity between Skype for Business Server and Teams or Skype for Business Online by configuring Skype for Business hybrid mode.
ms.custom: seo-marvel-jun2020
---

# Plan hybrid connectivity between Skype for Business Server and Teams

Read this topic to learn how to plan hybrid connectivity between Skype for Business Server and Teams (or Skype for Business Online until July 31, 2021). Setting up hybrid connectivity is the first step in moving your on-premises environment to the cloud.

If you have on-premises Skype for Business users that are also using Teams (side by side), those users do not have the ability to interoperate with Skype for Business users from their Teams client, nor communicate with users in federated organizations, from their Teams client. To gain this functionality in Teams, these users must be moved from Skype for Business on-premises to the cloud, which requires configuring Skype for Business hybrid mode. In addition, for the best experience, these users should be in Teams Only mode, which ensures all incoming calls and chats from any user land in the user’s Teams client.

Setting up hybrid connectivity and moving all users to the cloud is also required before you decommission your on-premises Skype for Business deployment.  With hybrid connectivity set up, you can choose to move your users to the cloud based on your schedule and business need. With Direct Routing, you can leverage your on-premises voice infrastructure while you move to the cloud and after your migration is complete.

This topic describes the infrastructure and system requirements you'll need to configure hybrid connectivity between your existing on-premises Skype for Business Server deployment and Teams or Skype for Business Online.

After you have read this topic and are ready to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md). The configuration topics provide step-by-step guidance for setting up hybrid connectivity between your on-premises deployment and Teams or Skype for Business Online.

> [!Important]
> Skype for Business Online will be retired on July 31, 2021 after which the service will no longer be accessible.  In addition, PSTN connectivity between your on-premises environment whether through Skype for Business Server or Cloud Connector Edition and Skype for Business Online will no longer be supported.  Learn how to connect your on-premises telephony network to Teams using [Direct Routing](/MicrosoftTeams/direct-routing-landing-page).

## Implications of the upcoming retirement of Skype for Business Online
It's important to remember that both before and after retirement of Skype for Business Online, users homed in Skype for Business Server on-premises can use Teams, but they cannot be TeamsOnly. (By default users are in Islands mode). Users can only experience the full benefits of Teams, in particular federation and PSTN support, once they are in TeamsOnly mode. 

The upcoming retirement of Skype for Business Online has no impact on the existing support lifecycle of Skype for Business Server or Lync Server 2013.  However, the upcoming retirement of Skype for Business Online will impact certain apsects of how customers with on-premises Skype for Business Server or Lync Server 2013, including existing hybrid organizations, transition to the cloud. What will not change after retirement is that the use of hybrid as the means to transition from on-premises to the cloud remains unchanged.

Currently, and up until the retirement of Skype for Business Online, hybrid organizations can consist of three basic types of users: 
- On-premises users (who may or may not use Teams, but not in Teams Only mode) 
- Online users with any coexistence mode other than TeamsOnly
- TeamsOnly users.

After the retirement of Skype for Business Online, however, hybrid organizations can only consist of two basic types of users: 
- On-premises users (Who may or may use Teams, but not in TeamsOnly mode)
- Teams Only users. 

For organizations to move from Skype for Business Server or Lync Server 2013 to Teams, they must still set up and configure hybrid using the same toolset, *exactly as before the retirement*. What has changed is when moving a user from on-premises to Teams, it is no longer required to specify the `-MoveToTeams` switch in `Move-CsUser` to move users directly from on-premises to TeamsOnly. Previously if this switch was not specified, users transitioned from being homed in Skype for Business Server on-premises to Skype for Business Online, and their mode remained unchanged. In preparation for retirement, when moving a user from on-premises to the cloud with `Move-CsUser`, users are now automatically assigned TeamsOnly mode and their meetings from on-premises are automatically converted to Teams meetings, just as if the `-MoveToTeams` switch had been specified, regardless of whether the switch is actually specified. (This includes migrations from Lync Server 2013, which never had the `MoveToTeams` switch.) 

Co-existence modes will continue to exist after retirement of Skype for Business Online. As before, users with accounts homed in Skype for Business Server on-premises can be assigned any coexistence mode except TeamsOnly. After retirement however, users homed online can only be TeamsOnly (in contrast to the present where Skype for Business Online users can be any mode).  

[!Important] Existing hybrid organizations with users homed in Skype for Business Online who are NOT TeamsOnly should focus on upgrading these users to Teams Only mode as soon as possible, but no later than the retirement on July 31, 2021. If your organization still has users homed in Skype for Business Online who are not TeamsOnly, you may be scheduled for a Microsoft-assisted upgrade to transition these users to TeamsOnly. This will not impact users who are homed in Skype for Business Server on-premises. Scheduling notifications will be sent in advance to hybrid customers with users homed in Skype for Business Online before these online, non-TeamsOnly users are upgraded to Teams.


## About Shared SIP Address Space functionality

<a name="BKMK_Overview"> </a>

 With hybrid connectivity set up between an on-premises deployment of Skype for Business Server and Teams or Skype for Business Online, you can have some users homed on-premises and some users homed online.

This type of configuration relies on shared SIP address space functionality, and is sometimes referred to as "split domain"--meaning users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Teams or Skype for Business Online, as shown in the following diagram:

![Skype for Business Hybrid connectivity - split domain](../../sfbserver2019/media/plan-hybrid-connectivity-2019-1.png)

When shared SIP address space is configured:

- Azure Active Directory Connect is used to synchronize your on-premises directory with Microsoft 365 or Office 365.
- Users who are homed on premises interact with on-premises Skype for Business servers.
- Users who are homed online may interact with Teams and, until July 31, 2021, Skype for Business Online based on their co-existence mode.
- Users from both environments can communicate with each other.
- The on-premises Active Directory is authoritative. All users should be created in the on-premises Active Directory first, and then synchronized to Azure AD. Even if you intend for the user to be homed online, you must first create the user in the on-premises environment, and then move the user to online to ensure the user is discoverable by on-premises users.

Before a user can be moved online, the user must be assigned a Teams license as well as Skype for Business Online (Plan 2). **Assignment of the Skype for Business Online license is required even after retirement of Skype for Business Online.** If your users want to take advantage of additional online features, such as Audio Conferencing or Phone System, you need to assign them the appropriate license in Microsoft 365 or Office 365.

## Hybrid connectivity infrastructure requirements

<a name="BKMK_Infrastructure"> </a>

To implement hybrid connectivity between your on-premises environment and Microsoft 365 or Office 365 communication services, you need to meet the following infrastructure requirements:

- A single on-premises deployment of Skype for Business Server or Lync Server that is deployed in a supported topology. See [Topology requirements](plan-hybrid-connectivity.md#BKMK_Topology) in this topic.

- A Microsoft 365 or Office 365 organization with Teams.
    > [!NOTE]
    > You can use only a single tenant for a hybrid configuration with your on-premises deployment.
    
- Azure Active Directory Connect to synchronize your on-premises directory with Microsoft 365 or Office 365. For more information, see [Azure AD Connect: Accounts and permissions](/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).

- Skype for Business Server administrative tools. These are required to move users from on-premises to the cloud. These tools must be installed on a server with access to both on-premises deployment and the internet.
- Online administrative tools. You can use either the Teams admin center or Windows PowerShell to manage Teams and Skype for Business Online. To use PowerShell to manage either Teams or Skype for Business Online, download and install the Teams PowerShell Module. (The Skype for Business Online Connector has been retired).
- Shared SIP address space must be enabled, and your on-premises deployment must be configured to use Microsoft 365 or Office 365 as a hosting provider. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity](configure-hybrid-connectivity.md).

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

*If hybrid voice is desired in any topology*, both the edge server that is designated as the Federation Edge as well as the pool associated with SIP federation must be running Skype for Business 2015 or later. Users can remain on a Lync 2013 Pool if one exists. For more details, see [Plan Phone System with PSTN Connectivity in Skype for Business Server](../../SfbServer/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity.md).

The following topologies that include **Lync Server 2010 are supported with Skype for Business Online** for instant messaging and meetings. Topologies that include **Lync Server 2010 are not supported for hybrid voice nor Teams**.

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

- **Multiple deployments of Skype for Business Server in multiple forests.** This configuration can arise as a result of merger and acquisition scenarios, as well as in more complex enterprises. Consolidation of all users from on premises to the cloud in a single Microsoft 365 or Office 365 organization can be achieved for any organization with multiple Skype for Business deployments, provided that the following key requirements are met:
  - There must be at most one Microsoft 365 or Office 365 organization involved. Consolidation in scenarios with more than one organization is not supported.
  - At any given time, only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space). All other on-premises Skype for Business forests must remain fully on premises (and presumably federated with each other). Note that these other on-premises organizations can sync to AAD if desired with [new functionality to disable online SIP domains](/powershell/module/skype/disable-csonlinesipdomain) available as of December 2018.

    Customers with deployments of Skype for Business in multiple forests must fully migrate each Skype for Business forest individually into the Microsoft 365 or Office 365 organization using split-domain (Shared SIP Address Space) functionality, and then disable hybrid with the on-premises deployment, before moving on to migrate the next on-premises Skype for Business deployment. Furthermore, prior to being migrated to the cloud, on-premises users remain in a federated state with any users that are not represented in the same user’s on-premises directory. For more details, see [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md).

## Federation requirements

<a name="BKMK_Federation"> </a>

When configuring Skype for Business hybrid mode, you must ensure that your on-premises and online environments can federate with each other.  The online environment has open federation by default; the on-premises environment often has closed federation by default.  

The following requirements must be met to successfully configure a hybrid deployment:

- Domain matching must be configured the same for your on-premises deployment and your Microsoft 365 or Office 365 organization. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online organization. If partner discovery is not enabled, then closed federation must be configured for your online organization.
- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.
- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.
- Federation must be enabled for the external communications for the online tenant.

## Network considerations

The following sections describe considerations for:

- DNS settings
- Firewall considerations

### DNS settings for hybrid deployments

<a name="BKMK_DNS"> </a>

When creating DNS records for hybrid deployments, all Skype for Business external DNS records should point to the on-premises infrastructure. For details on required DNS records, please refer to [DNS requirements for Skype for Business Server](../../sfbserver/plan-your-deployment/network-requirements/dns.md).

Additionally, you need to ensure that the DNS resolution described in the following table works in your on-premises deployment. (If you already configured federation for on-premises, then you most likely already have these.)

|DNS record  <br/> |Resolvable by  <br/> |DNS requirement  <br/> |
|:-----|:-----|:-----|
|DNS SRV record for _sipfederationtls._tcp.\<sipdomain.com\> for all supported SIP domains resolving to Access Edge external IP(s)  <br/> |Edge server(s)  <br/> |Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.  <br/> Must use strict DNS name matching between the domain in the user name and the SRV record.  <br/> |
|DNS A record(s) for Edge Web Conferencing Service FQDN, e.g. webcon.contoso.com resolving to Web Conferencing Edge external IP(s)  <br/> |Internal corporate network connected users' computers  <br/> |Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.  <br/> |

Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.

### Firewall considerations for hybrid deployments

<a name="BKMK_Firewall"> </a>

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.

Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from \*.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.

For more information, including details about ports and protocol requirements, see [Microsoft 365 and Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges).
