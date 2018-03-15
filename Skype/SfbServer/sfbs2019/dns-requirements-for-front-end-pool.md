---
title: "DNS requirements for Front End pool in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/16/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 02d2aa6b-9e01-437b-a2df-00590280150d
description: "To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# DNS requirements for Front End pool in Lync Server 2013
[]
To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group.
  
You need to configure the required Domain Name System (DNS) records prior to publishing your topology in Topology Builder. Additionally, some of the fully qualified domain names (FQDNs) used in the configuration of a Lync Server 2013 deployment are logical and not physical server FQDNs, so additional DNS configuration is required prior to publishing. 
  
> [!CAUTION]
> Lync Server 2013 does not support single-labeled domains. For example, a forest with a root domain named **contoso.local** is supported, but a root domain named **local** is not supported. For details, see Microsoft Knowledge Base article 300684, "Information about configuring Windows for domains with single-label DNS names," at [https://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=300684](https://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=300684). 
  
> [!IMPORTANT]
> The name you specify must be identical to the computer name configured on the server. By default the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. **Use only standard characters** (including A-Z, a-z, 0-9, and hyphens) when assigning FQDNs of your servers running Lync Server, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public certification authorities (CAs) (when the FQDN must be assigned to the SN in the certificate). 
  
Prior to operating the topology after it has been deployed, ensure that the following Active Directory and DNS records are created (as your needs for specific features dictate):
  
- Each server role that will exist in the topology is published as an Active Directory object (joining the computer to the domain will accomplish this).
    
- A DNS A Record exists for each server.
    
- A DNS SRV Record exists for each SIP domain if you plan to use automatic logon for clients in the form of _sipinternaltls_tcp. _\<SIP domain\>_. If you will use manual configuration for clients, this record is not necessary.
    
- A DNS A Record for each configured simple URL, of which there are typically four: meet, dialin, lwa, and scheduler. Additionally, there is the admin simple URL which is a special URL for access to the Lync Server 2013 Control Panel.
    
- The server running SQL Server must be joined to the domain, and reachable by the computer that Topology Builder is publishing from.
    
The table follows the reference architectures presented in the Planning section. For details, see [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md) in the Planning documentation. 
  
**DNS Records Required for the Front End pool**

|**Location**|**Type**|**FQDN**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|Internal DNS  <br/> |A  <br/> |pool01.contoso.net  <br/> |Pool01 (DNS load balancing). Requires a DNS A record for the IP address of each Front End Server within the pool, mapping to the pool FQDN.  <br/> |
|Internal DNS  <br/> |A  <br/> |pool01.contoso.net  <br/> |Pool01 (virtual IP (VIP) of hardware load balancer).  <br/> |
|Internal DNS  <br/> |A  <br/> |fe01.contoso.net  <br/> fe02.contoso.net  <br/> fe03.contoso.net  <br/> …  <br/> |Pool01 Front End Server (NODE 1).  <br/> Pool01 Front End Server (NODE 2).  <br/> Pool01 Front End Server (NODE 3).  <br/> …  <br/> |
|Internal DNS  <br/> |A  <br/> |fe02.contoso.net  <br/> |Pool01 Front End Server (NODE 2).  <br/> |
|Internal DNS  <br/> |A  <br/> |lsweb.contoso.net  <br/> |Pool01 (VIP) for client-to-server web traffic.  <br/> |
|Internal DNS  <br/> |A  <br/> |sqlbe.contoso.net  <br/> |Pool01 Back End Server running SQL Server 2008 R2.  <br/> |
|Internal DNS  <br/> |A  <br/> |sip.contoso.com  <br/> |Required for Lync Phone Edition, or automatic logon of clients without DNS SRV records, and for strict domain matching. Not required in all cases.  <br/> |
|Internal DNS  <br/> |A  <br/> |sip.fabrikam.com  <br/> |Assumes a second SIP domain. Required for Lync Phone Edition, automatic logon of clients without DNS SRV records, and for strict domain matching. Not required in all cases.  <br/> |
|Internal DNS  <br/> |A  <br/> |dialin.contoso.com  <br/> |Simple URL for dial-in conferencing published internally - Front End Server (or Director, if installed) responds to simple URL queries.  <br/> |
|Internal DNS  <br/> |A  <br/> |meet.contoso.com  <br/> |Simple URL for conferences published internally - Front End Server (or Director, if installed) responds to simple URL queries.  <br/> |
|Internal DNS  <br/> |A  <br/> |admin.contoso.com  <br/> admin  <br/> |Optional record, simple URL for Lync Server 2013 Control Panel published internally - Front End Server (or Director, if installed) responds to simple URL queries. Host name only (no domain name) is recommended.  <br/> |
   
> [!NOTE]
> VIP = Virtual IP address for hardware load balancer 
  
## DNS SRV Records for the Front End pool

|**Location**|**Type**|**FQDN**|**Target FQDN**|**Port**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Internal DNS  <br/> |SRV  <br/> |_sipinternaltls._tcp.contoso.com  <br/> |pool01.contoso.com  <br/> |5061  <br/> |Required for automatic configuration of Lync 2013 clients to work internally.  <br/> |
|Internal DNS  <br/> |SRV  <br/> |_sipinternaltls._tcp.fabrikam.com  <br/> |pool01.fabrikam.com  <br/> |5061  <br/> |Required for automatic configuration of Lync 2013 clients to work internally.  <br/> |
|Internal DNS  <br/> |SRV  <br/> |_ntp._udp.contoso.com  <br/> |dc01.contoso.com  <br/> |123  <br/> |Network Time Protocol (NTP) source required for devices running Lync Phone Edition. Internally, this should point to the domain controller. If the domain controller is not defined, it will try to use the NTP server time.windows.com.  <br/> |
   

