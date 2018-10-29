---
title: "Plan hybrid connectivity"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
description: "Planning considerations for implementing hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams."
---


# Plan hybrid connectivity between Skype for Business Server and Office 365

## Overview

Read this topic to learn how to plan hybrid connectivity between Skype for Business Server and Teams or Skype for Business Online. Setting up hybrid connectivity is the first step in in moving your on-premises environment to the cloud.

If you have an on-premises environment and are using Teams, users who are homed in Skype for Business on premises do not have the ability to interoperate with Skype for Business users, nor communicate with users in federated organizations. To enable this functionality, users must be in TeamsOnly mode, which requires moving the user’s Skype for Business home from on-premises to online. Therefore, you must configure hybrid connectivity to achieve TeamsOnly mode.  

Setting up hybrid connectivity and moving all users to the cloud is also required before you decommission your on-premises Skype for Business deployment.  With hybrid connectivity set up, you can choose to move your users to the cloud based on your schedule and business need. As you move to the cloud, you can still leverage your on-premises voice infrastructure. 

This topic describes the infrastructure and system requirements you'll need to configure hybrid connectivity between your existing on-premises Skype for Business Server deployment--with users who were created in your on-premises Active Directory--and Teams or Skype for Business Online. 

This topic describes the infrastructure and system requirements you'll need to configure hybrid connectivity between your existing on-premises Skype for Business Server deployment--with users who were created in your on-premises Active Directory--and Teams or Skype for Business Online.

After you have read this topic and are ready to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md). The configuration topics provide step-by-step guidance for setting up hybrid connectivity between your on-premises deployment and Teams or Skype for Business Online.


## About Split domain functionality
<a name="BKMK_Overview"> </a>

 With hybrid connectivity set up between an on-premises deployment of Skype for Business Server and Teams or Skype for Business Online, you can have some users homed on-premises and some users homed online.

This type of configuration relies on shared SIP address space functionality, and is sometimes referred to as "split domain"--meaning users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Teams or Skype for Business Online, as shown in the following diagram: 

![SfB Hybrid connectivity - split domain](../../sfbserver2019/media/plan-hybrid-connectivity-2019-1.png)

When a shared SIP address space is configured:

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

<<<<<<< HEAD
- Azure Active Directory Connect to synchronize your on-premises directory with Office 365. For more information, see [Azure AD Connect: Accounts and permissions](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).
=======
- Skype for Business Server administrative tools. (If you are using Lync Server 2013 or Lync Server 2010, you can use the Lync Server 2013 administrative tools. For more information, see [Lync Server 2013 hybrid](https://go.microsoft.com/fwlink/p/?LinkId=617360).)

- Azure Active Directory Connect to synchronize your on-premises directory with Office 365. For more information, see [Azure AD Connect: Accounts and permissions](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).
>>>>>>> master

- Skype for Business Server administrative tools.  These are required to move users from on-premises to the cloud. These tools must be installed on a server with access to both on-premises deployment and the internet. 

- Online administrative tools.  You can use either the Teams and Skype for Business Admin Center or Windows PowerShell to manage Teams and Skype for Business Online. To use PowerShell to manage either Teams or Skype for Business Online, download and install the Skype for Business Online Connector. 

- Shared SIP address space must be enabled, and your on-premise deployment must be configured to use Office 365 as a hosting provider. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity](configure-hybrid-connectivity.md).

After you configure hybrid connectivity, you can move users to Teams or Skype for Business Online. For more information, see [Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md) and [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).


## Topology requirements
<a name="BKMK_Topology"> </a>

To configure your deployment for hybrid with Teams or Skype for Business Online, you need to have one of the following supported topologies:

- A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019. 

- A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.

- A Lync Server 2013 deployment with all servers running Lync Server 2013.

    For hybrid voice connectivity, the Edge Server that is designated as Federation Edge must be Skype for Business 2015; the Edge also requires a Skype for Business Server backend. You might have a pool with no users on it.

- A mixed Lync Server 2015 and Skype for Business Server 2019 deployment with the following server roles: 

  - At least one Enterprise Pool or Standard Edition server 
  - The Director Pool associated with SIP federation, if it exists 
  - The Edge Pool associated with SIP federation 

- A mixed Lync Server 2013 and Skype for Business Server 2019 deployment with the following server roles in at least one site running Skype for Business Server 2019: 

  - At least one Enterprise Pool or Standard Edition server 
  - The Director Pool associated with SIP federation, if it exists 
  - The Edge Pool associated with SIP federation 

- A mixed Lync Server 2013 and Skype for Business Server 2015 deployment with the following server roles in at least one site running Skype for Business Server 2015:

  - At least one Enterprise Pool or Standard Edition server

  - The Director Pool associated with SIP federation, if it exists

  - The Edge Pool associated with SIP federation

- A mixed Lync Server 2010 and Skype for Business Server 2015 deployment with the following server roles in at least one site running Skype for Business Server 2015:

  - At least one Enterprise Pool or Standard Edition server

  - The Director Pool associated with SIP federation, if it exists

  - The Edge Pool associated with SIP federation for the Site

- A mixed Lync Server 2010 and Lync Server 2013 deployment with the following server roles in at least one site running Lync Server 2013:

  - At least one Enterprise Pool or Standard Edition server in the site

  - The Director Pool associated with SIP federation, if it exists in the site

  - The Edge Pool associated with SIP federation for the site

- A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates.

  - The federation Edge Server and next hop server from the federation Edge Server must be running Lync Server 2010 with the latest cumulative updates.

  - The Skype for Business Server 2015 or Lync Server 2013 Administrative Tools must be installed on at least one server or management workstation.


 ## Multi-forest support
<a name="BKMK_MultiForest"> </a>

Users can access Skype for Business functionality in another forest if the following requirements are met:

- Users are properly synchronized into the forest that hosts Skype for Business: In hybrid configurations, this means that users must be synchronized as disabled user objects.

- The forest hosting Skype for Business must trust the forest containing the users.

For details on multi-forest hybrid scenarios, see [Configure a multi-forest environment for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid.md).


## Federation requirements
<a name="BKMK_Federation"> </a>

When configuring hybrid, you must ensure that your on-premises and online environments can federate with each other.  The online environment has open federation by default; the on-premises environment often has closed federation by default.  

The following requirements must be met to successfully configure a hybrid deployment:

- Domain matching must be configured the same for your on-premises deployment and your Office 365 tenant. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online tenant. If partner discovery is not enabled, then closed federation must be configured for your online tenant.

- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.

- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.

- Federation must be enabled for the external communications for the online tenant, which is configured by using the Skype for Business Online Control Panel.


## Network considerations

The following sections describe considerations for: 

- DNS settings 
- Firewall considerations 
- Port and protocol requirements


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

For more information, see [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/p/?LinkId=252942).

### Port and protocol requirements
<a name="BKMK_Ports"> </a>

In addition to the port requirements for internal communication, you must also configure the following ports to enable hybrid connectivity:


|**Protocol**|**TCP or UDP**|**Source IP**|**Destination IP**|**Source port**|**Destination port**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|SIP (MTLS)  <br/> |TCP  <br/> |Access Edge  <br/> |Office 365  <br/> |Any  <br/> |5061  <br/> |Signaling  <br/> |
|SIP (MTLS)  <br/> |TCP  <br/> |Office 365  <br/> |Access Edge  <br/> |Any  <br/> |5061  <br/> |Signaling  <br/> |
|STUN  <br/> |TCP  <br/> |A/V Edge  <br/> |Office 365  <br/> |50000-59999  <br/> |443, 50000-59999  <br/> |Open for audio, video, application sharing sessions  <br/> |
|STUN  <br/> |TCP  <br/> |Office 365  <br/> |A/V Edge  <br/> |443  <br/> |50000-59999  <br/> |Open for audio, video, application sharing sessions  <br/> |
|STUN  <br/> |UDP  <br/> |A/V Edge  <br/> |Office 365  <br/> |3478  <br/> |3478  <br/> |Open for audio, video sessions  <br/> |
|STUN  <br/> |UDP  <br/> |Office 365  <br/> |A/V Edge  <br/> |3478  <br/> |3478  <br/> |Open for audio, video sessions  <br/> |

For more information about port and firewall planning for Edge Server, see [Edge Server environmental requirements in Skype for Business Server](../../sfbserver/plan-your-deployment/edge-server-deployments/edge-environmental-requirements.md). See also [Port and protocol requirements for servers](../../sfbserver/plan-your-deployment/network-requirements/ports-and-protocols.md) and the [Protocol workloads diagram](https://go.microsoft.com/fwlink/p/?LinkId=550989).
<<<<<<< HEAD
=======

## User accounts and data
<a name="BKMK_UserAccounts"> </a>

In a hybrid deployment, any user who you want to home online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services. You can then move the user to Skype for Business Online, which will move the user's contact list.

When you synchronize user accounts between your on-premises deployment and online tenant using AAD Connect, you need to synchronize the AD accounts for all Skype for Business or Lync users in your organization, even if users are not moved to online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.

> [!IMPORTANT]
> All user management, including user moves between on-premises and Skype for Business Online, must be done using the latest installed version of the administrative tools. The administrative tools must be installed on a separate server that has connect access to the existing on-premises deployment and to the Internet. The cmdlet to move users from your on-premises deployment to Skype for Business Online, [Move-CsUser](https://docs.microsoft.com/powershell/module/skype/move-csuser?view=skype-ps), must be run from the administrative tools connected to your on-premises deployment. For more information about moving users, see [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).

You should also consider the following user-related issues when planning for a hybrid deployment:

- **User contacts** The limit for contacts for Lync Online users is 250. Any contacts beyond that number will be removed from the user's contact list when the account is moved to Lync Online.

- **Instant Messaging and Presence** User contact lists, groups, and access control lists (ACLs) are migrated with the user account.

- **Conferencing data, meeting content, and scheduled meetings** This content is not migrated with the user account. Users must reschedule meetings after their accounts are migrated to Lync Online.

## User policies and features
<a name="BKMK_UserPolicies"> </a>

- In a hybrid environment, users can be enabled for Instant Messaging and conferencing (meetings) either on premises or online, but not both simultaneously.

- **Client support** Some users may require a new client version when they are moved to Skype for Business Online. For Office Communications Server 2007 R2, users must be moved to a Skype for Business Server or Lync Server 2013 pool prior to migration to Skype for Business Online.

- **On-premises policies and configuration (non-user)** Online and on-premises policies require separate configuration. You cannot set global policies that apply to both.
>>>>>>> master
