---
title: "Common security threats in modern day computing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/22/2016
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 56d22197-e8e2-46b8-b3a3-507bd663700e
description: "Because Skype for Business Server is an enterprise-class communications system, you should be aware of common security attacks that could affect its infrastructure and communications."
---

# Common security threats in modern day computing
 
Because Skype for Business Server is an enterprise-class communications system, you should be aware of common security attacks that could affect its infrastructure and communications.
  
## Compromised-Key Attack

A key is a secret code or number that is used to encrypt, decrypt, or validate secret information. There are two sensitive keys in use in public key infrastructure (PKI) that must be considered: 
  
- The private key that each certificate holder has
    
- The session key that is used after a successful identification and session key exchange by the communicating partners
    
A compromised-key attack occurs when the attacker determines the private key or the session key. When the attacker is successful in determining the key, the attacker can use the key to decrypt encrypted data without the knowledge of the sender.
  
Skype for Business Server uses the PKI features in the Windows Server operating system to protect the key data used for encryption for the Transport Layer Security (TLS) connections. The keys used for media encryption are exchanged over TLS connections.
  
## Network Denial-of-Service Attack

The denial-of-service attack occurs when the attacker prevents normal network use and function by valid users. This is done when the attacker floods the service with legitimate requests that overwhelm the use of the service by legitimate users. By using a denial-of-service attack, the attacker can do the following:
  
- Send invalid data to applications and services running in the attacked network to disrupt their normal function.
    
- Send a large amount of traffic, overloading the system until it stops responding or responds slowly to legitimate requests.
    
- Hide the evidence of the attacks.
    
- Prevent users from accessing network resources.
    
## Eavesdropping (Sniffing, Snooping)

Eavesdropping can occur when an attacker gains access to the data path in a network and has the ability to monitor and read the traffic. This is also called sniffing or snooping. If the traffic is in plain text, the attacker can read the traffic when the attacker gains access to the path. An example is an attack performed by controlling a router on the data path. 
  
The default recommendation and setting for traffic within Skype for Business Server is to use mutual TLS (MTLS) between trusted servers and TLS from client to server. This protective measure would make an attack very difficult or impossible to achieve within the time period in which a given conversation occurs. TLS authenticates all parties and encrypts all traffic. This does not prevent eavesdropping, but the attacker cannot read the traffic unless the encryption is broken.
  
The Traversal Using Relay NAT (TURN) protocol does not mandate the traffic to be encrypted and the information that it is sending is protected by message integrity. Although it is open to eavesdropping, the information it is sending (that is, the IP addresses and port) can be extracted directly by simply looking at the source and destination addresses of the packets. The A/V Edge service ensures that the data is valid by checking the Message Integrity of the message by using the key derived from a few items, including a TURN password, which is never sent in clear text. If Secure Real Time Protocol (SRTP) is used, media traffic is also encrypted.
  
## Identity Spoofing (IP Address and Caller Id Spoofing)

Identity Spoofing occurs when the attacker determines and uses a phone number of a valid user (caller id) or an IP address of a network, computer, or network component without being authorized to do so. A successful attack allows the attacker to operate as if the attacker is the entity normally identified by the phone number (caller id) or the IP address.

Within the context of Skype for Business Server, IP Address Spoofing comes into play only if an administrator has done both of the following:
  
- Configured connections that support only Transmission Control Protocol (TCP) (which is not recommended, because TCP communications are unencrypted).
    
- Marked the IP addresses of those connections as trusted hosts.
    
This is less of a problem for Transport Layer Security (TLS) connections, as TLS authenticates all parties and encrypts all traffic. Using TLS prevents an attacker from performing IP address spoofing on a specific connection (for example, mutual TLS connections). But an attacker could still spoof the address of the DNS server that Skype for Business Server uses. However, because authentication in Skype for Business is performed with certificates, an attacker would not have a valid certificate required to spoof one of the parties in the communication.

On the other hand, Caller Id Spoofing comes into play when you have established a SIP trunk between a provider, PSTN gateway or another PBX system and Skype for Business Server. In these cases, Skype for Business Server does not offer any protection to prevent against caller id spoofing. This means that a Skype for Business user can receive a call from the SIP trunk with a spoofed caller id displaying the phone number or display name (if reverse number lookup applies) of another Skype for Business user. Protection to this should be applied on the provider side, PSTN or PBX gateway.
  
## Man-in-the-Middle Attack

A man-in-the-middle attack occurs when an attacker reroutes communication between two users through the attacker's computer without the knowledge of the two communicating users. The attacker can monitor and read the traffic before sending it on to the intended recipient. Each user in the communication unknowingly sends traffic to and receives traffic from the attacker, all while thinking they are communicating only with the intended user. This can happen if an attacker can modify Active Directory Domain Services to add his or her server as a trusted server or modify Domain Name System (DNS) to get clients to connect through the attacker on their way to the server. A man-in-the-middle attack can also occur with media traffic between two clients. However, in Skype for Business Server point-to-point audio, video, and application sharing, streams are encrypted with SRTP, using cryptographic keys that are negotiated between the peers that are using Session Initiation Protocol (SIP) over TLS. Servers such as Group Chat make use of HTTPS to enhance the security of web traffic.
  
## RTP Replay Attack

A replay attack occurs when a valid media transmission between two parties is intercepted and retransmitted for malicious purposes. SRTP used in connection with a secure signaling protocol protects transmissions from replay attacks by enabling the receiver to maintain an index of already received RTP packets and compare each new packet with those already listed in the index.
  
## Spim

Spim is unsolicited commercial instant messages or presence subscription requests. While not by itself a compromise of the network, it is annoying in the least, can reduce resource availability and production, and can possibly lead to a compromise of the network. An example of this is users spimming each other by sending requests. Users can block each other to prevent this, but with federation, if a coordinated spim attack is established, this can be difficult to overcome unless you disable federation for the partner.
  
## Viruses and Worms

A virus is a unit of code whose purpose is to reproduce additional, similar code units. To work, a virus needs a host, such as a file, email, or program. Aworm is a unit of code whose purpose is to reproduce additional, similar code units, but it does not need a host. Viruses and worms primarily show up during file transfers between clients or when URLs are sent from other users. If a virus is on your computer, it can, for example, use your identity and send instant messages on your behalf.
  
## Personally Identifiable Information

Skype for Business Server has the potential to disclose information over a public network that might be able to be linked to an individual. The information types can be broken down to two specific categories:
  
- **Enhanced presence data** Enhanced presence data is information that a user can choose to share or not share over a link to a federated partner or with contacts within an organization. This data is not shared with users on a public IM network. Client policies and other client configuration may put some control with the system administrator. In Skype for Business Server, enhanced presence privacy mode can be configured for an individual user to prevent Skype for Business users not on the user's Contacts list from seeing the user's presence information. Enhanced presence privacy mode does not prevent users of Microsoft Office Communicator 2007 and Microsoft Office Communicator 2007 R2 from seeing a user's presence information. For details about deploying the client and presence, see [Deploy clients for Skype for Business Server](../../deploy/deploy-clients/deploy-clients.md) and [Plan for instant messaging and presence in Skype for Business Server](../../plan-your-deployment/instant-messaging-and-presence.md).
    
- **Mandatory data** Mandatory data is required for the proper operation of the server or the client and is NOT under the control of the client or system administration. This is information that is necessary at a server or network level for the purposes of routing, state maintenance, and signaling.
    
The following tables list the data that is exposed over a public network.
  
**Enhanced Presence Data**

|**Data Disclosed**|**Possible Settings**|
|:-----|:-----|
|Personal Data  <br/> |Name, Title, Company, Email Address, Time Zone  <br/> |
|Telephone Numbers  <br/> |Work, Mobile, Home  <br/> |
|Calendar Information  <br/> |Free/Busy, Out-Of-Town Notice, Meeting Details (to those who have access to your calendar)  <br/> |
|Presence Status  <br/> |Away, Available, Busy, Do Not Disturb, Offline  <br/> |
   
**Mandatory Data**


| **Data Disclosed** | **Example Information**                            |
|:-------------------|:---------------------------------------------------|
| IP Address  <br/>  | Actual address of computer or NATed address  <br/> |
| SIP URI  <br/>     | jeremylos@litwareinc.com  <br/>                    |

