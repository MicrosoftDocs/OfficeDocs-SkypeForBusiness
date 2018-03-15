---
title: "Request certificates in advance (optional) for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9d6d7de6-ff2a-46da-b1b7-a354c8e383e4
description: "Certificates are required for all internal servers that are running Lync Server 2013, including each Enterprise Edition Front End Server, Standard Edition server, Director, Edge Server and stand-alone Mediation Server. Although an internal enterprise certification authority (CA) is recommended for internal servers, you can also use a public CA. For details about certificate requirements and about the use of a public CA, see Certificate requirements for internal servers in Lync Server 2013 in the Planning documentation."
---

# Request certificates in advance (optional) for Lync Server 2013
[]
Certificates are required for all internal servers that are running Lync Server 2013, including each Enterprise Edition Front End Server, Standard Edition server, Director, Edge Server and stand-alone Mediation Server. Although an internal enterprise certification authority (CA) is recommended for internal servers, you can also use a public CA. For details about certificate requirements and about the use of a public CA, see [Certificate requirements for internal servers in Lync Server 2013](certificate-requirements-for-internal-servers.md) in the Planning documentation. 
  
Lync Server 2013 setup includes the Certificate Wizard, which facilitates the tasks of requesting, assigning, and installing certificates during deployment. If you want to request certificates prior to installing servers (for instance, to save time during actual deployment of servers), you can do so by using a computer on which the Lync Server 2013 administrative tools are installed or by using a certificate request procedure defined in your organization, as long as you make sure that the certificates are exportable and contain all the required subject alternative names. Requesting certificates in advance is optional. If you do not request them in advance, you must request them as part of the setup of each server that requires a certificate.
  
This Deployment documentation provides procedures for using the Certificate Wizard to request certificates as part of the setup process, as described in the [Configure certificates for servers in Lync Server 2013](configure-certificates-for-servers.md), [Configure certificates for the Director in Lync Server 2013](configure-certificates-for-the-director.md), and [Install the files for Mediation Server in Lync Server 2013](install-the-files-for-mediation-server.md) sections of this Deployment documentation. If you request certificates in advance, you must modify the certificate deployment procedures in those sections as appropriate to importing and assigning the certificates instead of requesting them at the time of deployment. 
  
> [!NOTE]
> Lync Server 2013 includes support for SHA-256 certificates for connections from clients running the Windows Vista, Windows Server 2008, Windows Server 2008 R2, and Windows 7 operating systems, and Lync Phone Edition. To support external access using SHA-256, the external certificate is issued by a public CA using SHA-256. 
  

