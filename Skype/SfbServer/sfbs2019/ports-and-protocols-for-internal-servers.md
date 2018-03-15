---
title: "Ports and protocols for internal servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 4/6/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c94063f1-e802-4a61-be90-022fc185335e
description: "This section summarizes the ports and protocols used by servers, load balancers, and clients in a Lync Server deployment."
---

# Ports and protocols for internal servers in Lync Server 2013
[]
This section summarizes the ports and protocols used by servers, load balancers, and clients in a Lync Server deployment.
  
> [!IMPORTANT]
> Lync and Communicator clients when involved in a one to one communication, is often referred to as peer-to-peer. Technically, the two clients are communicating in a one to one conversation, with the Instant Messaging multipoint control unit (IMMCU) in the middle. The IMMCU is a component of Front End Server. Placing the IMMCU in the required communication workflow allows call detail recording and other features that the Front End Server enables. Communication is from a dynamic source port on the client to the Front End Server port TLS/TCP/5061 (assuming the use of the recommended transport layer security). By design, peer-to-peer communication (as well as multi-party IM) is possible only when Lync Server and the IMMCU is active and available. 
  
## Port and Protocol Details

> [!NOTE]
> Windows Firewall must be running before you start the Lync Server services on a server, because that is when Lync Server opens the required ports in the firewall. 
  
For details about firewall configuration for edge components, see [Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md). 
  
The following table lists the ports that need to be open on each internal server role. 
  
**Required Server Ports (by Server Role)**

|**Server role**|**Service name**|**Port**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|All Servers  <br/> |SQL Browser  <br/> |1434  <br/> |UDP  <br/> |SQL Browser for the local replicated copy of the the Central Management Store database.  <br/> |
|Front End Servers  <br/> |Lync Server Front-End service  <br/> |5060  <br/> |TCP  <br/> |Optionally used by Standard Edition servers and Front End Servers for static routes to trusted services, such as remote call control servers.  <br/> |
|Front End Servers  <br/> |Lync Server Front-End service  <br/> |5061  <br/> | TCP (TLS)  <br/> |Used by Standard Edition servers and Front End pools for all internal SIP communications between servers (MTLS), for SIP communications between Server and Client (TLS) and for SIP communications between Front End Servers and Mediation Servers (MTLS). Also used for communications with Monitoring Server.  <br/> |
| Front End Servers  <br/> |Lync Server Front-End service  <br/> |444  <br/> | HTTPS  <br/> TCP  <br/> |Used for HTTPS communication between the Focus (the Lync Server component that manages conference state) and the individual servers.  <br/> This port is also used for TCP communication between Survivable Branch Appliances and Front End Servers.  <br/> |
|Front End Servers  <br/> |Lync Server Front-End service  <br/> |135  <br/> |DCOM and remote procedure call (RPC)  <br/> |Used for DCOM based operations such as Moving Users, User Replicator Synchronization, and Address Book Synchronization.  <br/> |
|Front End Servers  <br/> |Lync Server IM Conferencing service  <br/> |5062  <br/> |TCP  <br/> |Used for incoming SIP requests for instant messaging (IM) conferencing.  <br/> |
|Front End Servers  <br/> |Lync Server Web Conferencing service  <br/> |8057  <br/> |TCP (TLS)  <br/> |Used to listen for Persistent Shared Object Model (PSOM) connections from client.  <br/> |
|Front End Servers  <br/> |Lync Server Web Conferencing Compatibility service  <br/> |8058  <br/> |TCP (TLS)  <br/> |Used to listen for Persistent Shared Object Model (PSOM) connections from the Live Meeting client and previous versions of Lync Server.  <br/> |
|Front End Servers  <br/> |Lync Server Audio/Video Conferencing service  <br/> |5063  <br/> |TCP  <br/> |Used for incoming SIP requests for audio/video (A/V) conferencing.  <br/> |
|Front End Servers  <br/> |Lync Server Audio/Video Conferencing service  <br/> |57501-65535  <br/> |TCP/UDP  <br/> |Media port range used for video conferencing.  <br/> |
|Front End Servers  <br/> |Lync Server Web Compatibility service  <br/> |80  <br/> |HTTP  <br/> |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components) when HTTPS is not used.  <br/> |
|Front End Servers  <br/> |Lync Server Web Compatibility service  <br/> |443  <br/> |HTTPS  <br/> |Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components).  <br/> |
|Front End Servers  <br/> |Lync Server Web Compatibility service  <br/> |8080  <br/> |TCP and HTTP  <br/> |Used by web components for external access.  <br/> |
|Front End Servers  <br/> |Web server component  <br/> |4443  <br/> |HTTPS  <br/> |HTTPS (from Reverse Proxy) and HTTPS Front End inter-pool communications for Autodiscover sign-in.  <br/> |
|Front End Servers  <br/> |Web server component  <br/> |8060  <br/> |TCP (MTLS)  <br/> ||
|Front End Servers  <br/> |Web server component  <br/> |8061  <br/> |TCP (MTLS)  <br/> ||
|Front End Servers  <br/> |Mobility Services component  <br/> |5086  <br/> |TCP (MTLS)  <br/> |SIP port used by Mobility Services internal processes  <br/> |
|Front End Servers  <br/> |Mobility Services component  <br/> |5087  <br/> |TCP (MTLS)  <br/> |SIP port used by Mobility Services internal processes  <br/> |
|Front End Servers  <br/> |Mobility Services component  <br/> |443  <br/> |HTTPS  <br/> ||
|Front End Servers  <br/> |Lync Server Conferencing Attendant service (dial-in conferencing)  <br/> |5064  <br/> |TCP  <br/> |Used for incoming SIP requests for dial-in conferencing.  <br/> |
|Front End Servers  <br/> |Lync Server Conferencing Attendant service (dial-in conferencing)  <br/> |5072  <br/> |TCP  <br/> |Used for incoming SIP requests for Attendant (dial in conferencing).  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Lync Server Mediation service  <br/> |5070  <br/> |TCP  <br/> |Used by the Mediation Server for incoming requests from the Front End Server to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Lync Server Mediation service  <br/> |5067  <br/> |TCP (TLS)  <br/> |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Lync Server Mediation service  <br/> |5068  <br/> |TCP  <br/> |Used for incoming SIP requests from the PSTN gateway to the Mediation Server.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Lync Server Mediation service  <br/> |5081  <br/> |TCP  <br/> |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  <br/> |
|Front End Servers that also run a Collocated Mediation Server  <br/> |Lync Server Mediation service  <br/> |5082  <br/> |TCP (TLS)  <br/> |Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.  <br/> |
|Front End Servers  <br/> |Lync Server Application Sharing service  <br/> |5065  <br/> |TCP  <br/> |Used for incoming SIP listening requests for application sharing.  <br/> |
|Front End Servers  <br/> |Lync Server Application Sharing service  <br/> |49152-65535  <br/> |TCP  <br/> |Media port range used for application sharing.  <br/> |
|Front End Servers  <br/> |Lync Server Conferencing Announcement service  <br/> |5073  <br/> |TCP  <br/> |Used for incoming SIP requests for the Lync Server Conferencing Announcement service (that is, for dial-in conferencing).  <br/> |
|Front End Servers  <br/> |Lync Server Call Park service  <br/> |5075  <br/> |TCP  <br/> |Used for incoming SIP requests for the Call Park application.  <br/> |
|Front End Servers  <br/> |Lync Server Audio Test service  <br/> |5076  <br/> |TCP  <br/> |Used for incoming SIP requests for the Audio Test service.  <br/> |
|Front End Servers  <br/> |Not applicable  <br/> |5066  <br/> |TCP  <br/> |Used for outbound Enhanced 9-1-1 (E9-1-1) gateway.  <br/> |
|Front End Servers  <br/> |Lync Server Response Group service  <br/> |5071  <br/> |TCP  <br/> |Used for incoming SIP requests for the Response Group application.  <br/> |
|Front End Servers  <br/> |Lync Server Response Group service  <br/> |8404  <br/> |TCP (MTLS)  <br/> |Used for incoming SIP requests for the Response Group application.  <br/> |
|Front End Servers  <br/> |Lync Server Bandwidth Policy Service  <br/> |5080  <br/> |TCP  <br/> |Used for call admission control by the Bandwidth Policy service for A/V Edge TURN traffic.  <br/> |
|Front End Servers  <br/> |Lync Server Bandwidth Policy Service  <br/> |448  <br/> |TCP  <br/> |Used for call admission control by the Lync Server Bandwidth Policy Service.  <br/> |
|Front End Servers where the Central Management store resides  <br/> |Lync Server Master Replicator Agent service  <br/> |445  <br/> |TCP  <br/> |Used to push configuration data from the Central Management store to servers running Lync Server.  <br/> |
|All Servers  <br/> |SQL Browser  <br/> |1434  <br/> |UDP  <br/> |SQL Browser for local replicated copy of Central Management store data in local SQL Server instance  <br/> |
|All internal servers  <br/> |Various  <br/> |49152-57500  <br/> |TCP/UDP  <br/> |Media port range used for audio conferencing on all internal servers. Used by all servers that terminate audio: Front End Servers (for Lync Server Conferencing Attendant service, Lync Server Conferencing Announcement service, and Lync Server Audio/Video Conferencing service), and Mediation Server.  <br/> |
|Office Web Apps Servers  <br/> ||443  <br/> ||Used by Lync Server 2013 to connect to Office Web Apps Server.  <br/> |
|Directors  <br/> |Lync Server Front-End service  <br/> |5060  <br/> |TCP  <br/> |Optionally used for static routes to trusted services, such as remote call control servers.  <br/> |
|Directors  <br/> |Lync Server Front-End service  <br/> |444  <br/> |HTTPS  <br/> TCP  <br/> |Inter-server communication between Front End and Director. Additionally, client certificate publish (to Front End Servers) or validate if the client certificate has already been published.  <br/> |
|Directors  <br/> |Lync Server Web Compatibility service  <br/> |80  <br/> |TCP  <br/> |Used for initial communication from Directors to the web farm FQDNs (the URLs used by IIS web components). In normal operation, will switch to HTTPS traffic, using port 443 and protocol type TCP.  <br/> |
|Directors  <br/> |Lync Server Web Compatibility service  <br/> |443  <br/> |HTTPS  <br/> |Used for communication from Directors to the web farm FQDNs (the URLs used by IIS web components).  <br/> |
|Directors  <br/> |Lync Server Front-End service  <br/> |5061  <br/> |TCP  <br/> |Used for internal communications between servers and for client connections.  <br/> |
|Mediation Servers  <br/> |Lync Server Mediation service  <br/> |5070  <br/> |TCP  <br/> |Used by the Mediation Server for incoming requests from the Front End Server.  <br/> |
|Mediation Servers  <br/> |Lync Server Mediation service  <br/> |5067  <br/> |TCP (TLS)  <br/> |Used for incoming SIP requests from the PSTN gateway.  <br/> |
|Mediation Servers  <br/> |Lync Server Mediation service  <br/> |5068  <br/> |TCP  <br/> |Used for incoming SIP requests from the PSTN gateway.  <br/> |
|Mediation Servers  <br/> |Lync Server Mediation service  <br/> |5070  <br/> |TCP (MTLS)  <br/> |Used for SIP requests from the Front End Servers.  <br/> |
|Persistent Chat Front End Server  <br/> |Persistent Chat SIP  <br/> |5041  <br/> |TCP (MTLS)  <br/> ||
|Persistent Chat Front End Server  <br/> |Persistent Chat Windows Communication Foundation (WCF)  <br/> |881  <br/> |TCP (TLS) and TCP (MTLS)  <br/> ||
|Persistent Chat Front End Server  <br/> |Persistent Chat File Transfer Service  <br/> |443  <br/> |TCP (TLS)  <br/> ||
   
> [!NOTE]
> Some remote call control scenarios require a TCP connection between the Front End Server or Director and the PBX. Although Lync Server no longer uses TCP port 5060, during remote call control deployment you create a trusted server configuration, which associates the RCC Line Server FQDN with the TCP port that the Front End Server or Director will use to connect to the PBX system. For details, see the **CsTrustedApplicationComputer** cmdlet in the Lync Server Management Shell documentation. 
  
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
||||
|Director load balancer  <br/> |4443  <br/> |HTTPS (from reverse proxy)  <br/> |
   
**Required Client Ports**

|**Component**|**Port**|**Protocol**|**Notes**|
|:-----|:-----|:-----|:-----|
|Clients  <br/> |67/68  <br/> |DHCP  <br/> |Used by Lync Server to find the Registrar FQDN (that is, if DNS SRV fails and manual settings are not configured).  <br/> |
|Clients  <br/> |443  <br/> |TCP (TLS)  <br/> |Used for client-to-server SIP traffic for external user access.  <br/> |
|Clients  <br/> |443  <br/> |TCP (PSOM/TLS)  <br/> |Used for external user access to web conferencing sessions.  <br/> |
|Clients  <br/> |443  <br/> |TCP (STUN/MSTURN)  <br/> |Used for external user access to A/V sessions and media (TCP)  <br/> |
|Clients  <br/> |3478  <br/> |UDP (STUN/MSTURN)  <br/> |Used for external user access to A/V sessions and media (UDP)  <br/> |
|Clients  <br/> |5061  <br/> |TCP (MTLS)  <br/> |Used for client-to-server SIP traffic for external user access.  <br/> |
|Clients  <br/> |6891-6901  <br/> |TCP  <br/> |Used for file transfer between Lync clients and previous clients (clients of Microsoft Office Communications Server 2007 R2, Microsoft Office Communications Server 2007, and Live Communications Server 2005).  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP/UDP  <br/> |Audio port range (minimum of 20 ports required)  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP/UDP  <br/> |Video port range (minimum of 20 ports required).  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP  <br/> |Peer-to-peer file transfer (for conferencing file transfer, clients use PSOM).  <br/> |
|Clients  <br/> |1024-65535 \*  <br/> |TCP  <br/> |Application sharing.  <br/> |
|Aastra 6721ip common area phone  <br/> Aastra 6725ip desk phone  <br/> HP 4110 IP Phone (common area phone)  <br/> HP 4120 IP Phone (desk phone)  <br/> Polycom CX500 IP common area phone  <br/> Polycom CX600 IP desk phone  <br/> Polycom CX700 IP desk phone  <br/> Polycom CX3000 IP conference phone  <br/> |67/68  <br/> |DHCP  <br/> |Used by the listed devices to find the Lync Server certificate, provisioning FQDN, and Registrar FQDN.  <br/> |
   
 **\*** To configure specific ports for these media types, use the CsConferencingConfiguration cmdlet (ClientMediaPortRangeEnabled, ClientMediaPort, and ClientMediaPortRange parameters). 
  
> [!NOTE]
> The set programs for Lync clients automatically create the required operating-system firewall exceptions on the client computer. 
  
> [!NOTE]
> The ports that are used for external user access are required for any scenario in which the client must traverse the organization's firewall (for example, any external communications or meetings hosted by other organizations). 
  

