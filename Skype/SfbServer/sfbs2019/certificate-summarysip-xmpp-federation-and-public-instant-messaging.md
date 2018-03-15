---
title: "Certificate summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 933d6351-cfa6-4432-b3ed-1aff3ac92065

description: "The certificates that you need for federating with Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server will typically be met by the certificates that you configure, request and assign to your Edge Server."
---

# Certificate summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013
[]
The certificates that you need for federating with Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server will typically be met by the certificates that you configure, request and assign to your Edge Server. 
  
Certificate requirements for enabling and establishing communications with extensible messaging and presence protocol (XMPP) partners require addition of entries for your XMPP domains. The record that is included on the certificate as a subject alternative name (SAN) will be the domain that can participate in XMPP communications. The domain can be the root-level domain (for example, contoso.com) if you want to enable XMPP for your entire domain, or can be selected child domains (for example, corp.contoso.com, finance.contoso.com) if you are enabling XMPP for a subset of users. 
  
To configure certificates for public Instant Messaging connectivity, note that there is nothing different from other SIP federation types or even standard Edge Server certificates, except that America Online (AOL) requires a the certificate or certificates (in the case of an Edge pool) to also contain the client EKU. The client EKU is an addition to the certificate, and is part of the external public certificate that is assigned to your Edge Server.
  
To confirm that you have met the correct certificate requirements for your Edge Server deployment, review the topics listed in the section titled **See Also**.
  
## 

|**Component**|**Subject name**|**Subject alternative names (SAN)**|**Comments**|
|:-----|:-----|:-----|:-----|
|External/Access Edge  <br/> |sip.contoso.com  <br/> |sip.contoso.com  <br/> webcon.contoso.com  <br/> contoso.com  <br/> > [!NOTE]> To support the contoso.com XMPP namespace           sip.fabrikam.com  <br/> > [!NOTE]> To support the fabrikam.com SIP namespace           fabrikam.com  <br/> > [!NOTE]> To support the fabrikam.com XMPP namespace           
| The certificate must be from a Public CA, and must have the server EKU and client EKU if public IM connectivity with AOL is to be deployed. The certificate is assigned to the external Edge Server interfaces for:  <br/>  Access Edge service  <br/>  Web Conferencing Edge service  <br/>  A/V Edge service  <br/> > [!NOTE]>  Technically, a certificate is not assigned to the A/V Edge. Secure communication and authentication is managed by way of the Media Relay Authentication Service (MRAS). MRAS uses the certificate assigned to the Edge Server internal interface.            Note that SANs are automatically added to the certificate based on your definitions in Topology Builder. You add SAN entries as needed for additional SIP domains and other entries that you need to support. The subject name is replicated in the SAN and must be present for correct operation.  <br/> |
   
## See also

#### 

[Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk](example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)
#### 

[Plan for Edge Server certificates in Lync Server 2013](plan-for-edge-server-certificates.md)
  
[Certificate summary - Single consolidated edge with private IP addresses using NAT in Lync Server 2013](certificate-summarysingle-consolidated-edge-with-private-ip-addresses-using-nat.md)
  
[Certificate summary - Single consolidated edge with public IP addresses in Lync Server 2013](certificate-summarysingle-consolidated-edge-with-public-ip-addresses.md)
  
[Certificate summary - Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013](certificate-summaryscaled-consolidated-edge-dns-load-balancing-with-private-ip-a.md)
  
[Certificate summary - Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013](certificate-summaryscaled-consolidated-edge-dns-load-balancing-with-public-ip-ad.md)
  
[Certificate summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013](certificate-summaryscaled-consolidated-edge-with-hardware-load-balancers.md)

