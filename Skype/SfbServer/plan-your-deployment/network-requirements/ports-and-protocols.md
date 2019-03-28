---
title: "Port and protocol requirements for servers"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/15/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: c94063f1-e802-4a61-be90-022fc185335e
description: "Summary: Review the port usage considerations before implementing Skype for Business Server."
---

# Port and protocol requirements for servers
 
**Summary:** Review the port usage considerations before implementing Skype for Business Server.
  
Skype for Business Server requires that specific ports on the external and internal firewalls be open. Additionally, if Internet Protocol security (IPsec) is deployed in your organization, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. 
  
While this may seem a bit daunting at first, the heavy lifting for planning this can be done using the [Skype for Business Server 2015 Planning Tool](https://go.microsoft.com/fwlink/p/?LinkID=282725). Once you've gone through the wizard's questions about what features you plan to use, for each site you define you can view the Firewall Report within the Edge Admin Report, and use the information listed there to create yourfirewall rules. You can also make adjustments to many of the names and IP addresses used, for details see [Review the Firewall Report](../../management-tools/planning-tool/review-the-administrator-reports.md#Firewall_report). Keep in mind you can export the Edge Admin Report to an Excel spreadsheet, and the Firewall Report will be one of the worksheets in the file. 
  
You can also find the information in these tables in diagram form by reviewing the Protocol Workloads poster linked off of the [Technical diagrams for Skype for Business Server 2015](../../technical-diagrams.md) article.
> [!NOTE]
> - If you're implementing Skype for Business Online (O365) refer to [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;amp;rs=en-US&amp;amp;ad=US). Hybrid environments will need to reference this topic and also [Plan hybrid connectivity](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md?toc=/SkypeForBusiness/sfbhybridtoc/toc.json).
> - You can have hardware or software firewalls, we don't require specific models or versions. What matters is what ports are whitelisted so the firewall won't impair the functioning of Skype for Business Server.
  
## Port and Protocol Details

This section summarizes the ports and protocols used by servers, load balancers, and clients in a Skype for Business Server deployment.
  
> [!NOTE]
> When Skype for Business Server starts, it opens the required ports in the Windows Firewall. Windows Firewall should already be running in most normal applications, but if it is not being used Skype for Business Server will function without it. 
  
For details about firewall configuration for edge components, see [Edge Server scenarios in Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/scenarios.md). 
  
The following table lists the ports that need to be open on each internal server role. 
  
**Required Server Ports (by Server Role)**

|Server role|Service name|Port|Protocol|Notes|
|:-----|:-----|:-----|:-----|:-----|
|All Servers  |SQL Browser  |1434  |UDP  |SQL Browser for the local replicated copy of the Central Management Store database.  |
|Front End Servers  |Skype for Business Server Front-End service  |5060  |TCP  |Optionally used by Standard Edition servers and Front End Servers for static routes to trusted services, such as remote call control servers.  |
|Front End Servers  |Skype for Business Server Front-End service  |5061  | TCP (TLS) |Used by Standard Edition servers and Front End pools for all internal SIP communications between servers (MTLS), for SIP communications between Server and Client (TLS) and for SIP communications between Front End Servers and Mediation Servers (MTLS). Also used for communications with a Monitoring Server.  |
| Front End Servers |Skype for Business Server Front-End service  |444  | HTTPS <br/> TCP  |Used for HTTPS communication between the Focus (the Skype for Business Server component that manages conference state) and the individual servers.  <br/> This port is also used for TCP communication between Survivable Branch Appliances and Front End Servers.  |
|Front End Servers  |Skype for Business Server Front-End service  |135  |DCOM and remote procedure call (RPC)  |Used for DCOM based operations such as Moving Users, User Replicator Synchronization, and Address Book Synchronization.  |
|Front End Servers  |Skype for Business Server IM Conferencing service  |5062  |TCP  |Used for incoming SIP requests for instant messaging (IM) conferencing.  |
|Front End Servers  |Skype for Business Server Web Conferencing service  |8057  |TCP (TLS)  |Used to listen for Persistent Shared Object Model (PSOM) connections from client.  |
|Front End Servers  |Skype for Business Server Web Conferencing Compatibility service  |8058  |TCP (TLS)  |Used to listen for Persistent Shared Object Model (PSOM) connections from the Live Meeting client and previous versions of Skype for Business Server.  |
|Front End Servers  |Skype for Business Server Audio/Video Conferencing service  |5063  |TCP  |Used for incoming SIP requests for audio/video (A/V) conferencing.  |
|Front End Servers  |Skype for Business Server Audio/Video Conferencing service  |57501-65535  |TCP/UDP  |Media port range used for video conferencing.  |
|Front End Servers  |Skype for Business Server Web Compatibility service  |80  |HTTP  |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components) when HTTPS is not used.  |
|Front End Servers  |Skype for Business Server Web Compatibility service  |443  |HTTPS  |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components).  |
|Front End Servers  |Skype for Business Server Web Compatibility service  |8080  |TCP and HTTP  |Used by web components for external access.  |
|Front End Servers  |Web server component  |4443  |HTTPS  |HTTPS (from Reverse Proxy) and HTTPS Front End inter-pool communications for Autodiscover sign-in.  |
|Front End Servers  |Web server component  |8060  |TCP (MTLS)  ||
|Front End Servers  |Web server component  |8061  |TCP (MTLS)  ||
|Front End Servers  |Mobility Services component  |5086  |TCP (MTLS)  |SIP port used by Mobility Services internal processes  |
|Front End Servers  |Mobility Services component  |5087  |TCP (MTLS)  |SIP port used by Mobility Services internal processes  |
|Front End Servers  |Mobility Services component  |443  |HTTPS  ||
|Front End Servers  |Skype for Business Server Conferencing Attendant service (dial-in conferencing)  |5064  |TCP  |Used for incoming SIP requests for dial-in conferencing.  |
|Front End Servers  |Skype for Business Server Conferencing Attendant service (dial-in conferencing)  |5072  |TCP  |Used for incoming SIP requests for Attendant (dial in conferencing).  |
|Front End Servers that also run a Collocated Mediation Server  |Skype for Business Server Mediation service  |5070  |TCP  |Used by the Mediation Server for incoming requests from the Front End Server to the Mediation Server.  |
|Front End Servers that also run a Collocated Mediation Server  |Skype for Business Server Mediation service  |5067  |TCP (TLS)  |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  |
|Front End Servers that also run a Collocated Mediation Server  |Skype for Business Server Mediation service  |5068  |TCP  |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  |
|Front End Servers that also run a Collocated Mediation Server  |Skype for Business Server Mediation service  |5081  |TCP  |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  |
|Front End Servers that also run a Collocated Mediation Server  |Skype for Business Server Mediation service  |5082  |TCP (TLS)  |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  |
|Front End Servers  |Skype for Business Server Application Sharing service  |5065  |TCP  |Used for incoming SIP listening requests for application sharing.  |
|Front End Servers  |Skype for Business Server Application Sharing service  |49152-65535  |TCP  |Media port range used for application sharing.  |
|Front End Servers  |Skype for Business Server Conferencing Announcement service  |5073  |TCP  |Used for incoming SIP requests for the Skype for Business Server Conferencing Announcement service (that is, for dial-in conferencing).  |
|Front End Servers  |Skype for Business Server Call Park service  |5075  |TCP  |Used for incoming SIP requests for the Call Park application.  |
|Front End Servers  |Skype for Business Server Audio Test service  |5076  |TCP  |Used for incoming SIP requests for the Audio Test service.  |
|Front End Servers  |Not applicable  |5066  |TCP  |Used for outbound Enhanced 9-1-1 (E9-1-1) gateway.  |
|Front End Servers  |Skype for Business Server Response Group service  |5071  |TCP  |Used for incoming SIP requests for the Response Group application.  |
|Front End Servers  |Skype for Business Server Response Group service  |8404  |TCP (MTLS)  |Used for incoming SIP requests for the Response Group application.  |
|Front End Servers  |Skype for Business Server Bandwidth Policy Service  |5080  |TCP  |Used for call admission control by the Bandwidth Policy service for A/V Edge TURN traffic.  |
|Front End Servers  |Skype for Business Server File Share server access  |445   |SMB/TCP  | Used to retrieve Address book, meeting content, and other items stored on the File Share server.  |
|Front End Servers  |Skype for Business Server Bandwidth Policy Service  |448  |TCP  |Used for call admission control by the Skype for Business Server Bandwidth Policy Service.  |
|Front End Servers where the Central Management store resides  | Skype for Business Server Master Replicator Agent service |445  |TCP  |Used to push configuration data from the Central Management store to servers running Skype for Business Server.  |
|All Servers  |SQL Browser  |1434  |UDP  |SQL Browser for local replicated copy of Central Management store data in local SQL Server instance  |
|All internal servers  |Various  |49152-57500  |TCP/UDP  |Media port range used for audio conferencing on all internal servers. Used by all servers that terminate audio: Front End Servers (for Skype for Business Server Conferencing Attendant service, Skype for Business Server Conferencing Announcement service, and Skype for Business Server Audio/Video Conferencing service), and Mediation Server.  |
|Office Web Apps Servers  ||443  ||Used by Skype for Business Server to connect to Office Web Apps Server.  |
|Directors  |Skype for Business Server Front-End service  |5060  |TCP  |Optionally used for static routes to trusted services, such as remote call control servers.  |
|Directors  |Skype for Business Server Front-End service  |444  |HTTPS  <br/> TCP  |Inter-server communication between Front End and Director. Additionally, client certificate publish (to Front End Servers) or validate if the client certificate has already been published.  |
|Directors  |Skype for Business Server Web Compatibility service  |80  |TCP  |Used for initial communication from Directors to the web farm FQDNs (the URLs used by IIS web components). In normal operation, will switch to HTTPS traffic, using port 443 and protocol type TCP.  |
|Directors  |Skype for Business Server Web Compatibility service  |443  |HTTPS  |Used for communication from Directors to the web farm FQDNs (the URLs used by IIS web components).  |
|Directors  |Skype for Business Server Front-End service  |5061  |TCP  |Used for internal communications between servers and for client connections.  |
|Mediation Servers  |Skype for Business Server Mediation service  |5070  |TCP  |Used by the Mediation Server for incoming requests from the Front End Server.  |
|Mediation Servers  |Skype for Business Server Mediation service  |5067  |TCP (TLS)  |Used for incoming SIP requests from the PSTN gateway.  |
|Mediation Servers  |Skype for Business Server Mediation service  |5068  |TCP  |Used for incoming SIP requests from the PSTN gateway.  |
|Mediation Servers  |Skype for Business Server Mediation service  |5070  |TCP (MTLS)  |Used for SIP requests from the Front End Servers.  |
|Persistent Chat Front End Server  |Persistent Chat SIP  |5041  |TCP (MTLS)  ||
|Persistent Chat Front End Server  |Persistent Chat Windows Communication Foundation (WCF)  |881  |TCP (TLS) and TCP (MTLS)  ||
|Persistent Chat Front End Server  |Persistent Chat File Transfer Service  |443  |TCP (TLS)  ||
   
> [!NOTE]
> Some remote call control scenarios require a TCP connection between the Front End Server or Director and the PBX. Although Skype for Business Server no longer uses TCP port 5060, during remote call control deployment you create a trusted server configuration, which associates the RCC Line Server FQDN with the TCP port that the Front End Server or Director will use to connect to the PBX system. For details, see the **CsTrustedApplicationComputer** cmdlet in the Skype for Business Server Management Shell documentation.
  
For your pools that use only hardware load balancing (not DNS load balancing), the following table shows the ports that need to open the hardware load balancers.
  
**Hardware Load Balancer Ports if Using Only Hardware Load Balancing**

|Load Balancer|Port|Protocol|
|:-----|:-----|:-----|
|Front End Server load balancer  |5061  |TCP (TLS)  |
|Front End Server load balancer  |444  |HTTPS  |
|Front End Server load balancer  |135  |DCOM and remote procedure call (RPC)  |
|Front End Server load balancer  |80  |HTTP  |
|Front End Server load balancer  |8080  |TCP - Client and device retrieval of root certificate from Front End Server - clients and devices authenticated by NTLM  |
|Front End Server load balancer  |443  |HTTPS  |
|Front End Server load balancer  |4443  |HTTPS (from reverse proxy)  |
|Front End Server load balancer  |5072  |TCP  |
|Front End Server load balancer  |5073  |TCP  |
|Front End Server load balancer  |5075  |TCP  |
|Front End Server load balancer  |5076  |TCP  |
|Front End Server load balancer  |5071  |TCP  |
|Front End Server load balancer  |5080  |TCP  |
|Front End Server load balancer  |448  |TCP  |
|Mediation Server load balancer  |5070  |TCP  |
|Front End Server load balancer (if the pool also runs Mediation Server)  |5070  |TCP  |
|Director load balancer  |443  |HTTPS  |
|Director load balancer  |444  |HTTPS  |
|Director load balancer  |5061  |TCP  |
|Director load balancer  |4443  |HTTPS (from reverse proxy)  |
   
Your Front End pools and Director pools that use DNS load balancing also must have a hardware load balancer deployed. The following table shows the ports that need to be open on these hardware load balancers.
  
**Hardware Load Balancer Ports if Using DNS Load Balancing**

|Load Balancer|Port|Protocol|
|:-----|:-----|:-----|
|Front End Server load balancer  |80  |HTTP  |
|Front End Server load balancer  |443  |HTTPS  |
|Front End Server load balancer  |8080  |TCP - Client and device retrieval of root certificate from Front End Server - clients and devices authenticated by NTLM  |
|Front End Server load balancer  |4443  |HTTPS (from reverse proxy)  |
|Director load balancer  |443  |HTTPS  |
|Director load balancer  |4443  |HTTPS (from reverse proxy)  |

**Required Client Ports**

|Component|Port|Protocol|Notes|
|:-----|:-----|:-----|:-----|
|Clients  |67/68  |DHCP  |Used by Skype for Business Server to find the Registrar FQDN (that is, if DNS SRV fails and manual settings are not configured).  |
|Clients  |443  |TCP (TLS)  |Used for client-to-server SIP traffic for external user access.  |
|Clients  |443  |TCP (PSOM/TLS)  |Used for external user access to web conferencing sessions.  |
|Clients  |443  |TCP (STUN/MSTURN)  |Used for external user access to A/V sessions and media (TCP)  |
|Clients  |3478  |UDP (STUN/MSTURN)  |Used for external user access to A/V sessions and media (UDP)  |
|Clients  |5061  |TCP (MTLS)  |Used for client-to-server SIP traffic for external user access.  |
|Clients  |6891-6901  |TCP  |Used for file transfer between Skype for Business clients and previous clients.  |
|Clients  |1024-65535 \*  |TCP/UDP  |Audio port range (minimum of 20 ports required)  |
|Clients  |1024-65535 \*  |TCP/UDP  |Video port range (minimum of 20 ports required).  |
|Clients  |1024-65535 \*  |TCP  |Peer-to-peer file transfer (for conferencing file transfer, clients use PSOM).  |
|Clients  |1024-65535 \*  |TCP  |Application sharing.  |
|Aastra 6721ip common area phone  <br/> Aastra 6725ip desk phone  <br/> HP 4110 IP Phone (common area phone)  <br/> HP 4120 IP Phone (desk phone)  <br/> Polycom CX500 IP common area phone  <br/> Polycom CX600 IP desk phone  <br/> Polycom CX700 IP desk phone  <br/> Polycom CX3000 IP conference phone  |67/68  |DHCP  |Used by the listed devices to find the Skype for Business Server certificate, provisioning FQDN, and Registrar FQDN.  |
   
\* To configure specific ports for these media types, use the CsConferencingConfiguration cmdlet (ClientMediaPortRangeEnabled, ClientMediaPort, and ClientMediaPortRange parameters).
  
> [!NOTE]
> The setup programs for Skype for Business clients automatically create the required operating-system firewall exceptions on the client computer. 

> [!NOTE]
> The ports that are used for external user access are required for any scenario in which the client must traverse the organization's firewall (for example, any external communications or meetings hosted by other organizations). 
  
## IPsec exceptions

For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panoramic video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation.
  
The following table explains the recommended IPsec exception settings. 
  
**Recommended IPsec Exceptions**

|Rule name|Source IP|Destination IP|Protocol|Source port|Destination port|Authentication Requirement|
|:--- |:--- |:--- |:--- |:--- |:--- |:--- |
|A/V Edge Server Internal Inbound  |Any  |A/V Edge Server Internal  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|A/V Edge Server External Inbound  |Any  |A/V Edge Server External  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|A/V Edge Server Internal Outbound  |A/V Edge Server Internal  |Any  |UDP &amp; TCP  |Any  |Any  |Do not authenticate  |
|A/V Edge Server External Outbound  |A/V Edge Server External  |Any  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Mediation Server Inbound  |Any  |Mediation  <br/> Server(s)  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Mediation Server Outbound  |Mediation  <br/> Server(s)  |Any  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Conferencing Attendant Inbound  |Any  |Front End Server running Conferencing Attendant  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Conferencing Attendant Outbound  |Front End Server running Conferencing Attendant  |Any  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|A/V Conferencing Inbound  |Any  |Front End Servers  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|A/V Conferencing Outbound  |Front End Servers  |Any  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Exchange Inbound  |Any  |Exchange Unified Messaging  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Application Sharing Servers Inbound  |Any  |Application Sharing Servers  |TCP  |Any  |Any  |Do not authenticate  |
|Application Sharing Server Outbound  |Application Sharing Servers  |Any  |TCP  |Any  |Any  |Do not authenticate  |
|Exchange Outbound  |Exchange Unified Messaging  |Any  |UDP and TCP  |Any  |Any  |Do not authenticate  |
|Clients  |Any  |Any  |UDP  |Specified media port range  |Any  |Do not authenticate  |
