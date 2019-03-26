---
title: "Encryption for Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d18c74a6-385b-407b-98eb-0d525fa38fea
description: "Skype for Business Server uses TLS and MTLS to encrypt instant messages. All server-to-server traffic requires MTLS, regardless of whether the traffic is confined to the internal network or crosses the internal network perimeter. When connecting Skype for Business Server to 3rd party IPPBX systems or SIP trunks TLS is optional but strongly recommended between the Mediation Server and media gateway. If TLS is configured on this link, MTLS is required. Therefore, the gateway must be configured with a certificate from a CA that is trusted by the Mediation Server."
---

# Encryption for Skype for Business Server
 
Skype for Business Server uses TLS and MTLS to encrypt instant messages. All server-to-server traffic requires MTLS, regardless of whether the traffic is confined to the internal network or crosses the internal network perimeter. When connecting Skype for Business Server to third-party IPPBX systems or SIP trunks TLS is optional but strongly recommended between the Mediation Server and media gateway. If TLS is configured on this link, MTLS is required. Therefore, the gateway must be configured with a certificate from a CA that is trusted by the Mediation Server.
  
> [!NOTE]
> A security advisory regarding SSL 3.0 was published in 2014. Disabling SSL 3.0 in Skype for Business Server 2015 is a supported option. To learn more about the security advisory, see [Disabling SSL 3.0 in Lync Server 2013 and Skype for Business Server 2015](https://blogs.technet.microsoft.com/uclobby/2014/10/22/disabling-ssl-3-0-in-lync-server-2013/).<br/>
**Security note:** To ensure the strongest cryptographic protocol is used, Skype for Business Server 2015 will offer TLS encryption protocols in the following order to clients: **TLS 1.2 , TLS 1.1, TLS 1.0**. TLS is a critical aspect of Skype for Business Server 2015 and thus it is required in order to maintain a supported environment.<br/>
**Security note:** To ensure the strongest cryptographic protocol is used, Skype for Business Server 2019 will offer TLS encryption protocols in the following order to clients: **TLS 1.3, TLS 1.2**. TLS is a critical aspect of Skype for Business Server 2019 and thus it is required in order to maintain a supported environment. 
  
The following table summarizes the protocol requirements for each type of traffic. 
  
**Traffic Protection**

|**Traffic type**|**Protected by**|
|:-----|:-----|
|Server-to-server  <br/> |MTLS  <br/> |
|Client-to-server  <br/> |TLS  <br/> |
|Instant messaging and presence  <br/> |TLS  <br/> |
|Audio and video and desktop sharing of media  <br/> |SRTP  <br/> |
|Desktop sharing (signaling)  <br/> |TLS  <br/> |
|Web conferencing  <br/> |TLS  <br/> |
|Meeting content download, address book download, distribution group expansion  <br/> |HTTPS  <br/> |
   
## Media Encryption

Media traffic is encrypted using Secure RTP (SRTP), a profile of Real-Time Transport Protocol (RTP) that provides confidentiality, authentication, and replay attack protection to RTP traffic. In addition, media flowing in both directions between the Mediation Server and its internal next hop is also encrypted using SRTP. Media flowing in both directions between the Mediation Server and a media gateway is optionally encrypted and recommended. The Mediation Server can support encryption to the media gateway, but the gateway must support MTLS and storage of a certificate.
  
> [!NOTE]
> For more information about setting up hybrid, see [Plan hybrid connectivity](../../../SfbHybrid/hybrid/plan-hybrid-connectivity.md?toc=/SkypeForBusiness/sfbhybridtoc/toc.json).
  
## FIPS

Skype for Business Server and Microsoft Exchange Server 2016 operate with support for Federal Information Processing Standard (FIPS) 140-2 algorithms if the Windows Server operating systems are configured to use the FIPS 140-2 algorithms for system cryptography. To implement FIPS support, you must configure each server running Skype for Business Server to support it.
  

