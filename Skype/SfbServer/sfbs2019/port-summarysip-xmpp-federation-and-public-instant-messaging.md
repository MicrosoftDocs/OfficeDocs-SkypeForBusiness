---
title: "Port summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab05bdd6-e9b0-4b1b-9dd9-29ab88e8befe
description: "In this articleFirewall Summary - SIP FederationFirewall Summary - Public Instant Messaging ConnectivityFirewall Summary - Extensible Messaging and Presence Protocol (XMPP)"
---

# Port summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013
[]
 **In this article**
  
[Firewall Summary - SIP Federation](#sectionSection0)
  
[Firewall Summary - Public Instant Messaging Connectivity](#sectionSection1)
  
[Firewall Summary - Extensible Messaging and Presence Protocol (XMPP)](#sectionSection2)
  
Port, protocol and firewall requirements for federation with Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server are similar to those for the deployed Edge Server. Clients initiate communication with the Access Edge service over TLS/SIP/TCP 443. Federated partners however, will initiate communications to the Access Edge service over MTLS/SIP/TCP 5061.
  
To configure your firewall for ports and protocols necessary to support public instant messaging connectivity, first note that SIP/MTLS/TCP 5061 is bidirectional to account for the ability of contacts in the public IM provider to contact Lync clients, or for Lync to contact public IM contacts.
  
Windows Live Messenger can participate in audio/video communications with Lync clients. This accounts for the very similar firewall port and protocol configuration that you would typically have on the firewall to support Lync clients as external users.
  
> [!IMPORTANT]
> More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard Client Access License (CAL). Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice. > Federation with Messenger client contacts will officially end on March 15, 2013, except for mainland China. Skype will become the federation client for federated users who previously used Messenger. 
  
The ports and protocols defined for the extensible messaging and presence protocol (XMPP) proxy deployed on the Edge Server allow communications from the XMPP federated partner to the Edge Server, and also allows communication from your Edge Server to the XMPP federated partner. A rule is also defined on the internal-facing firewall from the Front End Server or Front End pool to the Edge Server or Edge pool. 
  
## Firewall Summary - SIP Federation
<a name="sectionSection0"> </a>

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Access Edge service public IP address  <br/> |Any  <br/> |For federated and public IM connectivity using SIP  <br/> |
   
## Firewall Summary - Public Instant Messaging Connectivity
<a name="sectionSection1"> </a>

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Public IM connectivity partners  <br/> |Edge Server Access interface  <br/> |For federated and public IM connectivity that use SIP.  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Edge Server Access interface  <br/> |Public IM connectivity partners  <br/> |For federated and public IM connectivity that use SIP.  <br/> |
|Access/SIP(TLS)/TCP/443  <br/> |Clients  <br/> |Edge Server Access interface  <br/> |Client-to-server SIP traffic for external user access.  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Edge Server Access interface  <br/> |Live Messenger clients  <br/> |Used for A/V sessions with Windows Live Messenger if public IM connectivity is configured.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Edge Server Access interface  <br/> |Live Messenger clients  <br/> |Required for public IM connectivity with Windows Live Messenger.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Live Messenger clients  <br/> |Edge Server Access interface  <br/> |Required for public IM connectivity with Windows Live Messenger.  <br/> |
   
## Firewall Summary - Extensible Messaging and Presence Protocol (XMPP)
<a name="sectionSection2"> </a>

|**Protocol/TCP or UDP/Port**|**Source (IP address)**|**Destination (IP address)**|**Comments**|
|:-----|:-----|:-----|:-----|
|XMPP/TCP/5269  <br/> | Any  <br/> |Access Edge service interface IP address  <br/> |Standard server-to-server communication port for XMPP. Allows communication to the Edge Server XMPP proxy from federated XMPP partners  <br/> |
|XMPP/TCP/5269  <br/> |Access Edge service interface IP address  <br/> |Any  <br/> |Standard server-to-server communication port for XMPP. Allows communication from the Edge Server XMPP proxy to federated XMPP partners  <br/> |
|XMPP/MTLS/23456  <br/> |Any  <br/> |Internal Edge Server Interface IP  <br/> |Internal XMPP traffic from the XMPP Gateway on the Front End Server or Front End pool to the Edge Server  <br/> |
   
## See also
<a name="sectionSection2"> </a>

#### 

[Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)
  
[Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md)
#### 

[Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md)

