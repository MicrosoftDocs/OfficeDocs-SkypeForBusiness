---
title: "Certificate requirements for mobility in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bb0e97af-cf60-4271-a0ab-654429d884ea
description: "If you deploy the mobility feature and support automatic discovery for mobile clients, you need to include certain subject alternative name entries on certificates to support secure connections from the mobile clients."
---

# Certificate requirements for mobility in Lync Server 2013
[]
If you deploy the mobility feature and support automatic discovery for mobile clients, you need to include certain subject alternative name entries on certificates to support secure connections from the mobile clients. 
  
You need to include subject alternative name entries for automatic discovery on the following certificates:
  
- Director pool 
    
- Front End pool
    
- Reverse proxy
    
This section describes the subject alternative name entries that are required on your certificates for automatic discovery.
  
> [!NOTE]
>  Reissuing certificates by using an internal certificate authority is typically a simple process, but adding multiple subject alternative name entries to public certificates used by the reverse proxy can be expensive. If you have many SIP domains, making the addition of subject alternative names very expensive, you can configure the reverse proxy to use HTTP for the initial Autodiscover Service request, instead of using HTTPS (the default configuration). For details, see [Technical requirements for mobility in Lync Server 2013](technical-requirements-for-mobility.md). 
  
**Director Pool Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|Internal Autodiscover Service URL  <br/> |SAN=lyncdiscoverinternal.\<sipdomain\>  <br/> |
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover.\<sipdomain\>  <br/> |
   
> [!NOTE]
> Alternatively, you can use SAN=\*.\<sipdomain\> 
  
**Front End Pool Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|Internal Autodiscover Service URL  <br/> |SAN=lyncdiscoverinternal.\<sipdomain\>  <br/> |
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover.\<sipdomain\>  <br/> |
   
> [!NOTE]
> Alternatively, you can use SAN=\*.\<sipdomain\> 
  
**Reverse Proxy (Public CA) Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover.\<sipdomain\>  <br/> |
   
> [!NOTE]
> You assign this SAN to the certificate assigned to the SSL Listener on the reverse proxy. 
  
> [!NOTE]
> Your reverse proxy listener will have subject alternative names for your external Web Services URL(s) (for example, SAN=lyncwebextpool01.contoso.com, and dirwebexternal.contoso.com if you have deployed the optional Director). 
  

