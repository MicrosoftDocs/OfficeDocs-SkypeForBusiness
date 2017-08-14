---
title: Plan hybrid connectivity between Skype for Business Server and Skype for Business Online
ms.prod: SKYPEFORBUSINESS
ms.assetid: f8b3d240-bc2e-42c9-acf8-d532d641a14c
---


# Plan hybrid connectivity between Skype for Business Server and Skype for Business Online
[] **Summary:** Read this topic to learn how to plan hybrid connectivity between Skype for Business Server and Skype for Business Online.
Hybrid connectivity between Skype for Business Server and Skype for Business Online means users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Skype for Business Online. Some of the domain users are homed on premises, and some users are homed online. 
  
    
    

You can configure your on-premises deployment for hybrid with Skype for Business Online and use Active Directory Synchronization to keep your on-premises and online users synchronized. You can also configure hybrid deployments for integration with on-premises Exchange and SharePoint, or with Microsoft Office 365 applications, including Exchange Online and SharePoint Online. For more information about planning your hybrid deployment, see  [Plan your hybrid deployment for Skype for Business](plan-your-hybrid-deployment-for-skype-for-business.md).
With a Skype for Business Server hybrid deployment, users in your organization who are homed online can take advantage of Microsoft's Cloud PBX technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Skype for Business Online. For more information about Cloud PBX, see  [Plan your Cloud PBX solution in Skype for Business](plan-your-cloud-pbx-solution-in-skype-for-business.md).
  
    
    


## About this topic

This topic describes the infrastructure and system requirements you'll need to configure your existing on-premises deployment with Skype for Business Online. This topic describes an on-premises deployment with users who were created in your on-premises Active Directory. For more information about deploying hybrid connectivity, see  [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](deploy-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busin.md). 
  
    
    
If you are currently a Skype for Business Online customer who has users enabled for Skype for Business Online who have not been enabled in an on-premises deployment, see  [Configure hybrid from online to on-premises in Skype for Business Server 2015](configure-hybrid-from-online-to-on-premises-in-skype-for-business-server-2015.md).
  
    
    

## Administrator credentials

When you are asked to provide your administrator credentials, use the username and password for the administrator account for your Office 365 tenant. You will also use these credentials when you configure Azure Active Directory for federation, directory synchronization, single sign-on, and moving users to Skype for Business Online.
  
    
    

## Connecting to Skype for Business Online PowerShell

Administrators now have the ability to use Windows PowerShell to manage Skype for Business Online and their Skype for Business Online user accounts. To do this, you must first download and install the Skype for Business Online Connector Module from the Microsoft Download Center. For more information on downloading, installing, and using the Skype for Business Online Connector Module, and for detailed information on using Windows PowerShell to manage Skype for Business Online, see  [Using Windows PowerShell to Manage Lync Online](http://technet.microsoft.com/library/9ef2d853-10fb-4e02-a552-dcf6818d7153.aspx). Updated information for Skype for Business Online coming soon.
  
    
    

## Infrastructure requirements

You must have the following configured in your environment in order to implement and deploy a hybrid deployment.
  
    
    

- A Microsoft Office 365 tenant with Skype for Business Online enabled. Note that you can use only a single tenant for a hybrid configuration with your on-premises deployment.
    
  
- A single on-premises deployment (infrastructure) of Skype for Business Server or Lync Server that is deployed in a supported topology. See  [Topology requirements](plan-hybrid-connectivity-between-skype-for-business-server-and-skype-for-busines.md#BKMK_Topology).
    
    For information about configuring your Lync Server 2013 or Lync Server 2010 deployment for hybrid, see  [Lync Server 2013 hybrid](https://go.microsoft.com/fwlink/p/?LinkId=617360).
    
  
- Skype for Business Server 2015 administrative tools. If you are using Lync Server 2013 or Lync Server 2010, you can use the Lync Server 2013 administrative tools. Please see  [Lync Server 2013 hybrid](https://go.microsoft.com/fwlink/p/?LinkId=617360) for more information.
    
  
- To support Single Sign-on with Office 365 so that users can use the same login credentials for signing in to Office as they do on-premises, you can use the password sync features of Azure Active Directory (AAD) Connect. You can also use Active Directory Federation Services (AD FS) for single sign-on with Office 365. 
    
    For more information, see  [Connect Active Directory with Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-accounts-permissions).
    
  
- For details on multi-forest hybrid scenarios, see  [Configure a multi-forest environment for hybrid Skype for Business](configure-a-multi-forest-environment-for-hybrid-skype-for-business.md).
    
  
- For details on co-existence with Exchange Server, including support criteria and limitations in various combinations of on-premises and online, see  [Feature support](plan-to-integrate-skype-for-business-and-exchange.md#feature_support) in [Plan to integrate Skype for Business and Exchange](plan-to-integrate-skype-for-business-and-exchange.md).
    
  

## Skype for Business client support

There are some differences in the features supported in clients, as well as the features available in on-premises and online environments. Before you decide where you want to home users in your organization, you should review the  [Desktop client comparison tables for Skype for Business](desktop-client-comparison-tables-for-skype-for-business.md) to determine the client support for the various configurations of Skype for Business Server. The following clients are supported with Skype for Business Online in a hybrid deployment:
  
    
    

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
    
  
For details about client support, see the following topics:
  
    
    

-  [Desktop client comparison tables for Skype for Business](desktop-client-comparison-tables-for-skype-for-business.md)
    
  
-  [Mobile client comparison tables for Skype for Business](mobile-client-comparison-tables-for-skype-for-business.md)
    
  
-  [Plan for clients and devices](plan-for-clients-and-devices.md)
    
  

## Topology requirements
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
> All user management, including user moves between on-premises and Skype for Business Online, needs to be done using the latest installed version of the administrative tools. The administrative tools must be installed on a separate server that has connect access to the existing on-premises deployment and to the Internet. The  [Move-CsUser](move-csuser.md) cmdlet to move users from your on-premises deployment to Skype for Business Online must be run from the administrative tools connected to your on-premises deployment.
  
    
    


## Requirements for Federation Allowed/Blocked Lists
<a name="BKMK_Topology"> </a>

The Allowed domains list includes domains that have a partner Edge fully qualified domain name (FQDN) configured. These are sometimes referred to as allowed partner servers ordirect federation partners. You should be familiar with the difference between Open Federation and Closed Federation, referred to as partner discovery andallowed partner domain list, respectively, in on-premises deployments.
  
    
    
The following requirements must be met to successfully configure a hybrid deployment:
  
    
    

- Domain matching must be configured the same for your on-premises deployment and your Office 365 tenant. If partner discovery is enabled on the on-premises deployment, then open federation must be configured for your online tenant. If partner discovery is not enabled, then closed federation must be configured for your online tenant.
    
  
- The Blocked domains list in the on-premises deployment must exactly match the Blocked domains list for your online tenant.
    
  
- The Allowed domains list in the on-premises deployment must exactly match the Allowed domains list for your online tenant.
    
  
- Federation must be enabled for the external communications for the online tenant, which is configured by using the Skype for Business Online Control Panel.
    
  

## DNS settings
<a name="BKMK_Topology"> </a>

When creating DNS records for hybrid deployments, all Skype for Business external DNS records should point to the on-premises infrastructure. For details on required DNS records, please refer to  [DNS requirements for Skype for Business](dns-requirements-for-skype-for-business.md).
  
    
    
Additionally you need to ensure that the DNS resolution described in the following table works in your on-premises deployment:
  
    
    

||||
|:-----|:-----|:-----|
|DNS record  <br/> |Resolvable by  <br/> |DNS requirement  <br/> |
|DNS SRV record for _sipfederationtls._tcp.<sipdomain.com> for all supported SIP domains resolving to Access Edge external IP(s)  <br/> |Edge server(s)  <br/> |Enable federated communication in a hybrid configuration. The Edge Server needs to know where to route federated traffic for the SIP domain that is split between on premises and online.  <br/> Must use strict DNS name matching between the domain in the user name and the SRV record.  <br/> |
|DNS A record(s) for Edge Web Conferencing Service FQDN, e.g. webcon.contoso.com resolving to Web Conferencing Edge external IP(s)  <br/> |Internal corporate network connected users' computers  <br/> |Enable online users to present or view content in on-premises hosted meetings. Content includes PowerPoint files, whiteboards, polls, and shared notes.  <br/> |
   
Depending on how DNS is configured in your organization, you may need to add these records to the internal hosted DNS zone for the corresponding SIP domain(s) to provide internal DNS resolution to these records.
  
    
    

## Firewall considerations
<a name="BKMK_Topology"> </a>

Computers on your network must be able to perform standard Internet DNS lookups. If these computers can reach standard Internet sites, your network meets this requirement.
  
    
    
Depending on the location of your Microsoft Online Services data center, you must also configure your network firewall devices to accept connections based on wildcard domain names (for example, all traffic from *.outlook.com). If your organization's firewalls do not support wildcard name configurations, you will have to manually determine the IP address ranges that you would like to allow and the specified ports.
  
    
    
For more information, see  [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/p/?LinkId=252942).
  
    
    

## Port and protocol requirements
<a name="BKMK_Topology"> </a>

In addition to the port requirements for internal communication, you must also configure the following ports to enable hybrid connectivity:
  
    
    

|
|
|**Protocol**|**TCP or UDP**|**Source IP**|**Destination IP**|**Source Port**|**Destination Port**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|SIP (MTLS)  <br/> |TCP  <br/> |Access Edge  <br/> |Office 365  <br/> |Any  <br/> |5061  <br/> |Signaling  <br/> |
|SIP (MTLS)  <br/> |TCP  <br/> |Office 365  <br/> |Access Edge  <br/> |Any  <br/> |5061  <br/> |Signaling  <br/> |
|STUN  <br/> |TCP  <br/> |A/V Edge  <br/> |Office 365  <br/> |50000-59999  <br/> |443, 50000-59999  <br/> |Open for audio, video, application sharing sessions  <br/> |
|STUN  <br/> |TCP  <br/> |Office 365  <br/> |A/V Edge  <br/> |443  <br/> |50000-59999  <br/> |Open for audio, video, application sharing sessions  <br/> |
|STUN  <br/> |UDP  <br/> |A/V Edge  <br/> |Office 365  <br/> |3478  <br/> |3478  <br/> |Open for audio, video sessions  <br/> |
|STUN  <br/> |UDP  <br/> |Office 365  <br/> |A/V Edge  <br/> |3478  <br/> |3478  <br/> |Open for audio, video sessions  <br/> |
   

  
    
    
For more information about port and firewall planning for Edge Server, see  [Edge Server environmental requirements in Skype for Business Server 2015](edge-server-environmental-requirements-in-skype-for-business-server-2015.md).
  
    
    

## User accounts and data
<a name="BKMK_Topology"> </a>

In a hybrid deployment, any user that you want to home online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services. You can then move the user to Skype for Business Online, which will move the user's contact list.
  
    
    
When you synchronize user accounts between your on-premises deployment and online tenant using AAD Connect, you need to synchronize the AD accounts for all Skype for Business or Lync users in your organization, even if users are not moved to online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.
  
    
    

> [!IMPORTANT]
> If the user was created by using the online portal for Office 365, the user account will not be synchronized with on-premises Active Directory, and the user will not exist in the on-premises Active Directory. If you have already created users in your online tenant, and want to configure hybrid with an on-premises deployment, see  [Configure hybrid from online to on-premises in Skype for Business Server 2015](configure-hybrid-from-online-to-on-premises-in-skype-for-business-server-2015.md). 
  
    
    

You should also consider the following user-related issues when planning for a hybrid deployment.
  
    
    

- **User contacts** The limit for contacts for Lync Online users is 250. Any contacts beyond that number will be removed from the user's contact list when the account is moved to Lync Online.
    
  
- **Instant Messaging and Presence** User contact lists, groups, and access control lists (ACLs) are migrated with the user account.
    
  
- **Conferencing data, meeting content, and scheduled meetings** This content is not migrated with the user account. Users must reschedule meetings after their accounts are migrated to Lync Online.
    
  

## User policies and features
<a name="BKMK_Topology"> </a>


- In a hybrid environment, users can be enabled for Instant Messaging and conferencing (meetings) either on premises or online, but not both simultaneously.
    
  
- **Client support** Some users may require a new client version when they are moved to Skype for Business Online. For Office Communications Server 2007 R2, users must be moved to a Skype for Business Server or Lync Server 2013 pool prior to migration to Skype for Business Online.
    
  
- **On-premises policies and configuration (non-user)** Online and on-premises policies require separate configuration. You cannot set global policies that apply to both.
    
  

