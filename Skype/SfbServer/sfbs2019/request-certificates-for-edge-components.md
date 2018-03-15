---
title: "Request certificates for edge components in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8c72b877-febc-428f-89dc-389e7a7ac849
description: "The certificates required to support external user access include certificates issued by a public certification authority (CA), and certificates issued by an internal Enterprise CA:"
---

# Request certificates for edge components in Lync Server 2013
[]
The certificates required to support external user access include certificates issued by a public certification authority (CA), and certificates issued by an internal Enterprise CA: 
  
- Certificates required for the external interface of Edge Server and the reverse proxy must be issued by a public CA.
    
- Certificates required for the internal interface can be issued by either a public CA or an internal enterprise CA. We recommend using an internal Windows Server 2008 CA, Windows Server 2008 R2 CA, Windows Server 2012 CA, or Windows Server 2012 R2 CA for creating these certificates to save on the expense of using public certificates. 
    
> [!IMPORTANT]
> It can take time to process certificate requests, especially requests to public CAs, so you should request certificates for your Edge Servers early enough to ensure that they are available when you start deployment of your Edge Server components. For a summary of certificate requirements for Edge Servers, see [Certificate requirements for external user access in Lync Server 2013](certificate-requirements-for-external-user-access.md). 
  
Although you can choose to use a public CA for the internal edge certificate, we recommend that you use an internal enterprise CA for those other certificates instead to minimize the cost of certificates. For a summary of certificate requirements for Edge Servers, see [Certificate requirements for external user access in Lync Server 2013](certificate-requirements-for-external-user-access.md). 
  
> [!NOTE]
> When you install an Edge Server, setup includes a certificate wizard that facilitates the tasks of requesting, assigning, and installing certificates, as described in the [Set up Edge certificates for Lync Server 2013](set-up-edge-certificates.md) section. If you want to request certificates prior to installing an Edge Server (such as to save time during actual deployment of Edge Server components), you can do so using internal servers as long as you ensure that the certificates are exportable and contain all of the required subject alternative names. This documentation does not provide procedures for using internal servers to request certificates. 
  
## Request certificates from a public CA

Your Edge Server deployment requires a single public certificate for the external interfaces of Edge Servers, which is used for the Access Edge service, the Web Conferencing Edge service, and for A/V authentication service. This certificate must have an exportable private key to ensure that the A/V authentication service uses the same keys on all Edge Servers in a pool. The reverse proxy, which is used with Microsoft Internet Security and Acceleration (ISA) Server 2006 or Microsoft Forefront Threat Management Gateway 2010, also requires a public certificate. 
  
## Request certificates from an internal Enterprise CA

The certificates required for the internal edge interface can be issued by either a public certification authority (CA) or an internal CA. You can use an internal enterprise CA to help minimize the cost of certificates. If your organization has an internal CA deployed, the certificates for the internal edge should be issued by the internal CA. Using an internal enterprise CA for internal certificates can reduce the cost of certificates.
  
For a summary of certificate requirements for edge components, see [Certificate requirements for external user access in Lync Server 2013](certificate-requirements-for-external-user-access.md). For details about using a public CA to obtain certificates, see [Request certificates for edge components in Lync Server 2013](request-certificates-for-edge-components.md). For details about requesting, installing, and assigning certificates, see [Set up Edge certificates for Lync Server 2013](set-up-edge-certificates.md).
  

