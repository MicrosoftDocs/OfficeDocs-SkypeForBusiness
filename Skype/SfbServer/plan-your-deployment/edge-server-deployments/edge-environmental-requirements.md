---
title: "Edge Server environmental requirements in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Hybrid
ms.custom:
ms.assetid: 67435465-b4d0-4e38-8e03-56a60b844a34

description: "Summary: Learn about the environmental requirements for Edge Server in Skype for Business Server."
---

# Edge Server environmental requirements in Skype for Business Server
 
**Summary:** Learn about the environmental requirements for Edge Server in Skype for Business Server.
  
A lot of planning and preparation needs to take place outside of the Skype for Business Server Edge Server environment itself. In this article, we'll review what preparations need to be made in the organizational environment, as per our list below:
  
- [Topology planning](edge-environmental-requirements.md#TopoPlan)
    
- [DNS planning](edge-environmental-requirements.md#DNSPlan)
    
- [Certificate planning](edge-environmental-requirements.md#CertPlan)
    
- [Port and firewall planning](edge-environmental-requirements.md#PortFirewallPlan)
    
## Topology planning
<a name="TopoPlan"> </a>

Skype for Business Server Edge Server topologies are able to use:
  
- Routable public IP addresses.
    
- Non-routable private IP addresses, if **symmetric** network address translation (NAT) is used.
    
> [!TIP]
> Your Edge Server can be configured to use a single IP address with distinct ports for each service, or it can use distinct IP addresses for each service, but use the same default port (which by default will be TCP 443). We have more information in IP Address requirements section, below. 
  
If you choose non-routable private IP addresses with NAT, remember these points:
  
- You need to use routable private IP addresses on **all three** external interfaces.
    
- You need to configure **symmetric** NAT for incoming and outgoing traffic. Symmetric NAT is the only supported NAT you can use with Skype for Business Server Edge Server.
    
- Configure your NAT to not change incoming source addresses. The A/V Edge service needs to be able to receive the incoming source address to find the optimal media path.
    
- Your Edge Servers need to be able to communicate with one another from their public A/V Edge IP addresses. Your firewall needs to allow this traffic.
    
- NAT can **only** be used for scaled consolidated Edge Servers if you use DNS load balancing. If you use hardware load balancing (HLB), you need to use publicly routable IP addresses **without** NAT.
    
You'll have no problems having your Access, Web conferencing and A/V Edge interfaces behind a router or firewall performing symmetric NAT for both single and scaled consolidated Edge Server topologies (as long as you're not using hardware load balancing).
  
### Summary of Edge Server topology options

We have several topology options available for Skype for Business Server Edge Server deployments:
  
- Single consolidated Edge with private IP addresses and NAT
    
- Single consolidated Edge with public IP addresses
    
- Scaled consolidated Edge with private IP addresses and NAT
    
- Scaled consolidated Edge with public IP addresses
    
- Scaled consolidated Edge with hardware load balancers
    
To help you choose one, we have the following table which gives a summary of what options you have for each topology:
  
|**Topology**|**High availability**|**Additional DNS records required for external Edge Server in the Edge pool?**|**Edge failover for Skype for Business Server sessions**|**Edge failover for Skype for Business Server federation sessions**|
|:-----|:-----|:-----|:-----|:-----|
|Single consolidated Edge with private IP addresses and NAT  <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Single consolidated Edge with public IP addresses  <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Scaled consolidated Edge with private IP addresses and NAT (DNS load balanced)  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes&sup1;  <br/> |
|Scaled consolidated Edge with public IP addresses (DNS load balanced)  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes&sup1;  <br/> |
|Scaled consolidated Edge with hardware load balancers  <br/> |Yes  <br/> |No (one DNS A record per VIP)  <br/> |Yes  <br/> |Yes  <br/> |
   
&sup1; Exchange Unified Messaging (UM) remote user failover using DNS load balancing requires Exchange 2013 or newer.
  
### IP Address requirements

On a fundamental level, three services need IP addresses; Access Edge service, Web Conferencing Edge service, and A/V Edge service. You have the option of either using three IP addresses, one for each of the services, or you can use one and opt to put each service on a different port (you can check out the [Port and firewall planning](edge-environmental-requirements.md#PortFirewallPlan) section for more information on some of that). For a single consolidated Edge environment, that's pretty much it.
  
> [!NOTE]
> As noted above, you can choose to have one IP address for all three services and run them on different ports. But to be clear, we don't recommend this. If your customers can't access the alternate ports you'd be using in this scenario, they can't access the full functionality of your Edge environment, either. 
  
It can be a little more complicated with scaled consolidated topologies, so let's look at some tables that lay out the IP Address requirements, keeping in mind that the primary decision points for topology selection are high availability and load balancing. High availability needs can influence your load balancing choice (we'll talk about that more after the tables).
  
#### IP Address requirements for scaled consolidated Edge (IP Address per role)

|**Number of Edge Servers per pool**|**Number of required IP addresses for DNS load balancing**|**Number of required IP addresses for hardware load balancing**|
|:-----|:-----|:-----|
|2  <br/> |6  <br/> |3 (1 per VIP) + 6  <br/> |
|3  <br/> |9  <br/> |3 (1 per VIP) + 9  <br/> |
|4  <br/> |12  <br/> |3 (1 per VIP) + 12  <br/> |
|5  <br/> |15  <br/> |3 (1 per VIP) +15  <br/> |
   
#### IP Address requirements for scale consolidated Edge (Single IP address for all roles)

|**Number of Edge Servers per pool**|**Number of required IP addresses for DNS load balancing**|**Number of required IP addresses for hardware load balancing**|
|:-----|:-----|:-----|
|2  <br/> |2  <br/> |1 (1 per VIP) + 2  <br/> |
|3  <br/> |3  <br/> |1 (1 per VIP) + 3  <br/> |
|4  <br/> |4  <br/> |1 (1 per VIP) + 4  <br/> |
|5  <br/> |5  <br/> |1 (1 per VIP) + 5  <br/> |
   
Let's look at some additional things to think about while planning.
  
- **High availability**: If you need high availability in your deployment, you should deploy at least two Edge Servers in a pool. It's worth noting that a single Edge pool will support up to 12 Edge Servers (though Topology Builder will allow you to add up to 20, that's not tested or supported, so we advise you don't do that). If you need more than 12 Edge Servers, you should create additional Edge pools for them.
    
- **Hardware load balancing**: We recommend DNS load balancing for most scenarios. Hardware load balancing is also supported, of course, but notably it's required for a single scenario over DNS load balancing:
    
  - External access to Exchange 2007 or Exchange 2010 (with no SP) Unified Messaging (UM).
    
- **DNS load balancing**: For UM, Exchange 2010 SP1 and newer are able to be supported by DNS load balancing. Note that if you need to go with DNS load balancing for an earlier version of Exchange, it'll work, but all the traffic for this will go to the first server in the pool, and if it's not available, that traffic will subsequently fail.
    
    DNS load balancing is also recommended if you're federating with companies using:
- Skype for Business Server 2015:
    - Lync Server 2010
    - Lync Server 2013
    - Microsoft Office O365
- Skype for Business Server 2019:
    - Lync Server 2013
    - Skype for Business Server 2015
    - Microsoft Office 365.
    
## DNS planning
<a name="DNSPlan"> </a>

When it comes to Skype for Business Server Edge Server deployment, it's vital to prepare for DNS properly. With the right records in place, the deployment will be much more straightforward. Hopefully you've chosen a topology in the section above, as we're going to do an overview, and then list a couple of tables outlining the DNS records for those scenarios. We'll also have some [Advanced Edge Server DNS planning for Skype for Business Server](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md) for more in-depth reading, if you need it.
  
### DNS records for Single consolidated Edge Server scenarios

These will be the DNS records you're going to need for a singe Edge Server using either public IPs or private IPs with NAT. Because this is sample data, we'll give example IPs so you can work out your own entries more easily:
  
- Internal network adapter: 172.25.33.10 (no default gateway's assigned)
    
    > [!NOTE]
    > Ensure that there is a route from the network containing the Edge internal interface to any networks that contain servers running Skype for Business Server or Lync Server 2013 clients (for example, from 172.25.33.0 to 192.168.10.0). 
  
- External network adapter:
    
  - Public IPs:
    
  - Access Edge: 131.107.155.10 (this is the primary, with default gateway set to your public router, ex: 131.107.155.1)
    
  - Web Conferencing Edge: 131.107.155.20 (secondary)
    
  - A/V Edge: 131.107.155.30 (secondary)
    
  Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
    
  - Private IPs:
    
  - Access Edge: 10.45.16.10 (this is the primary, with default gateway set to your router, ex: 10.45.16.1)
    
  - Web Conferencing Edge: 10.45.16.20 (secondary)
    
  - A/V Edge: 10.45.16.30 (secondary)
    
Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
  
> [!TIP]
>There are other possible configurations here:
  
- You could use one IP address on the external network adapter. We don't recommend this because then you're going to need to differentiate between the thee services using different ports (which you can do in Skype for Business Server) but there are some firewalls that may block the alternate ports. See the [Port and firewall planning](edge-environmental-requirements.md#PortFirewallPlan) section for more about this.
    
- You can have three external network adapters instead of one, and assign one of the service IPs to each one. Why do this? It would separate the services and if something goes wrong, that would make it easier to troubleshoot, and potentially let your other services continue working while you resolve an issue.
    
|**Location**|**Type**|**Port**|**FQDN or DNS record**|**IP address or FQDN**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|External DNS  <br/> |A record  <br/> |NA  <br/> |sip.contoso.com  <br/> |**public:** 131.107.155.10 <br/> **private:** 10.45.16.10 <br/> |An external interface for your Access Edge service. You'll need one for every SIP domain with Skype for Business users.  <br/> |
|External DNS  <br/> |A record  <br/> |NA  <br/> |webcon.contoso.com  <br/> |**public:** 131.107.155.20 <br/> **private:** 10.45.16.20 <br/> |An external interface for your Web Conferencing Edge service.  <br/> |
|External DNS  <br/> |A record  <br/> |NA  <br/> |av.contoso.com  <br/> |**public:** 131.107.155.30 <br/> **private:** 10.45.16.30 <br/> |An external interface for your A/V Edge service.  <br/> |
|External DNS  <br/> |SRV record  <br/> |443  <br/> |_sip._tls.contoso.com  <br/> |sip.contoso.com  <br/> |An external interface for your Access Edge service. This SRV record is required for Skype for Business Server, Lync Server 2013, and Lync Server 2010 clients to work externally. You'll need one for every domain with Skype for Business users.  <br/> |
|External DNS  <br/> |SRV record  <br/> |5061  <br/> |_sipfederationtls._tcp.contoso.com  <br/> |sip.contoso.com  <br/> |An external interface for your Access Edge service. This SRV record is required for automatic DNS discovery of federated partners called Allowed SIP domains. You'll need one for every domain with Skype for Business users.  <br/> |
|Internal DNS  <br/> |A record  <br/> |NA  <br/> |sfvedge.contoso.net  <br/> |172.25.33.10  <br/> |The internal interface for your consolidated Edge.  <br/> |
   
### DNS records for Scaled DNS and hardware Edge Server scenarios

These will be the DNS records you're going to need for a singe Edge Server using either public IPs or private IPs with NAT. Because this is sample data, we'll give example IPs so you can work out your own entries more easily:
  
- Internal network adapter:
    
  - Node 1: 172.25.33.10 (no default gateway's assigned)
    
  - Node 2: 172.25.33.11 (no default gateway's assigned)
    
    > [!NOTE]
    > Ensure that there is a route from the network containing the Edge internal interface to any networks that contain servers running Skype for Business Server or Lync Server 2013 clients (for example, from 172.25.33.0 to 192.168.10.0). 
  
- External network adapter:
    
  - Node 1
    
     - Public IPs:
    
        - Access Edge: 131.107.155.10 (this is the primary, with default gateway set to your public router, ex: 131.107.155.1)
    
        - Web Conferencing Edge: 131.107.155.20 (secondary)
    
        - A/V Edge: 131.107.155.30 (secondary)
    
          Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
    
    - Private IPs:
    
         - Access Edge: 10.45.16.10 (this is the primary, with default gateway set to your router, ex: 10.45.16.1)
    
         - Web Conferencing Edge: 10.45.16.20 (secondary)
    
         - A/V Edge: 10.45.16.30 (secondary)
    
      Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
    
  - Node 2
    
    - Public IPs:
    
      - Access Edge: 131.107.155.11 (this is the primary, with default gateway set to your public router, ex: 131.107.155.1)
    
      - Web Conferencing Edge: 131.107.155.21 (secondary)
    
      - A/V Edge: 131.107.155.31 (secondary)
    
      Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
    
  - Private IPs:
    
    - Access Edge: 10.45.16.11 (this is the primary, with default gateway set to your router, ex: 10.45.16.1)
    
    - Web Conferencing Edge: 10.45.16.21 (secondary)
    
    - A/V Edge: 10.45.16.31 (secondary)
    
      Web conferencing and A/V Edge public IP addresses are additional (secondary) IP addresses in the Advanced section of the properties of Internet Protocol Version 4 (TCP/IPv4) and Internet Protocol Version 6 (TCP/IPv6) of the Local Area Connection Properties in Windows Server.
    
There are other possible configurations here:
  
- You could use one IP address on the external network adapter. We don't recommend this because then you're going to need to differentiate between the thee services using different ports (which you can do in Skype for Business Server) but there are some firewalls that may block the alternate ports. See the [Port and firewall planning](edge-environmental-requirements.md#PortFirewallPlan) section for more about this.
    
- You can have three external network adapters instead of one, and assign one of the service IPs to each one. Why do this? It would separate the services and if something goes wrong, that would make it easier to troubleshoot, and potentially let your other services continue working while you resolve an issue.
    
|**Location**|**Type**|**Port**|**FQDN or DNS record**|**IP address or FQDN**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|External DNS  <br/> |A record  <br/> |NA  <br/> |sip.contoso.com  <br/> |**public:** 131.107.155.10 and 131.107.155.11 <br/> **private:** 10.45.16.10 and 10.45.16.11 <br/> |An external interface for your Access Edge service. You'll need one for every SIP domain with Skype for Business users.  <br/> |
|External DNS  <br/> |A record  <br/> |NA  <br/> |webcon.contoso.com  <br/> |**public:** 131.107.155.20 and 131.107.155.21 <br/> **private:** 10.45.16.20 and 10.45.16.21 <br/> |An external interface for your Web Conferencing Edge service.  <br/> |
|External DNS  <br/> |A record  <br/> |NA  <br/> |av.contoso.com  <br/> |**public:** 131.107.155.30 and 131.107.155.31 <br/> **private:** 10.45.16.30 and 10.45.16.31 <br/> |An external interface for your A/V Edge service.  <br/> |
|External DNS  <br/> |SRV record  <br/> |443  <br/> |_sip._tls.contoso.com  <br/> |sip.contoso.com  <br/> |An external interface for your Access Edge service. This SRV record is required for Skype for Business Server, Lync Server 2013, and Lync Server 2010 clients to work externally. You'll need one for every domain with Skype for Business.  <br/> |
|External DNS  <br/> |SRV record  <br/> |5061  <br/> |_sipfederationtls._tcp.contoso.com  <br/> |sip.contoso.com  <br/> |An external interface for your Access Edge service. This SRV record is required for automatic DNS discovery of federated partners called Allowed SIP domains. You'll need one for every domain with Skype for Business.  <br/> |
|Internal DNS  <br/> |A record  <br/> |NA  <br/> |sfvedge.contoso.net  <br/> |172.25.33.10 and 172.25.33.11  <br/> |The internal interface for your consolidated Edge.  <br/> |
   
### DNS record for federation (all scenarios)

|**Location**|**Type**|**Port**|**FQDN**|**FQDN host record**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|External DNS  <br/> |SRV  <br/> |5061  <br/> |_sipfederationtls_tcp.contoso.com  <br/> |sip.contoso.com  <br/> |The SIP Access Edge external interface required for automatic DNS discovery. Used by your other potential federation partners. It's also known as "Allow SIP domains." You'll need one of these for each SIP domain with Skype for Business users.  <br/><br/> **Note:** You will need this SRV record for mobility and the push notification clearing house. <br/> |
   
### DNS records for extensible messaging and presence protocol

|**Location**|**Type**|**Port**|**FQDN**|**IP address or FQDN host record**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|External DNS  <br/> |SRV  <br/> |5269  <br/> |_xmpp-server._tcp.contoso.com  <br/> |xmpp.contoso.com  <br/> |The XMPP proxy interface on your Access Edge service or Edge pool. You need to repeat this as needed for all internal SIP domains with Skype for Business Server enabled users, where contact with XMPP contacts is allowed through:  <br/> • a global policy  <br/> • a site policy where the user's enabled  <br/> • a user policy applied to the Skype for Business Server enabled user  <br/> An allowed XMPP policy also needs to be configured in the XMPP federated users policy.  <br/> |
|External DNS  <br/> |SRV  <br/> |A  <br/> |xmpp.contoso.com  <br/> |IP address of the Access Edge service on the Edge Server or Edge pool hosting your XMPP Proxy service  <br/> |This points to the Access Edge service on the Edge Server or Edge pool that hosts the XMPP Proxy service. Typically the SRV record that you create will point to this host (A or AAAA) record.  <br/> |
   
> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.

## Certificate planning
<a name="CertPlan"> </a>

Skype for Business Server uses certificates for secure, encrypted communications both between servers and from server to client. As you'd expect, your certificates will need to have DNS records for your servers match up to any subject name (SN) and subject alternate name (SAN) on your certificates. This will take work now, at the planning stage, to ensure you have the right FQDNs registered in DNS for the SN and SAN entries for your certificates.
  
We'll discuss external and internal certificate needs separately, and then look at a table providing the requirements for both.
  
### External Certificates

At a minimum, the certificate assigned to your external Edge Server interfaces will need to be provided by a public Certificate Authority (CA). We can't recommend a specific CA to you, but we do have a list of CAs, [Unified Communications certificate partners](https://support.microsoft.com/en-us/kb/929395) that you can take a look at to see if your preferred CA is listed.
  
When will you need to submit a request to a CA for this public certificate, and how do you do it? There are a couple of ways to accomplish this:
  
- You can go through the installation of Skype for Business Server, and then the Edge Server deployment. The Skype for Business Server Deployment Wizard will have a step to generate a certificate request, which you can then send to your chosen CA.
    
- You can also use Windows PowerShell commands to generate this request, if that's more inline with your business needs or deployment strategy.
    
- Finally, your CA may have their own submission process, which may also involve Windows PowerShell or another method. In that case, you'll need to rely on their documentation, in addition to the information provided here for your reference.
    
After you've gotten the certificate, you'll need to go ahead and assign it to these services in Skype for Business Server:
  
- Access Edge service interface
    
- Web Conferencing Edge service interface
    
- Audio/Video Authentication service (don't confuse this with the A/V Edge service, as that doesn't use a certificate to encrypt audio and video streams)
    
> [!IMPORTANT]
> All Edge Servers (if they belong to the same pool of Edge Servers) need to have the exact same certificate with the same private key for the Media Relay Authentication service. 
  
### Internal Certificates

For the internal Edge Server interface, you can use a public certificate from a public CA, or a certificate issued from your organization's internal CA. The thing to remember about the internal certificate is that it uses an SN entry, and no SAN entries, so you don't have to worry about SAN on the internal cert at all.
  
### Required Certificates table

We have a table here to help you out with your requests. The FQDN entries here are for sample domains only. You're going to need to make requests based on your own private and public domains, but here's a guide to what we've used:
  
- contoso<span></span>.com: Public FQDN
    
- fabrikam<span></span>.com: Second public FQDN (added as a demo of what to request if you have multiple SIP domains)
    
- Contoso<span></span>.net: Internal domain
    
#### Edge Certificate table

Regardless of whether you're doing a single Edge Server or an Edge pool, this is what you'll need for your certificate:
  
|**Component**|**Subject name (SN)**|**Subject alternative names (SAN)/order**|**Notes**|
|:-----|:-----|:-----|:-----|
|External Edge  <br/> |sip.contoso.com  <br/> |sip.contoso.com  <br/> webcon.contoso.com  <br/> sip.fabrikam.com  <br/> |This is the certificate you need to request from a public CA. It'll need to be assigned to the external Edge interfaces for the following:  <br/> • Access Edge  <br/> • Web Conferencing Edge  <br/> • Audio/Video Authentication  <br/> <br/>The good news is that SANs are automatically added to your certificate request, and therefore your certificate after you submit the request, based on what you defined for this deployment in Topology Builder. You'll only need to add SAN entries for any additional SIP domains or other entries you need to support. Why is sip.contoso.com replicated in this instance? That happens automatically as well, and it's needed for things to work properly.  <br/><br/> **Note:** This certificate can also be used for Public Instant Messaging connectivity. You don't need to do anything differently with it, but in previous versions of this documentation, it was listed as a separate table, and now it's not. <br/> |
|Internal Edge  <br/> |sfbedge.contoso.com  <br/> |NA  <br/> |You can get this certificate from a public CA or an internal CA. It'll need to contain the server EKU (Enhanced Key Usage), and you'll assign it to the internal Edge interface.  <br/> |
   
If you need a certificate for Extensible Messaging and Presence Protocol (XMPP), it will look identical to the External Edge table entries above, but will have the following two additional SAN entries:
  
- xmpp.<span></span>contoso<span></span>.com
    
- \*.contoso<span></span>.com
    
Please remember that currently XMPP is only supported in Skype for Business Server for Google Talk, if you want or need to use it for anything else, you need to confirm that functionality with the third-party vendor involved.
  
## Port and firewall planning
<a name="PortFirewallPlan"> </a>

Getting your planning right for ports and firewalls for Skype for Business Server Edge Server deployments can save you days or weeks of troubleshooting and stress. As a result, we're going to list a couple of tables that will indicate our protocol usage and what ports you need to have open, inbound and outbound, both for NAT and public IP scenarios. We'll also have separate tables for hardware load balanced scenarios (HLB) and some further guidance on that. For more reading from there, we also have some [Edge Server scenarios in Skype for Business Server](scenarios.md) you can check out for your particular deployment concerns.
  
### General protocol usage

Before we look at the summary tables for external and internal firewalls, let's consider the following table as well:
  
|**Audio/Video transport**|**Usage**|
|:-----|:-----|
|UDP  <br/> |The preferred transport layer protocol for audio and video.  <br/> |
|TCP  <br/> |The fallback transport layer protocol for audio and video.  <br/> The required transport layer protocol for application sharing to Skype for Business Server, Lync Server 2013, and Lync Server 2010.  <br/> The required transport layer protocol for file transfer to Skype for Business Server, Lync Server 2013, and Lync Server 2010.  <br/> |
   
### External port firewall summary table

The Source IP address and Destination IP address will contain information for users who are using Private IP addresses with NAT, as well as people using public IP addresses. This will cover all the permutations in our [Edge Server scenarios in Skype for Business Server](scenarios.md) section.
  
|**Role or protocol**|**TCP or UDP**|**Destination Port or port range**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|XMPP  <br/> Not supported in Skype for Business Server 2019 |TCP  <br/> |5269  <br/> |Any  <br/> |XMPP Proxy service (shares an IP address with the Access Edge service  <br/> |The XMPP Proxy service accepts traffic from XMPP contacts in defined XMPP federations.  <br/> |
|Access/HTTP  <br/> |TCP  <br/> |80  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Any  <br/> |Certificate revocation and CRL check and retrieval.  <br/> |
|Access/DNS  <br/> |TCP  <br/> |53  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Any  <br/> |DNS query over TCP.  <br/> |
|Access/DNS  <br/> |UDP  <br/> |53  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Any  <br/> |DNS query over UDP.  <br/> |
|Access/SIP(TLS)  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Client-to-server SIP traffic for external user access.  <br/> |
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |For federated and public IM connectivity using SIP.  <br/> |
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Any  <br/> |For federated and public IM connectivity using SIP.  <br/> |
|Web conferencing/PSOM(TLS)  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Web Conferencing Edge service <br/> **Public IP:** Edge Server Web Conferencing Edge service public IP address <br/> |Web conferencing media.  <br/> |
|A/V/RTP  <br/> |TCP  <br/> |50000-59999  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |Any  <br/> |This is used for relaying media traffic.  <br/> |
|A/V/RTP  <br/> |UDP  <br/> |50000-59999  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |Any  <br/> |This is used for relaying media traffic.  <br/> |
|A/V/STUN.MSTURN  <br/> |UDP  <br/> |3478  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |Any  <br/> |3478 outbound is:  <br/> • Used by Skype for Business Server to determine the version of Edge Server it's communicating with.  <br/> • Used for media traffic between Edge Servers.  <br/> • Required for federation with Lync Server 2010.  <br/> • Needed if multiple Edge pools are deployed within your organization.  <br/> |
|A/V/STUN.MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |STUN/TURN negotiation of candidates over UDP on port 3478.  <br/> |
|A/V/STUN.MSTURN  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |STUN/TURN negotiation of candidates over TCP on port 443.  <br/> |
|A/V/STUN.MSTURN  <br/> |TCP  <br/> |443  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |Any  <br/> |STUN/TURN negotiation of candidates over TCP on port 443.  <br/> |
   
### Internal port firewall summary table

|**Protocol**|**TCP or UDP**|**Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|XMPP/MTLS  <br/> |TCP  <br/> |23456  <br/> |Any of the following running the XMPP Gateway service:  <br/> • Front End Server  <br/> • Front End pool  <br/> |Edge Server internal interface  <br/> |Outbound XMPP traffic from your XMPP Gateway service running on your Front End Server or Front End pool.  <br/> **Note:** XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.|
|SIP/MTLS  <br/> |TCP  <br/> |5061  <br/> |Any:  <br/> • Director  <br/> • Director pool  <br/> • Front End Server  <br/> • Front End pool  <br/> |Edge Server internal interface  <br/> |Outbound SIP traffic from your Director, Director pool, Front End Server or Front End pool to your Edge Server internal interface.  <br/> |
|SIP/MTLS  <br/> |TCP  <br/> |5061  <br/> |Edge Server internal interface  <br/> |Any:  <br/> • Director  <br/> • Director pool  <br/> • Front End Server  <br/> • Front End pool  <br/> |Inbound SIP traffic to your Director, Director pool, Front End Server, or Front End pool from your Edge Server internal interface.  <br/> |
|PSOM/MTLS  <br/> |TCP  <br/> |8057  <br/> |Any:  <br/> • Front End Server  <br/> • Each Front End Server  <br/>  in your Front End pool <br/> |Edge Server internal interface  <br/> |Web conferencing traffic from your Front End Server or each Front End Server (if you have a Front End pool) to your Edge Server internal interface.  <br/> |
|SIP/MTLS  <br/> |TCP  <br/> |5062  <br/> |Any:  <br/> • Front End Server  <br/> • Front End pool  <br/> • Any Survivable Branch Appliance using this Edge Server  <br/> • Any Survivable Branch Server using this Edge Server  <br/> |Edge Server internal interface  <br/> |Authentication of A/V users from your Front End Server or Front End pool, or your Survivable Branch Appliance or Survivable Branch Server, using your Edge Server.  <br/> |
|STUN/MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Preferred path for A/V media transfer between your internal and external users and your Survivable Branch Appliance or Survivable Branch Server.  <br/> |
|STUN/MSTURN  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Fallback path for A/V media transfer between your internal and external users and your Survivable Branch Appliance or Survivable Branch Server, if UDP communication doesn't work. TCP is then used for file transfers and desktop sharing.  <br/> |
|HTTPS  <br/> |TCP  <br/> |4443  <br/> |Any:  <br/> • Front End Server that holds the Central Management store  <br/> • Front End pool that holds the Central Management store  <br/> |Edge Server internal interface  <br/> |Replication of changes from your Central Management store to your Edge Server.  <br/> |
|MTLS  <br/> |TCP  <br/> |50001  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
|MTLS  <br/> |TCP  <br/> |50002  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
|MTLS  <br/> |TCP  <br/> |50003  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
   
### Hardware load balancers for Edge port tables

We're giving hardware load balancers (HLBs) and Edge ports their own section, as things are a little more complicated with the additional hardware. Please refer to the tables below for guidance for this particular scenario:
  
#### External port firewall summary table

The Source IP address and Destination IP address will contain information for users who are using Private IP addresses with NAT, as well as people using public IP addresses. This will cover all the permutations in our [Edge Server scenarios in Skype for Business Server](scenarios.md) section.
  
|**Role or protocol**|**TCP or UDP**|**Destination Port or port range**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Access/HTTP  <br/> |TCP  <br/> |80  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |Certificate revocation and CRL check and retrieval.  <br/> |
|Access/DNS  <br/> |TCP  <br/> |53  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |DNS query over TCP.  <br/> |
|Access/DNS  <br/> |UDP  <br/> |53  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |DNS query over UDP.  <br/> |
|A/V/RTP  <br/> |TCP  <br/> |50000-59999  <br/> |Edge Server A/V Edge service IP address  <br/> |Any  <br/> |This is used for relaying media traffic.  <br/> |
|A/V/RTP  <br/> |UDP  <br/> |50000-59999  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |This is used for relaying media traffic.  <br/> |
|A/V/STUN.MSTURN  <br/> |UDP  <br/> |3478  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |3478 outbound is:  <br/> • Used by Skype for Business Server to determine the version of Edge Server it's communicating with.  <br/> • Used for media traffic between Edge Servers.  <br/> • Required for federation.  <br/> • Needed if multiple Edge pools are deployed within your organization.  <br/> |
|A/V/STUN.MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |STUN/TURN negotiation of candidates over UDP on port 3478.  <br/> |
|A/V/STUN.MSTURN  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |STUN/TURN negotiation of candidates over TCP on port 443.  <br/> |
|A/V/STUN.MSTURN  <br/> |TCP  <br/> |443  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |STUN/TURN negotiation of candidates over TCP on port 443.  <br/> |
   
#### Internal port firewall summary table

|**Protocol**|**TCP or UDP**|**Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|XMPP/MTLS  <br/> |TCP  <br/> |23456  <br/> |Any of the following running the XMPP Gateway service:  <br/> • Front End Server  <br/> • Front End pool VIP address running the XMPP Gateway service  <br/> |Edge Server internal interface  <br/> |Outbound XMPP traffic from your XMPP Gateway service running on your Front End Server or Front End pool.  <br/><br/> **Note:** XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information. |
|HTTPS  <br/> |TCP  <br/> |4443  <br/> |Any:  <br/> • Front End Server that holds the Central Management store  <br/> • Front End pool that holds the Central Management store  <br/> |Edge Server internal interface  <br/> |Replication of changes from your Central Management store to your Edge Server.  <br/> |
|PSOM/MTLS  <br/> |TCP  <br/> |8057  <br/> |Any:  <br/> • Front End Server  <br/> • Each Front End Server in your Front End pool  <br/> |Edge Server internal interface  <br/> |Web conferencing traffic from your Front End Server or each Front End Server (if you have a Front End pool) to your Edge Server internal interface.  <br/> |
|STUN/MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any:  <br/> • Front End Server  <br/> • Each Front End Server in your Front End pool  <br/> |Edge Server internal interface  <br/> |Preferred path for A/V media transfer between your internal and external users and your Survivable Branch Appliance or Survivable Branch Server.  <br/> |
|STUN/MSTURN  <br/> |TCP  <br/> |443  <br/> |Any:  <br/> • Front End Server  <br/> • Each Front End Server in your pool  <br/> |Edge Server internal interface  <br/> |Fallback path for A/V media transfer between your internal and external users and your Survivable Branch Appliance or Survivable Branch Server, if UDP communication doesn't work. TCP is then used for file transfers and desktop sharing.  <br/> |
|MTLS  <br/> |TCP  <br/> |50001  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
|MTLS  <br/> |TCP  <br/> |50002  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
|MTLS  <br/> |TCP  <br/> |50003  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Skype for Business Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection.  <br/> |
   
#### External interface Virtual IPs

|**Role or protocol**|**TCP or UDP**|**Destination Port or port range**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|XMPP  <br/> Not Supported in Skype for Businesss Server 2019 |TCP  <br/> |5269  <br/> |Any  <br/> |XMPP Proxy service (shares an IP address with the Access Edge service)  <br/> |The XMPP Proxy service accepts traffic from XMPP contacts in defined XMPP federations.  <br/> |
|XMPP  <br/>Not Supported in Skype for Businesss Server 2019 |TCP  <br/> |5269  <br/> |XMPP Proxy service (shares an IP address with the Access Edge service)  <br/> |Any  <br/> |The XMPP Proxy service sends traffic from XMPP contacts in defined XMPP federations.  <br/> |
|Access/SIP(TLS)  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Client-to-server SIP traffic for external user access.  <br/> |
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |For federated and public IM connectivity using SIP.  <br/> |
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |**Private IP using NAT:** Edge Server Access Edge service <br/> **Public IP:** Edge Server Access Edge service public IP address <br/> |Any  <br/> |For federated and public IM connectivity using SIP.  <br/> |
|Web conferencing/PSOM(TLS)  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server Web Conferencing Edge service <br/> **Public IP:** Edge Server Web Conferencing Edge service public IP address <br/> |Web conferencing media.  <br/> |
|A/V/STUN.MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |STUN/TURN negotiation of candidates over UDP on port 3478.  <br/> |
|A/V/STUN.MSTURN  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |**Private IP using NAT:** Edge Server A/V Edge service <br/> **Public IP:** Edge Server A/V Edge service public IP address <br/> |STUN/TURN negotiation of candidates over TCP on port 443.  <br/> |
   
#### Internal interface Virtual IPs

Our guidance here is going to be a little different. In actuality, in a HLB situation, we now recommend you only have routing through an internal VIP under the following circumstances:
  
- If you are using Exchange 2007 or Exchange 2010 Unified Messaging (UM).
    
- If you have legacy clients using the Edge.
    
The following table does give guidance for those scenarios, but otherwise, you should be able to depend on Central Management store (CMS) to route traffic to the individual Edge Server it's aware of (this does require that CMS is kept up to date on Edge Server information, of course).
  
|**Protocol**|**TCP or UDP**|**Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |Any:  <br/> • Director  <br/> • Director pool VIP address  <br/> • Front End Server  <br/> • Front End pool VIP address  <br/> |Edge Server internal interface  <br/> |Outbound SIP traffic from your Director, Director pool VIP address, Front End Server, or Front End pool VIP address to your Edge Server internal interface.  <br/> |
|Access/SIP(MTLS)  <br/> |TCP  <br/> |5061  <br/> |Edge Server internal VIP interface  <br/> |Any:  <br/> • Director  <br/> • Director pool VIP address  <br/> • Front End Server  <br/> • Front End pool VIP address  <br/> |Inbound SIP traffic to your Director, Director pool VIP address, Front End Server, or Front End pool VIP address from your Edge Server internal interface.  <br/> |
|SIP/MTLS  <br/> |TCP  <br/> |5062  <br/> |Any:  <br/> • Front End Server IP address  <br/> • Front End pool IP address  <br/> • Any Survivable Branch Appliance using this Edge Server  <br/> • Any Survivable Branch Server using this Edge Server  <br/> |Edge Server internal interface  <br/> |Authentication of A/V users from your Front End Server or Front End pool, or your Survivable Branch Appliance or Survivable Branch Server, using your Edge Server.  <br/> |
|STUN/MSTURN  <br/> |UDP  <br/> |3478  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Preferred path for A/V media transfer between your internal and external users.  <br/> |
|STUN/MSTURN  <br/> |TCP  <br/> |443  <br/> |Any  <br/> |Edge Server internal VIP interface  <br/> |Fallback path for A/V media transfer between your internal and external users if UDP communication doesn't work. TCP is then used for file transfers and desktop sharing.  <br/> |
