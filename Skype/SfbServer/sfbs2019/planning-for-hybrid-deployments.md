---
title: "Planning for Lync Server 2013 hybrid deployments"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: f8b3d240-bc2e-42c9-acf8-d532d641a14c
description: "In this articleInfrastructure RequirementsLync Client SupportTopology RequirementsRequirements for Federation Allowed/Blocked ListsDNS SettingsFirewall ConsiderationsPort and Protocol RequirementsUser Accounts and DataUser Policies and Features"
---

# Planning for Lync Server 2013 hybrid deployments
[]
 **In this article**
  
[Infrastructure Requirements](#sectionSection0)
  
[Lync Client Support](#sectionSection1)
  
[Topology Requirements](#BKMK_Topology)
  
[Requirements for Federation Allowed/Blocked Lists](#sectionSection3)
  
[DNS Settings](#sectionSection4)
  
[Firewall Considerations](#sectionSection5)
  
[Port and Protocol Requirements](#b)
  
[User Accounts and Data](#sectionSection7)
  
[User Policies and Features](#sectionSection8)
  
You should consider the following requirements for users and your network infrastructure while planning for a hybrid deployment.
  
## Infrastructure Requirements
<a name="sectionSection0"> </a>

You must have the following configured in your environment in order to implement and deploy a hybrid deployment.
  
- A Microsoft Office 365 tenant with Skype for Business Online enabled. Note that you can use only a single tenant for a hybrid configuration with your on-premises deployment.
    
- A single on-premises deployment (infrastructure) of Skype for Business Server or Lync Server that is deployed in a supported topology. See [Topology Requirements](planning-for-hybrid-deployments.md#BKMK_Topology).
    
    For information about configuring your Lync Server 2013 or Lync Server 2010 deployment for hybrid, see [Configuring Lync Server 2013 hybrid deployments](configuring-hybrid-deployments.md).
    
- Skype for Business Server 2015 administrative tools. If you are using Lync Server 2013 or Lync Server 2010, you can use the Lync Server 2013 administrative tools. 
    
- To support Single Sign-on with Office 365 so that users can use the same login credentials for signing in to Office as they do on-premises, you can use the password sync features of Azure Active Directory (AAD) Connect. You can also use Active Directory Federation Services (AD FS) for single sign-on with Office 365. 
    
    For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=619754).
    
- A single directory synchronization solution to keep your on-premises and online Active Directory objects synchronized. For details about Directory Synchronization, see [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkId=530320).
    
## Lync Client Support
<a name="sectionSection1"> </a>

There are some differences in the features supported in Lync clients, as well as the features available in on-premises and online environments. Before you decide where you want to home users in your organization, you can view the client support for the various configurations of Lync Server. The following clients are supported with Skype for Business Online in a Lync hybrid deployment:
  
- Lync 2010
    
- Lync 2013
    
- Lync Windows Store app
    
- Lync Web App
    
- Lync Mobile
    
- Lync for Mac 2011
    
- Lync Room System
    
- Lync Basic 2013
    
For details about client support, see the following topics:
  
- [Clients for Lync Online](https://go.microsoft.com/fwlink/?LinkId=281902)
    
- [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md)
    
- [Mobile client comparison tables for Lync Server 2013](mobile-client-comparison-tables.md)
    
## Topology Requirements
<a name="BKMK_Topology"> </a>

To configure your deployment for hybrid with Skype for Business Online, you need to have one of the following supported topologies:
  
- A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.
    
- A Lync Server 2013 deployment with all servers running Lync Server 2013.
    
- A Lync Server 2010 deployment with all servers running Lync Server 2010 with the latest cumulative updates.
    
  - The federation Edge Server and next hop server from the federation Edge Server must be running Lync Server 2010 with the latest cumulative updates.
    
  - The Skype for Business Server 2015 or Lync Server 2013 Administrative Tools must be installed on at least one server or management workstation.
    
- A mixed Lync Server 2013 and Skype for Business Server 2015 deployment with the following server roles in at least one site running Skype for Business Server 2015:
    
  - At least one Enterprise Pool or Standard Edition server 
    
  - The Director Pool associated with SIP federation, if it exists
    
  - The Edge Pool associated with SIP federation
    
- A mixed Lync Server 2010 and Skype for Business Server 2015 deployment with the following servers roles in at least one site running Skype for Business Server 2015:
    
  - At least one Enterprise Pool or Standard Edition server 
    
  - The Director Pool associated with SIP federation, if it exists
    
  - The Edge Pool associated with SIP federation for the Site
    
- A mixed Lync Server 2010 and Lync Server 2013 deployment with the following server roles in at least one site running Lync Server 2013:
    
  - At least one Enterprise Pool or Standard Edition server in the site
    
  - The Director Pool associated with SIP federation, if it exists in the site
    
  - The Edge Pool associated with SIP federation for the site
    
> [!IMPORTANT]
> All user management, including user moves between on-premises and UNRESOLVED_TOKEN_VAL(skypeforbusiness) Online, needs to be done using the latest installed version of the administrative tools. The administrative tools must be installed on a separate server that has connect access to the existing on-premises deployment and to the Internet. The [Move-CsUser](move-csuser.md) cmdlet to move users from your on-premises deployment to UNRESOLVED_TOKEN_VAL(skype16_online) must be run from the administrative tools connected to your on-premises deployment. 
  
For more information about supported topologies, see [Supported topologies in Lync Server 2013](supported-topologies.md), and [Lync Server 2013 Reference Topologies for Enterprise Hybrid Deployments](https://go.microsoft.com/fwlink/p/?LinkId=398709). 
  
For troubleshooting information about hybrid deployments and connecting PowerShell to Lync Online, see [Lync Online: Lync PowerShell and Hybrid Troubleshooting](https://go.microsoft.com/fwlink/p/?LinkId=306718).
  
## Requirements for Federation Allowed/Blocked Lists
<a name="sectionSection3"> </a>

The Allowed domains list includes domains that have a partner Edge fully qualified domain name (FQDN) configured. These are sometimes referred to as allowed partner servers or direct federation partners. You should be familiar with the difference between Open Federation and Closed Federation, referred to as partner discovery and allowed partner domain list, respectively, in on-premises deployments.
  
The following requirements must be met to successfully configure a hybrid deployment:
  
- Domain matching must be configured the same for your on-premises deployment and your Office 365 tenant. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online tenant. If partner discovery is not enabled, then closed federation must be configured for your online tenant.
    
- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.
    
- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.
    
- Federation must be enabled for the external communications for the online tenant, which is configured by using the Lync Online Control Panel.
    
## DNS Settings
<a name="sectionSection4"> </a>

When creating DNS records for hybrid deployments, all Lync external DNS records should point to the on-premises infrastructure. For details on required DNS records, please refer to [Domain Name System (DNS) requirements for Lync Server 2013](domain-name-system-dns-requirements.md).
  
Additionally you need to ensure that the DNS resolution described in the following table works in your on-premises deployment:
  
||||
|:-----|:-----|:-----|
|DNS record  <br/> |Resolvable by  <br/> |DNS requirement  <br/> |
|DNS SRV record for _sipfederationtls._tcp.\<sipdomain.com\> for all supported SIP domains resolving to Access Edge external IP(s)  <br/> |Edge server(s)  <br/> |Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.  <br/> Must use strict DNS name matching between the domain in the user name and the SRV record.  <br/> |
|DNS A record(s) for Edge Web Conferencing Service FQDN, e.g. webcon.contoso.com resolving to Web Conferencing Edge external IP(s)  <br/> |Internal corporate network connected users' computers  <br/> |Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.  <br/> |
   
Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.
  
## Firewall Considerations
<a name="sectionSection5"> </a>

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.
  
Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from \*.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.
  
Refer to the Help topic [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/p/?LinkId=252942).
  
## Port and Protocol Requirements
<a name="b"> </a>

In addition to the port requirements for internal Lync Server 2013 communication, you must also configure the following ports.
  
|**Protocol / Port**|**Applications**|
|:-----|:-----|
|TCP 443  <br/> | Open inbound  <br/>  Active Directory Federation Services (federation server role)  <br/>  For more information, see [Understanding AD FS Role Services](https://go.microsoft.com/fwlink/p/?LinkId=281899).  <br/>  Active Directory Federation Services (proxy server role)  <br/>  Microsoft Online Services Portal  <br/>  My Company Portal  <br/>  Outlook Web App  <br/>  Lync client (communication to Lync Online from on-premises Lync Server)  <br/> |
|TCP 80 and 443  <br/> | Open inbound  <br/>  Microsoft Online Services Directory Synchronization Tool  <br/> |
|TCP 5061  <br/> |Open inbound/outbound on the Edge Server  <br/> |
|PSOM/TLS 443  <br/> |Open inbound/outbound for data sharing sessions  <br/> |
|STUN/TCP 443  <br/> |Open inbound/outbound for audio, video, application sharing sessions  <br/> |
|STUN/UDP 3478  <br/> |Open inbound/outbound for audio and video sessions  <br/> |
|RTP/TCP 50000-59999  <br/> |Open outbound for audio and video sessions  <br/> |
   
## User Accounts and Data
<a name="sectionSection7"> </a>

In a Lync Server 2013 hybrid deployment, any user that you want to home in Lync Online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services. You can then move the user to Skype for Business Online, which will move the user's contact list.
  
When you synchronize user accounts between your Lync on-premises and Lync Online deployments with AD FS and Dirsync, you need to synchronize the AD accounts for all Lync users in your organization between your on-premises and online Lync deployments, even if users are not moved to Lync Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.
  
> [!IMPORTANT]
> If the user is created by using the online portal for Office 365, the user account will not be synchronized with on-premises Active Directory, and the user will not exist in the on-premises Active Directory. If you have already created users in Lync Online, and want to configure hybrid with an on-premises Lync Server, see [Moving users from Lync Online to Lync on-premises in Lync Server 2013](moving-users-from-lync-online-to-lync-on-premises.md). 
  
You should also consider the following user-related issues when planning for a hybrid deployment.
  
- **User contacts** The limit for contacts for Lync Online users is 250. Any contacts beyond that number will be removed from the user's contact list when the account is moved to Lync Online. 
    
- **Instant Messaging and Presence** User contact lists, groups, and access control lists (ACLs) are migrated with the user account. 
    
- **Conferencing data, meeting content, and scheduled meetings** This content is not migrated with the user account. Users must reschedule meetings after their accounts are migrated to Lync Online. 
    
## User Policies and Features
<a name="sectionSection8"> </a>

- In a Lync Server 2013 hybrid environment, users can be enabled for Instant Messaging, voice, and meetings either on-premises or online, but not both simultaneously.
    
- **Lync Client** Some users may require a new client version when they are moved to Lync Online. For Office Communications Server 2007 R2, users must be moved to a Lync Server 2013 pool prior to migration to Lync Online. 
    
    For more information about client support, see [Clients for Lync Online](https://go.microsoft.com/fwlink/p/?LinkId=281902) and [Supported Lync clients and network port configurations](https://go.microsoft.com/fwlink/p/?LinkId=281901).
    
- **On-premises policies and configuration (non-user)** Online and on-premises policies require separate configuration. You cannot set global policies that apply to both. 
    

