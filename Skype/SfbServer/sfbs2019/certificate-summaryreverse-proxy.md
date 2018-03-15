---
title: "Certificate summary - Reverse proxy in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f2b9a53f-aead-413d-81e9-4a294a010fbb
description: "Certificate requirements for the reverse proxy are much simpler than that for the Edge Servers. The provided flowchart presents the requirements necessary. The accompanying table presents typical certificate subject name and subject alternative names in relation to the scenarios that we have been reviewed in the Edge Server discussions. For more details on the Edge Server scenarios, see Scenarios for external user access in Lync Server 2013."
---

# Certificate summary - Reverse proxy in Lync Server 2013
[]
Certificate requirements for the reverse proxy are much simpler than that for the Edge Servers. The provided flowchart presents the requirements necessary. The accompanying table presents typical certificate subject name and subject alternative names in relation to the scenarios that we have been reviewed in the Edge Server discussions. For more details on the Edge Server scenarios, see [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md).
  
**Certificates Flow Chart for Reverse Proxy**

![Certificates Flow Chart for Edge Server](media/Plan_LyncServer_Edge_Scenario_ReverseProxyCertificateFlowchart.jpg)
  
**Reverse Proxy: External Interface**

|**Component**|**Subject name**|**Subject alternative name (SAN)/Order**|**Comments**|
|:-----|:-----|:-----|:-----|
|Reverse Proxy  <br/> |webext.contoso.com  <br/> |webext.contoso.com  <br/> webdirext.contoso.com  <br/> dialin.contoso.com  <br/> meet.contoso.com  <br/> officewebapps01.contoso.com  <br/> lyncdiscover.contoso.com  <br/> (Optional):\*.contoso.com  <br/> | Certificate must be issued by a public CA and with the server EKU. Services include Address Book Service, distribution group expansion Office Web Apps for conferencing, and Lync IP Device publishing rules. Subject alternative name includes:  <br/>  External Web Services FQDN for Front End Server or Front End pool  <br/>  External Web Services FQDN for Director or Director pool  <br/>  Dial-in conferencing  <br/>  Online meeting publishing rule  <br/>  Office Web Apps for conferencing  <br/>  Lyncdiscover (Autodiscover)  <br/>  The optional wildcard replaces both meet and dialin SAN  <br/> |
   

