---
title: "Port and protocol requirements for servers"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/15/2018
ms.audience: ITPro
ms.topic: concetpual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Admin
ms.assetid: c94063f1-e802-4a61-be90-022fc185335e
description: "Summary: Review the port usage considerations before implementing Skype for Business Server 2015."
---

# Port and protocol requirements for servers
 
**Summary:** Review the port usage considerations before implementing Skype for Business Server 2015.
  
Skype for Business Server requires that specific ports on the external and internal firewalls be open. Additionally, if Internet Protocol security (IPsec) is deployed in your organization, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. 
  
While this may seem a bit daunting at first, the heavy lifting for planning this can be done using the [Skype for Business Server 2015 Planning Tool](https://www.microsoft.com/en-us/download/details.aspx?id=50357). Once you've gone through the wizard's questions about what features you plan to use, for each site you define you can view the Firewall Report within the Edge Admin Report, and use the information listed there to create yourfirewall rules. You can also make adjustments to many of the names and IP addresses used, for details see [Review the Firewall Report](../../management-tools/planning-tool/review-the-administrator-reports.md#Firewall_report). Keep in mind you can export the Edge Admin Report to an Excel spreadsheet, and the Firewall Report will be one of the worksheets in the file. 
  
You can also find the information in these tables in diagram form by reviewing the Protocol Workloads poster linked off of the [Technical diagrams for Skype for Business Server 2015](../../technical-diagrams.md) article.
  
## Port and Protocol Details

This section summarizes the ports and protocols used by servers, load balancers, and clients in a Skype for Business Server deployment.
  
> [!NOTE]
> When Skype for Business Server starts, it opens the required ports in the Windows Firewall. Windows Firewall should already be running in most normal applications, but if it is not being used Skype for Business Server will function without it. 
  
For details about firewall configuration for edge components, see [Edge Server scenarios in Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/scenarios.md). 
  
The following table lists the ports that need to be open on each internal server role. 
  
**Required Server Ports (by Server Role)**

|**Server role**|**Service name**|**Port**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|All Servers  <br/> |SQL Browser  <br/> |1434  <br/> |UDP  <br/> |SQL Browser for the local replicated copy of the the Central Management Store database.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Front-End service  <br/> |5060  <br/> |TCP  <br/> |Optionally used by Standard Edition servers and Front End Servers for static routes to trusted services, such as remote call control servers.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Front-End service  <br/> |5061  <br/> | TCP (TLS) <br/> |Used by Standard Edition servers and Front End pools for all internal SIP communications between servers (MTLS), for SIP communications between Server and Client (TLS) and for SIP communications between Front End Servers and Mediation Servers (MTLS). Also used for communications with a Monitoring Server.  <br/> |
| Front End Servers <br/> |Skype for Business Server Front-End service  <br/> |444  <br/> | HTTPS <br/> TCP  <br/> |Used for HTTPS communication between the Focus (the Skype for Business Server component that manages conference state) and the individual servers.  <br/> This port is also used for TCP communication between Survivable Branch Appliances and Front End Servers.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Front-End service  <br/> |135  <br/> |DCOM and remote procedure call (RPC)  <br/> |Used for DCOM based operations such as Moving Users, User Replicator Synchronization, and Address Book Synchronization.  <br/> |
|Front End Servers  <br/> |Skype for Business Server IM Conferencing service  <br/> |5062  <br/> |TCP  <br/> |Used for incoming SIP requests for instant messaging (IM) conferencing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Web Conferencing service  <br/> |8057  <br/> |TCP (TLS)  <br/> |Used to listen for Persistent Shared Object Model (PSOM) connections from client.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Web Conferencing Compatibility service  <br/> |8058  <br/> |TCP (TLS)  <br/> |Used to listen for Persistent Shared Object Model (PSOM) connections from the Live Meeting client and previous versions of Skype for Business Server.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Audio/Video Conferencing service  <br/> |5063  <br/> |TCP  <br/> |Used for incoming SIP requests for audio/video (A/V) conferencing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Audio/Video Conferencing service  <br/> |57501-65535  <br/> |TCP/UDP  <br/> |Media port range used for video conferencing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Web Compatibility service  <br/> |80  <br/> |HTTP  <br/> |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components) when HTTPS is not used.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Web Compatibility service  <br/> |443  <br/> |HTTPS  <br/> |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components).  <br/> |
|Front End Servers  <br/> |Skype for Business Server Web Compatibility service  <br/> |8080  <br/> |TCP and HTTP  <br/> |Used by web components for external access.  <br/> |
|Front End Servers  <br/> |Web server component  <br/> |4443  <br/> |HTTPS  <br/> |HTTPS (from Reverse Proxy) and HTTPS Front End inter-pool communications for Autodiscover sign-in.  <br/> |
|Front End Servers  <br/> |Web server component  <br/> |8060  <br/> |TCP (MTLS)  <br/> ||
|Front End Servers  <br/> |Web server component  <br/> |8061  <br/> |TCP (MTLS)  <br/> ||
|Front End Servers  <br/> |Mobility Services component  <br/> |5086  <br/> |TCP (MTLS)  <br/> |SIP port used by Mobility Services internal processes  <br/> |
|Front End Servers  <br/> |Mobility Services component  <br/> |5087  <br/> |TCP (MTLS)  <br/> |SIP port used by Mobility Services internal processes  <br/> |
|Front End Servers  <br/> |Mobility Services component  <br/> |443  <br/> |HTTPS  <br/> ||
|Front End Servers  <br/> |Skype for Business Server Conferencing Attendant service (dial-in conferencing)  <br/> |5064  <br/> |TCP  <br/> |Used for incoming SIP requests for dial-in conferencing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Conferencing Attendant service (dial-in conferencing)  <br/> |5072  <br/> |TCP  <br/> |Used for incoming SIP requests for Attendant (dial in conferencing).  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Skype for Business Server Mediation service  <br/> |5070  <br/> |TCP  <br/> |Used by the Mediation Server for incoming requests from the Front End Server to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Skype for Business Server Mediation service  <br/> |5067  <br/> |TCP (TLS)  <br/> |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Skype for Business Server Mediation service  <br/> |5068  <br/> |TCP  <br/> |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Skype for Business Server Mediation service  <br/> |5081  <br/> |TCP  <br/> |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Skype for Business Server Mediation service  <br/> |5082  <br/> |TCP (TLS)  <br/> |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Application Sharing service  <br/> |5065  <br/> |TCP  <br/> |Used for incoming SIP listening requests for application sharing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Application Sharing service  <br/> |49152-65535  <br/> |TCP  <br/> |Media port range used for application sharing.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Conferencing Announcement service  <br/> |5073  <br/> |TCP  <br/> |Used for incoming SIP requests for the Skype for Business Server Conferencing Announcement service (that is, for dial-in conferencing).  <br/> |
|Front End Servers  <br/> |Skype for Business Server Call Park service  <br/> |5075  <br/> |TCP  <br/> |Used for incoming SIP requests for the Call Park application.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Audio Test service  <br/> |5076  <br/> |TCP  <br/> |Used for incoming SIP requests for the Audio Test service.  <br/> |
|Front End Servers  <br/> |Not applicable  <br/> |5066  <br/> |TCP  <br/> |Used for outbound Enhanced 9-1-1 (E9-1-1) gateway.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Response Group service  <br/> |5071  <br/> |TCP  <br/> |Used for incoming SIP requests for the Response Group application.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Response Group service  <br/> |8404  <br/> |TCP (MTLS)  <br/> |Used for incoming SIP requests for the Response Group application.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Bandwidth Policy Service  <br/> |5080  <br/> |TCP  <br/> |Used for call admission control by the Bandwidth Policy service for A/V Edge TURN traffic.  <br/> |
|Front End Servers  <br/> |Skype for Business Server Bandwidth Policy Service  <br/> |448  <br/> |TCP  <br/> |Used for call admission control by the Skype for Business Server Bandwidth Policy Service.  <br/> |
|Front End Servers where the Central Management store resides  <br/> | Skype for Business Server Master Replicator Agent service <br/> |445  <br/> |TCP  <br/> |Used to push configuration data from the Central Management store to servers running Skype for Business Server.  <br/> |
|All Servers  <br/> |SQL Browser  <br/> |1434  <br/> |UDP  <br/> |SQL Browser for local replicated copy of Central Management store data in local SQL Server instance  <br/> |
|All internal servers  <br/> |Various  <br/> |49152-57500  <br/> |TCP/UDP  <br/> |Media port range used for audio conferencing on all internal servers. Used by all servers that terminate audio: Front End Servers (for Skype for Business Server Conferencing Attendant service, Skype for Business Server Conferencing Announcement service, and Skype for Business Server Audio/Video Conferencing service), and Mediation Server.  <br/> |
|Office Web Apps Servers  <br/> ||443  <br/> ||Used by Skype for Business Server 2015 to connect to Office Web Apps Server.  <br/> |
|Directors  <br/> |Skype for Business Server Front-End service  <br/> |5060  <br/> |TCP  <br/> |Optionally used for static routes to trusted services, such as remote call control servers.  <br/> |
|Directors  <br/> |Skype for Business Server Front-End service  <br/> |444  <br/> |HTTPS  <br/> TCP  <br/> |Inter-server communication between Front End and Director. Additionally, client certificate publish (to Front End Servers) or validate if the client certificate has already been published.  <br/> |
|Directors  <br/> |Skype for Business Server Web Compatibility service  <br/> |80  <br/> |TCP  <br/> |Used for initial communication from Directors to the web farm FQDNs (the URLs used by IIS web components). In normal operation, will switch to HTTPS traffic, using port 443 and protocol type TCP.  <br/> |
|Directors  <br/> |Skype for Business Server Web Compatibility service  <br/> |443  <br/> |HTTPS  <br/> |Used for communication from Directors to the web farm FQDNs (the URLs used by IIS web components).  <br/> |
|Directors  <br/> |Skype for Business Server Front-End service  <br/> |5061  <br/> |TCP  <br/> |Used for internal communications between servers and for client connections.  <br/> |
|Mediation Servers  <br/> |Skype for Business Server Mediation service  <br/> |5070  <br/> |TCP  <br/> |Used by the Mediation Server for incoming requests from the Front End Server.  <br/> |
|Mediation Servers  <br/> |Skype for Business Server Mediation service  <br/> |5067  <br/> |TCP (TLS)  <br/> |Used for incoming SIP requests from the PSTN gateway.  <br/> |
|Mediation Servers  <br/> |Skype for Business Server Mediation service  <br/> |5068  <br/> |TCP  <br/> |Used for incoming SIP requests from the PSTN gateway.  <br/> |
|Mediation Servers  <br/> |Skype for Business Server Mediation service  <br/> |5070  <br/> |TCP (MTLS)  <br/> |Used for SIP requests from the Front End Servers.  <br/> |
|Persistent Chat Front End Server  <br/> |Persistent Chat SIP  <br/> |5041  <br/> |TCP (MTLS)  <br/> ||
|Persistent Chat Front End Server  <br/> |Persistent Chat Windows Communication Foundation (WCF)  <br/> |881  <br/> |TCP (TLS) and TCP (MTLS)  <br/> ||
|Persistent Chat Front End Server  <br/> |Persistent Chat File Transfer Service  <br/> |443  <br/> |TCP (TLS)  <br/> ||
   
> [!NOTE]
> Some remote call control scenarios require a TCP connection between the Front End Server or Director and the PBX. Although Skype for Business Server no longer uses TCP port 5060, during remote call control deployment you create a trusted server configuration, which associates the RCC Line Server FQDN with the TCP port that the Front End Server or Director will use to connect to the PBX system. For details, see the **CsTrustedApplicationComputer** cmdlet in the Skype for Business Server Management Shell documentation.
  
For your pools that use only hardware load balancing (not DNS load balancing), the following table shows the ports that need to open the hardware load balancers.
  
**Hardware Load Balancer Ports if Using Only Hardware Load Balancing**

|**Load Balancer**|**Port**|**Protocol**|
|:-----|:-----|:-----|
|Front End Server load balancer  <br/> |5061  <br/> |TCP (TLS)  <br/> |
|Front End Server load balancer  <br/> |444  <br/> |HTTPS  <br/> |
|Front End Server load balancer  <br/> |135  <br/> |DCOM and remote procedure call (RPC)  <br/> |
|Front End Server load balancer  <br/> |80  <br/> |HTTP  <br/> |
|Front End Server load balancer  <br/> |8080  <br/> |TCP - Client and device retrieval of root certificate from Front End Server - clients and devices authenticated by NTLM  <br/> |
|Front End Server load balancer  <br/> |443  <br/> |HTTPS  <br/> |
|Front End Server load balancer  <br/> |4443  <br/> |HTTPS (from reverse proxy)  <br/> |
|Front End Server load balancer  <br/> |5072  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |5073  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |5075  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |5076  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |5071  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |5080  <br/> |TCP  <br/> |
|Front End Server load balancer  <br/> |448  <br/> |TCP  <br/> |
|Mediation Server load balancer  <br/> |5070  <br/> |TCP  <br/> |
|Front End Server load balancer (if the pool also runs Mediation Server)  <br/> |5070  <br/> |TCP  <br/> |
|Director load balancer  <br/> |443  <br/> |HTTPS  <br/> |
|Director load balancer  <br/> |444  <br/> |HTTPS  <br/> |
|Director load balancer  <br/> |5061  <br/> |TCP  <br/> |
|Director load balancer  <br/> |4443  <br/> |HTTPS (from reverse proxy)  <br/> |
   
Your Front End pools and Director pools that use DNS load balancing also must have a hardware load balancer deployed. The following table shows the ports that need to be open on these hardware load balancers.
  
**Hardware Load Balancer Ports if Using DNS Load Balancing**

|**Load Balancer**|**Port**|**Protocol**|
|:-----|:-----|:-----|
|Front End Server load balancer  <br/> |80  <br/> |HTTP  <br/> |
|Front End Server load balancer  <br/> |443  <br/> |HTTPS  <br/> |
|Front End Server load balancer  <br/> |8080  <br/> |TCP - Client and device retrieval of root certificate from Front End Server - clients and devices authenticated by NTLM  <br/> |
|Front End Server load balancer  <br/> |4443  <br/> |HTTPS (from reverse proxy)  <br/> |
|Director load balancer  <br/> |443  <br/> |HTTPS  <br/> |
|Director load balancer  <br/> |4443  <br/> |HTTPS (from reverse proxy)  <br/> |
   
**Required Client Ports**

|**Component**|**Port**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|
|Clients  <br/> |67/68  <br/> |DHCP  <br/> |Used by Skype for Business Server to find the Registrar FQDN (that is, if DNS SRV fails and manual settings are not configured).  <br/> |
|Clients  <br/> |443  <br/> |TCP (TLS)  <br/> |Used for client-to-server SIP traffic for external user access.  <br/> |
|Clients  <br/> |443  <br/> |TCP (PSOM/TLS)  <br/> |Used for external user access to web conferencing sessions.  <br/> |
|Clients  <br/> |443  <br/> |TCP (STUN/MSTURN)  <br/> |Used for external user access to A/V sessions and media (TCP)  <br/> |
|Clients  <br/> |3478  <br/> |UDP (STUN/MSTURN)  <br/> |Used for external user access to A/V sessions and media (UDP)  <br/> |
|Clients  <br/> |5061  <br/> |TCP (MTLS)  <br/> |Used for client-to-server SIP traffic for external user access.  <br/> |
|Clients  <br/> |6891-6901  <br/> |TCP  <br/> |Used for file transfer between Skype for Business clients and previous clients.  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP/UDP  <br/> |Audio port range (minimum of 20 ports required)  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP/UDP  <br/> |Video port range (minimum of 20 ports required).  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP  <br/> |Peer-to-peer file transfer (for conferencing file transfer, clients use PSOM).  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP  <br/> |Application sharing.  <br/> |
|Aastra 6721ip common area phone  <br/> Aastra 6725ip desk phone  <br/> HP 4110 IP Phone (common area phone)  <br/> HP 4120 IP Phone (desk phone)  <br/> Polycom CX500 IP common area phone  <br/> Polycom CX600 IP desk phone  <br/> Polycom CX700 IP desk phone  <br/> Polycom CX3000 IP conference phone  <br/> |67/68  <br/> |DHCP  <br/> |Used by the listed devices to find the Skype for Business Server certificate, provisioning FQDN, and Registrar FQDN.  <br/> |
   
\* To configure specific ports for these media types, use the CsConferencingConfiguration cmdlet (ClientMediaPortRangeEnabled, ClientMediaPort, and ClientMediaPortRange parameters).
  
> [!NOTE]
> The setup programs for Skype for Business clients automatically create the required operating-system firewall exceptions on the client computer. 
  
> [!NOTE]
> The ports that are used for external user access are required for any scenario in which the client must traverse the organization's firewall (for example, any external communications or meetings hosted by other organizations). 
  
## IPsec exceptions

For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panoramic video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation.
  
The following table explains the recommended IPsec exception settings. 
  
**Recommended IPsec Exceptions**

|**Rule name**|**Source IP**|**Destination IP**|**Protocol**|**Source port**|**Destination port**|**Authentication Requirement**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|A/V Edge Server Internal Inbound  <br/> |Any  <br/> |A/V Edge Server Internal  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server External Inbound  <br/> |Any  <br/> |A/V Edge Server External  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server Internal Outbound  <br/> |A/V Edge Server Internal  <br/> |Any  <br/> |UDP &amp; TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Edge Server External Outbound  <br/> |A/V Edge Server External  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Mediation Server Inbound  <br/> |Any  <br/> |Mediation  <br/> Server(s)  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Mediation Server Outbound  <br/> |Mediation  <br/> Server(s)  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Conferencing Attendant Inbound  <br/> |Any  <br/> |Front End Server running Conferencing Attendant  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Conferencing Attendant Outbound  <br/> |Front End Server running Conferencing Attendant  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Conferencing Inbound  <br/> |Any  <br/> |Front End Servers  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|A/V Conferencing Outbound  <br/> |Front End Servers  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Exchange Inbound  <br/> |Any  <br/> |Exchange Unified Messaging  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Application Sharing Servers Inbound  <br/> |Any  <br/> |Application Sharing Servers  <br/> |TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Application Sharing Server Outbound  <br/> |Application Sharing Servers  <br/> |Any  <br/> |TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Exchange Outbound  <br/> |Exchange Unified Messaging  <br/> |Any  <br/> |UDP and TCP  <br/> |Any  <br/> |Any  <br/> |Do not authenticate  <br/> |
|Clients  <br/> |Any  <br/> |Any  <br/> |UDP  <br/> |Specified media port range  <br/> |Any  <br/> |Do not authenticate  <br/> |
   

