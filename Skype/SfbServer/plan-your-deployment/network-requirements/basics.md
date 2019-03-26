---
title: "DNS basics"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2618cfa1-2e2c-4f1d-a5e5-70a0286591a7
description: "Windows Server 2016 has built-in software that can provide DNS services, so you may want to review the available documentation such as the DNS Policy Scenario Guide. You can choose a third-party solution if you prefer."
---

# DNS basics
 
Windows Server 2016 has built-in software that can provide DNS services, so you may want to review the available documentation such as the [DNS Policy Scenario Guide](https://docs.microsoft.com/windows-server/networking/dns/deploy/dns-policy-scenario-guide). You can choose a third-party solution if you prefer.
  
We recommend that as a best practice you dedicate a specific server in your implementation to provide DNS. You could potentially set it up on one of the servers dedicated to one of the Skype for Business server roles, but if that server was also part of a pool and got decommissioned by accident Skype for Business would malfunction until DNS services were re-established.
  
## DNS Records

Each mapping of a name to an IP address (and that could be an IPv4 or IPv6 address) is stored in a DNS record on the DNS server. The name is described in the DNS Report specifically as an FQDN — a Fully Qualified Domain Name. While  *contoso.com*  is a valid domain name, it's shorthand for *\*.contoso.com*  , so it's ambiguous and could possibly refer to any server in the domain. An example of an FQDN that would refer to a single server in your domain might be **meeting01.contoso.com**.
  
> [!IMPORTANT]
> By default the computer name of a computer that is not joined to a domain is a host name, and not a fully qualified domain name (FQDN). Topology Builder uses FQDNs, not host names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. **Use only standard characters** (including A-Z, a-z, 0-9, and hyphens) when assigning FQDNs to your servers running Skype for Business Server. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (that is, when the FQDN must be assigned to the SN in the certificate).
  
In addition to an IP address, the FQDN could map to a **VIP** — A virtual IP address. A VIP is an IP address that doesn't correspond to an actual physical network interface. A VIP often points to a pool of servers performing a server role, or to a pair of servers configured for redundancy and fault-tolerance.
  
There are several types of DNS record, the ones that are most relevant to this discussion are: 
  
- **A** — an Address record or Host record, Returns a 32-bit IPv4 address. Most commonly used to map hostnames to an IP address of the host.
    
- **AAAA** — an IPv6 address record. Returns a 128-bit IPv6 address. Most commonly used to map hostnames to an IP address of the host.
    
- **CNAME** — a Canonical name record. This resolves one name to another: the DNS lookup will retry the lookup with the new name.
    
- **SRV** — a Service record (SRV record) specifies a service (a process on a server) that is accessed on a specific port and IP combination. The names of services requiring a service record are fixed, and can't be customized beyond making them part of your SIP domain. Some user services use Simple URLs. An SRV record must point to a location in the same SIP domain, so if you have multiple domains you'll need multiple SRV records for a given service.
    
## How to choose a SIP domain name
<a name="BK_NameSIP"> </a>

An organization's SIP domain name usually aligns with the email addresses given to its users. If a user in your organization would have an email address like Brown@contoso.com, the preferred \<sip-domain\> for an organization with the contoso.com domain name is simply contoso.com.
  
### Multiple SIP domains

 Your organization might in some cases need several SIP domains. As an example, if Fabrikam.com was acquired by contoso.com, you might need to create a new SIP domain that Skype for Business Server recognizes and will accept connection from. When you do this, you'd need to create an additional set of all the DNS records that use contoso.com, with new FQDNs that show where to send requests for Fabrikam.
  
## DNS Load Balancing
<a name="BK_NameSIP"> </a>

You can use DNS to share traffic load among several servers that are set up as a server pool. To do this, you would create several A records for the pool's FQDN, each of which points to the IP address of a node in the pool.
  
See [DNS load balancing](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#DNSLB) for additional discussions of load balancing.
  

