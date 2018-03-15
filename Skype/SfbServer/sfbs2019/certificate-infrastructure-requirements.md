---
title: "Certificate infrastructure requirements for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0051aa23-0bbe-4e72-9f29-e01c6bcc6190
description: "Lync Server 2013 requires a public key infrastructure (PKI) to support TLS and mutual TLS (MTLS) connections."
---

# Certificate infrastructure requirements for Lync Server 2013
[]
Lync Server 2013 requires a public key infrastructure (PKI) to support TLS and mutual TLS (MTLS) connections.
  
Lync Server uses certificates for the following purposes:
  
- TLS connections between client and server
    
- MTLS connections between servers
    
- Federation using automatic DNS discovery of partners
    
- Remote user access for instant messaging (IM)
    
- External user access to audio/video (A/V) sessions, application sharing, and conferencing
    
- Mobile requests using automatic discovery of Web Services
    
For Lync Server, the following common requirements apply:
  
- All server certificates must support server authorization (Server EKU).
    
- All server certificates must contain a CRL Distribution Point (CDP).
    
- All certificates must be signed using a signing algorithm supported by the operating system. Lync Server 2013 supports the SHA-1 and SHA-2 suite of digest sizes (224, 256, 384 and 512-bit), and meets or exceeds the operating system requirements. For operating system support, see [https://go.microsoft.com/fwlink/?LinkId=287002](https://go.microsoft.com/fwlink/?LinkId=287002).
    
    > [!NOTE]
    > Using the RSASSA-PSS signature algorithm is unsupported, and may lead to errors on login and call forwarding issues, among other problems. 
  
- Auto-enrollment is supported for internal servers running Lync Server.
    
- Auto-enrollment is not supported for Lync Server Edge Servers.
    
- When you submit a web-based certificate request to a Windows Server 2003 CA, you must submit it from a computer running either Windows Server 2003 with SP2 or Windows XP. 
    
    Note that although KB922706 provides support for resolving issues with enrolling web certificates against a Windows Server 2003 Certificate Services web enrollment, it does not make it possible to use Windows Server 2008, Windows Vista, or Windows 7 to request a certificate from a Windows Server 2003 CA.
    
- Encryption key lengths of 1024, 2048, and 4096 are supported. Key lengths of 2048 and greater are recommended.
    
- The default digest, or hash signing, algorithm is RSA. The ECDH_P256, ECDH_P384, and ECDH_P521 algorithms are also supported. 
    
## In this section

- [Certificate requirements for internal servers in Lync Server 2013](certificate-requirements-for-internal-servers.md)
    
- [Certificate requirements for external user access in Lync Server 2013](certificate-requirements-for-external-user-access.md)
    
- [Certificate requirements for Persistent Chat server in Lync Server 2013](certificate-requirements-for-persistent-chat-server.md)
    
- [Certificate requirements for mobility in Lync Server 2013](certificate-requirements-for-mobility.md)
    

