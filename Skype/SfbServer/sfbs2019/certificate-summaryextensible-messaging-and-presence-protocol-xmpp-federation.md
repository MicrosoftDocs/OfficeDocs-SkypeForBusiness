---
title: "Certificate summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b059a34e-99df-40af-91fe-fe2aa52841f6
description: "Certificate requirements for enabling and establishing communications with extensible messaging and presence protocol (XMPP) partners require the additional record of your XMPP domains. The record that is included on the certificate as a subject alternative name (SAN) will be the domain that can participate in XMPP communications. The domain can be the root-level domain (for example, contoso.com) if you want to enable XMPP for your entire domain, or can be selected child domains (for example, corp.contoso.com, finance.contoso.com) if you are enabling XMPP for a subset of users."
---

# Certificate summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013
[]
Certificate requirements for enabling and establishing communications with extensible messaging and presence protocol (XMPP) partners require the additional record of your XMPP domains. The record that is included on the certificate as a subject alternative name (SAN) will be the domain that can participate in XMPP communications. The domain can be the root-level domain (for example, contoso.com) if you want to enable XMPP for your entire domain, or can be selected child domains (for example, corp.contoso.com, finance.contoso.com) if you are enabling XMPP for a subset of users. 
  
## Certificate Summary for Extensible Messaging and Presence Protocol

|**Component**|**Subject name**|**Subject alternative names (SAN)/Order**|**Comments**|
|:-----|:-----|:-----|:-----|
|Assign to Access Edge service of Edge Server or Edge pool  <br/> |sip.contoso.com  <br/> |webcon.contoso.com  <br/> sip.contoso.com  <br/> sip.fabrikam.com  <br/> contoso.com  <br/> |The first three SAN entries are the normal SAN entries for a full Edge Server. The contoso.com is the entry required for federation with the XMPP partner at the root domain level. This entry will allow XMPP for all domains with the suffix contoso.com.  <br/> |
   
## See also

#### 

[Example XMPP configuration in Lync Server 2013 - XMPP federation with Google Talk](example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)
#### 

[Plan for Edge Server certificates in Lync Server 2013](plan-for-edge-server-certificates.md)
#### 

[Set up Edge certificates for Lync Server 2013](set-up-edge-certificates.md)
  
[Request-CsCertificate](request-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

