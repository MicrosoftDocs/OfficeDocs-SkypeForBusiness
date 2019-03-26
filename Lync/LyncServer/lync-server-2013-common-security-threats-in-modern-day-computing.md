---
title: 'Lync Server 2013: Common security threats in modern day computing'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Common security threats in modern day computing
ms:assetid: 56d22197-e8e2-46b8-b3a3-507bd663700e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn433220(v=OCS.15)
ms:contentKeyID: 56708403
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Common security threats in modern day computing

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-09-10_

Because Lync Server 2013 is an enterprise-class communications system, you should be aware of common security attacks that could affect its infrastructure and communications.

<div>

## Compromised-Key Attack

A key is a secret code or number that is used to encrypt, decrypt, or validate secret information. There are two sensitive keys in use in public key infrastructure (PKI) that must be considered: .

  - The private key that each certificate holder has

  - The session key that is used after a successful identification and session key exchange by the communicating partners

A compromised-key attack occurs when the attacker determines the private key or the session key. When the attacker is successful in determining the key, the attacker can use the key to decrypt encrypted data without the knowledge of the sender.

Lync Server 2013 uses the PKI features in the Windows Server operating system to protect the key data used for encryption for the Transport Layer Security (TLS) connections. The keys used for media encryption are exchanged over TLS connections.

</div>

<div>

## Network Denial-of-Service Attack

The *denial-of-service attack* occurs when the attacker prevents normal network use and function by valid users. This is done when the attacker floods the service with legitimate requests that overwhelm the use of the service by legitimate users. By using a denial-of-service attack, the attacker can do the following:

  - Send invalid data to applications and services running in the attacked network to disrupt their normal function.

  - Send a large amount of traffic, overloading the system until it stops responding or responds slowly to legitimate requests.

  - Hide the evidence of the attacks.

  - Prevent users from accessing network resources.

</div>

<div>

## Eavesdropping (Sniffing, Snooping)

*Eavesdropping* can occur when an attacker gains access to the data path in a network and has the ability to monitor and read the traffic. This is also called *sniffing* or *snooping*. If the traffic is in plain text, the attacker can read the traffic when the attacker gains access to the path. An example is an attack performed by controlling a router on the data path.

The default recommendation and setting for traffic within Microsoft Lync Server 2013 is to use mutual TLS (MTLS) between trusted servers and TLS from client to server. This protective measure would make an attack very difficult or impossible to achieve within the time period in which a given conversation occurs. TLS authenticates all parties and encrypts all traffic. This does not prevent eavesdropping, but the attacker cannot read the traffic unless the encryption is broken.

The Traversal Using Relay NAT (TURN) protocol does not mandate the traffic to be encrypted and the information that it is sending is protected by message integrity. Although it is open to eavesdropping, the information it is sending (that is, the IP addresses and port) can be extracted directly by simply looking at the source and destination addresses of the packets. The A/V Edge service ensures that the data is valid by checking the Message Integrity of the message by using the key derived from a few items, including a TURN password, which is never sent in clear text. If Secure Real Time Protocol (SRTP) is used, media traffic is also encrypted.

</div>

<div>

## Identity Spoofing (IP Address Spoofing)

*Spoofing* occurs when the attacker determines and uses an IP address of a network, computer, or network component without being authorized to do so. A successful attack allows the attacker to operate as if the attacker is the entity normally identified by the IP address. Within the context of Microsoft Lync Server 2013, this situation comes into play only if an administrator has done both of the following:

  - Configured connections that support only Transmission Control Protocol (TCP) (which is not recommended, because TCP communications are unencrypted).

  - Marked the IP addresses of those connections as trusted hosts.

This is less of a problem for Transport Layer Security (TLS) connections, as TLS authenticates all parties and encrypts all traffic. Using TLS prevents an attacker from performing IP address spoofing on a specific connection (for example, mutual TLS connections). But an attacker could still spoof the address of the DNS server that Lync Server 2013 uses. However, because authentication in Lync is performed with certificates, an attacker would not have a valid certificate required to spoof one of the parties in the communication.

</div>

<div>

## Man-in-the-Middle Attack

A man-in-the-middle attack occurs when an attacker reroutes communication between two users through the attacker’s computer without the knowledge of the two communicating users. The attacker can monitor and read the traffic before sending it on to the intended recipient. Each user in the communication unknowingly sends traffic to and receives traffic from the attacker, all while thinking they are communicating only with the intended user. This can happen if an attacker can modify Active Directory Domain Services to add his or her server as a trusted server or modify Domain Name System (DNS) to get clients to connect through the attacker on their way to the server. A man-in-the-middle attack can also occur with media traffic between two clients. However, in Microsoft Lync Server 2013 point-to-point audio, video, and application sharing, streams are encrypted with SRTP, using cryptographic keys that are negotiated between the peers that are using Session Initiation Protocol (SIP) over TLS. Servers such as Group Chat make use of HTTPS to enhance the security of web traffic.

</div>

<div>

## RTP Replay Attack

A *replay attack* occurs when a valid media transmission between two parties is intercepted and retransmitted for malicious purposes. SRTP used in connection with a secure signaling protocol protects transmissions from replay attacks by enabling the receiver to maintain an index of already received RTP packets and compare each new packet with those already listed in the index.

</div>

<div>

## Spim

*Spim* is unsolicited commercial instant messages or presence subscription requests. While not by itself a compromise of the network, it is annoying in the least, can reduce resource availability and production, and can possibly lead to a compromise of the network. An example of this is users spimming each other by sending requests. Users can block each other to prevent this, but with federation, if a coordinated spim attack is established, this can be difficult to overcome unless you disable federation for the partner.

</div>

<div>

## Viruses and Worms

A *virus* is a unit of code whose purpose is to reproduce additional, similar code units. To work, a virus needs a host, such as a file, email, or program. A *worm* is a unit of code whose purpose is to reproduce additional, similar code units, but it does not need a host. Viruses and worms primarily show up during file transfers between clients or when URLs are sent from other users. If a virus is on your computer, it can, for example, use your identity and send instant messages on your behalf.

</div>

<div>

## Personally Identifiable Information

Microsoft Lync Server 2013 has the potential to disclose information over a public network that might be able to be linked to an individual. The information types can be broken down to two specific categories:

  - **Enhanced presence data ** Enhanced presence data is information that a user can choose to share or not share over a link to a federated partner or with contacts within an organization. This data is not shared with users on a public IM network. Client policies and other client configuration may put some control with the system administrator. In Lync Server 2013, enhanced presence privacy mode can be configured for an individual user to prevent Lync users not on the user’s Contacts list from seeing the user’s presence information. Enhanced presence privacy mode does not prevent users of Microsoft Office Communicator 2007 and Microsoft Office Communicator 2007 R2 from seeing a user’s presence information. For details, see [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md) in the Getting Started documentation and [Configuring enhanced presence privacy mode in Lync Server 2013](lync-server-2013-configuring-enhanced-presence-privacy-mode.md) in the Deployment documentation.

  - **Mandatory data** Mandatory data is required for the proper operation of the server or the client and is NOT under the control of the client or system administration. This is information that is necessary at a server or network level for the purposes of routing, state maintenance, and signaling.

The following tables list the data that is exposed over a public network.

### Enhanced Presence Data

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Data Disclosed</th>
<th>Possible Settings</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Personal Data</p></td>
<td><p>Name, Title, Company, Email Address, Time Zone</p></td>
</tr>
<tr class="even">
<td><p>Telephone Numbers</p></td>
<td><p>Work, Mobile, Home</p></td>
</tr>
<tr class="odd">
<td><p>Calendar Information</p></td>
<td><p>Free/Busy, Out-Of-Town Notice, Meeting Details (to those who have access to your calendar)</p></td>
</tr>
<tr class="even">
<td><p>Presence Status</p></td>
<td><p>Away, Available, Busy, Do Not Disturb, Offline</p></td>
</tr>
</tbody>
</table>


### Mandatory Data

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Data Disclosed</th>
<th>Example Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IP Address</p></td>
<td><p>Actual address of computer or NATed address</p></td>
</tr>
<tr class="even">
<td><p>SIP URI</p></td>
<td><p>jeremylos@litwareinc.com</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

