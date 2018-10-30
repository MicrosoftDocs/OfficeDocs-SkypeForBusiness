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

Read this topic to learn how to plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams. Setting up hybrid connectivity is the first step in deploying many Skype for Business hybrid solutions.

Hybrid solutions enable you to retain some on-premises control while also taking advantage of online services provided in the Microsoft cloud. With hybrid connectivity set up, and a variety of cloud services available to your online and on-premises users, you can choose to move your users to the cloud based on your schedule and business need.

For example, you might choose to get call control through Microsoft Phone System in the cloud while retaining your on-premises PSTN connectivity. You might also choose to take advantage of other cloud services, such as Cloud Voicemail and Call Data Connector.

This topic describes the infrastructure and system requirements you'll need to configure hybrid connectivity between your existing on-premises Skype for Business Server deployment--with users who were created in your on-premises Active Directory--and Skype for Business Online or Teams.

After you have read this topic and are ready to configure hybrid connectivity, see [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md). The configuration topics provide step-by-step guidance for setting up hybrid connectivity between your on-premises deployment and Skype for Business Online.

(For information about configuring your Lync Server 2013 or Lync Server 2010 deployment for hybrid, see [Lync Server 2013 hybrid](https://go.microsoft.com/fwlink/p/?LinkId=617360).)

## Split domain functionality
<a name="BKMK_Overview"> </a>

 With hybrid connectivity set up between an on-premises deployment of Skype for Business Server and Skype for Business Online or Teams, you can have some users homed on-premises and some users homed online.

This type of configuration is sometimes referred to as "split domain"--meaning users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Skype for Business Online or Teams, as shown in the following diagram:

![SfB Hybrid connectivity - split domain](../../sfbserver2019/media/plan-hybrid-connectivity-2019-1.png)

With a split domain environment:

- Users who are homed on premises interact with on-premises Skype for Business servers. They might also have access to online services, such as Cloud Voicemail.

- Users who are homed online may interact with Skype for Business or Teams online services.

- Users from both environments can collaborate with each other by using Instant Messaging, participating in conference calls or VoIP calls, and so on.

- Azure Active Directory Connect is used to synchronize your on-premises directory with Office 365.

The on-premises Active Directory is authoritative, which means that you must do the following to ensure that on-premises and online users are discoverable to one another:

- All users should be created in the on-premises Active Directory first, and then synchronized to Azure AD.

- Users who are moving to the cloud must have either a Skype for Business Plan 2 or Teams license.

- If your users want to take advantage of additional online features, such as Skype Meeting Broadcast or Cloud Voicemail, you need to assign them the appropriate license in Office 365.

- After Skype for Business Online users are assigned a license, you need to enable them for Skype for Business or for Enterprise Voice on premises. For more information, see [Enable the users for Enterprise Voice on premises](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-the-users-for-enterprise-voice-on-premises.md). For more information about hybrid voice requirements, see [Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](../../sfbserver/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity.md).


## Infrastructure requirements
<a name="BKMK_Infrastructure"> </a>

To implement hybrid connectivity between your on-premises environment and Office 365 communication services, you need to meet the following infrastructure requirements.

- A single on-premises deployment of Skype for Business Server or Lync Server that is deployed in a supported topology. See [Topology requirements](plan-hybrid-connectivity.md#BKMK_Topology) in this topic.

- A Microsoft Office 365 tenant with Skype for Business Online enabled.

    > [!NOTE]
    > You can use only a single tenant for a hybrid configuration with your on-premises deployment.

- Skype for Business Server administrative tools. (If you are using Lync Server 2013 or Lync Server 2010, you can use the Lync Server 2013 administrative tools. For more information, see [Lync Server 2013 hybrid](https://go.microsoft.com/fwlink/p/?LinkId=617360).)

- Azure Active Directory Connect to synchronize your on-premises directory with Office 365. For more information, see [Azure AD Connect: Accounts and permissions](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).

    To support Single Sign-on with Office 365 so that users can use the same login credentials as they do for on premises, you can use the password sync features of Azure Active Directory (AAD) Connect. You can also use Active Directory Federation Services (AD FS) for single sign-on with Office 365.

To configure hybrid connectivity, you will also need to set up federation between your on-premises and online environments, and configure your Skype for Business Online tenant for a shared Session Initiation Protocol (SIP) address space. For more information about the steps required to configure hybrid connectivity, see [Configure hybrid connectivity](configure-hybrid-connectivity.md).

After you configure hybrid connectivity, you can move users to Skype for Business Online or Teams. For more information, see [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md) and [Move users from on-premises to Teams](move-users-from-on-premises-to-teams.md).

## Multi-forest support
<a name="BKMK_MultiForest"> </a>

Users can access Skype for Business functionality in another forest if the following requirements are met:

- Users are properly synchronized into the forest that hosts Skype for Business: In hybrid configurations, this means that users must be synchronized as disabled user objects.

- The forest hosting Skype for Business must trust the forest containing the users.

For details on multi-forest hybrid scenarios, see [Configure a multi-forest environment for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid.md).

## Administrator credentials
<a name="BKMK_Credentials"> </a>

When you are asked to provide your administrator credentials, use the username and password for the administrator account for your Office 365 tenant. You will also use these credentials when you configure Azure Active Directory for federation, directory synchronization, single sign-on, and moving users to Skype for Business Online.

## Skype for Business Online PowerShell
<a name="BKMK_PowerShell"> </a>

Administrators now have the ability to use Windows PowerShell to manage Skype for Business Online and their Skype for Business Online user accounts. To do this, you must first download and install the Skype for Business Online Connector Module from the Microsoft Download Center. For more information on downloading, installing, and using the Skype for Business Online Connector Module, and for detailed information on using Windows PowerShell to manage Skype for Business Online, see [Set up your computer for Windows PowerShell](https://technet.microsoft.com/library/dn362831.aspx).

## Skype for Business client support
<a name="BKMK_ClientSupport"> </a>

There are some differences in the features supported in clients, as well as the features available in on-premises and online environments. The following clients are supported with Skype for Business Online in a hybrid deployment:

- Skype for Business

- Lync 2013

- Lync 2010

- Lync Windows Store app

- Lync Web App

- Lync Mobile

- Lync for Mac 2011

- Lync Room System and Skype for Business Room System

- Lync Basic 2013

- Microsoft Surface Hub

Before you decide where you want to home users in your organization, you should review the [Desktop client feature comparison for Skype for Business](../../sfbserver/plan-your-deployment/clients-and-devices/desktop-feature-comparison.md) to determine the client support for the various configurations of Skype for Business Server. See also:

- [Plan for clients and devices](../../sfbserver/plan-your-deployment/clients-and-devices/clients-and-devices.md)

- [Mobile client feature comparison for Skype for Business](../../sfbserver/plan-your-deployment/clients-and-devices/mobile-feature-comparison.md)

## Topology requirements
<a name="BKMK_Topology"> </a>

To configure your deployment for hybrid with Skype for Business Online, you need to have one of the following supported topologies:

- A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.

- A Lync Server 2013 deployment with all servers running Lync Server 2013.

    For hybrid voice connectivity, the Edge Server that is designated as Federation Edge must be Skype for Business 2015; the Edge also requires a Skype for Business Server backend. You might have a pool with no users on it.

- A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates.

  - The federation Edge Server and next hop server from the federation Edge Server must be running Lync Server 2010 with the latest cumulative updates.

  - The Skype for Business Server 2015 or Lync Server 2013 Administrative Tools must be installed on at least one server or management workstation.

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

## Federation Allowed/Blocked Lists requirements
<a name="BKMK_Federation"> </a>

The Allowed domains list includes domains that have a partner Edge fully qualified domain name (FQDN) configured. These are sometimes referred to as allowed partner servers or direct federation partners. You should be familiar with the difference between Open Federation and Closed Federation, referred to as partner discovery and allowed partner domain list, respectively, in on-premises deployments.

The following requirements must be met to successfully configure a hybrid deployment:

- Domain matching must be configured the same for your on-premises deployment and your Office 365 tenant. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online tenant. If partner discovery is not enabled, then closed federation must be configured for your online tenant.

- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.

- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.

- Federation must be enabled for the external communications for the online tenant, which is configured by using the Skype for Business Online Control Panel.

## DNS settings
<a name="BKMK_DNS"> </a>

When creating DNS records for hybrid deployments, all Skype for Business external DNS records should point to the on-premises infrastructure. For details on required DNS records, please refer to [DNS requirements for Skype for Business Server](../../sfbserver/plan-your-deployment/network-requirements/dns.md).

Additionally, you need to ensure that the DNS resolution described in the following table works in your on-premises deployment:

|DNS record  <br/> |Resolvable by  <br/> |DNS requirement  <br/> |
|:-----|:-----|:-----|
|DNS SRV record for _sipfederationtls._tcp.\<sipdomain.com\> for all supported SIP domains resolving to Access Edge external IP(s)  <br/> |Edge server(s)  <br/> |Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.  <br/> Must use strict DNS name matching between the domain in the user name and the SRV record.  <br/> |
|DNS A record(s) for Edge Web Conferencing Service FQDN, e.g. webcon.contoso.com resolving to Web Conferencing Edge external IP(s)  <br/> |Internal corporate network connected users' computers  <br/> |Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.  <br/> |

Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.

## Firewall considerations
<a name="BKMK_Firewall"> </a>

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.

Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from \*.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.

For more information, see [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/p/?LinkId=252942).

## Port and protocol requirements
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
