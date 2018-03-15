---
title: "DNS requirements for Standard Edition servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d6bbe65-e7ce-491b-a0bd-d2f7197f240d
description: "This section describes the Domain Name System (DNS) records that are required for deployment of Standard Edition servers."
---

# DNS requirements for Standard Edition servers in Lync Server 2013
[]
This section describes the Domain Name System (DNS) records that are required for deployment of Standard Edition servers.
  
## DNS Records for Standard Edition Servers

The following table specifies DNS requirements for Lync Server 2013 Standard Edition server deployment.
  
**DNS Requirements for a Standard Edition Server**

|**Deployment scenario**|**DNS requirement**|
|:-----|:-----|
|Standard Edition server  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.  <br/> |
|Automatic client sign-in  <br/> |For each supported SIP domain, an SRV record for _sipinternaltls._tcp. _\<domain\>_ over port 5061 that maps to the FQDN of the Standard Edition server that authenticates and redirects client requests for sign-in. For details, see [DNS requirements for automatic client sign-in in Lync Server 2013](dns-requirements-for-automatic-client-sign-in.md).  <br/> |
|Device Update Web service discovery by unified communications (UC) devices  <br/> |An internal A record with the name ucupdates-r2. _\<SIP domain\>_ that resolves to the IP address of the Standard Edition server hosting Device Update Web service. In the situation where a UC device is turned on, but a user has never logged into the device, the A record allows the device to discover the server hosting Device Update Web service and obtain updates. Otherwise, devices obtain the server information though in-band provisioning the first time a user logs in.  <br/> |
|A reverse proxy to support HTTP traffic  <br/> |An external A record that resolves the external web farm FQDN to the external IP address of the reverse proxy. Clients and UC devices use this record to connect to the reverse proxy. For details, see [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md) in the Planning documentation.  <br/> |
   

