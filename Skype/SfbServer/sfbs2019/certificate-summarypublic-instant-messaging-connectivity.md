---
title: "Certificate summary - Public instant messaging connectivity in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2b3687ee-50c2-4c1c-880e-8dcf8bd4f309
description: "To configure certificates for public Instant Messaging connectivity, you should first notice that there is nothing different from other SIP federation types or even standard Edge Server certificates, except that America Online (AOL) requires a unique certificate configuration. In addition to the usual server enhanced key usage (EKU), America Online requires the certificate or certificates (in the case of an Edge pool) to also contain the client EKU. The client EKU is an addition to the certificate, and is part of the external public certificate that is assigned to your Edge Server."
---

# Certificate summary - Public instant messaging connectivity in Lync Server 2013
[]
To configure certificates for public Instant Messaging connectivity, you should first notice that there is nothing different from other SIP federation types or even standard Edge Server certificates, except that America Online (AOL) requires a unique certificate configuration. In addition to the usual server enhanced key usage (EKU), America Online requires the certificate or certificates (in the case of an Edge pool) to also contain the client EKU. The client EKU is an addition to the certificate, and is part of the external public certificate that is assigned to your Edge Server.
  
## Certificate Summary - Public Instant Messaging Connectivity

|**Component**|**Subject name**|**Subject alternative names (SAN)/Order**|**Comments**|
|:-----|:-----|:-----|:-----|
|External/Access Edge  <br/> |sip.contoso.com  <br/> |sip.contoso.com  <br/> webcon.contoso.com  <br/> sip.fabrikam.com  <br/> | The certificate must be from a Public CA, and must have the server EKU and client EKU if public IM connectivity with AOL is to be deployed. The certificate is assigned to the external Edge Server interfaces for:  <br/>  Access Edge service  <br/>  Web Conferencing Edge service  <br/>  A/V Edge service  <br/>  Note that SANs are automatically added to the certificate based on your definitions in Topology Builder. You add SAN entries as needed for additional SIP domains and other entries that you need to support. The subject name is replicated in the SAN and must be present for correct operation.  <br/> |
   
## See also

#### 

[Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)

