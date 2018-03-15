---
title: "DNS requirements for a Standard Edition server in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5d1daf54-6e60-4ce0-9254-7d57a0835fa4
description: "This section describes the Domain Name System (DNS) records that are required for deployment of Standard Edition servers."
---

# DNS requirements for a Standard Edition server in Lync Server 2013
[]
This section describes the Domain Name System (DNS) records that are required for deployment of Standard Edition servers.
  
## DNS Records for Standard Edition Servers

The following table specifies DNS requirements for Lync Server 2013 Standard Edition server deployment.
  
|**Deployment scenario**|**DNS requirement**|
|:-----|:-----|
|Standard Edition server  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.  <br/> |
|Automatic client sign-in  <br/> |For each supported SIP domain, an SRV record for _sipinternaltls._tcp.<domain> over port 5061 that maps to the FQDN of the Standard Edition server that authenticates and redirects client requests for sign-in. For details, see [DNS requirements for automatic client sign-in in Lync Server 2013](dns-requirements-for-automatic-client-sign-in.md).  <br/> |
|Device Update Web service discovery by unified communications (UC) devices  <br/> |An internal A record with the name ucupdates-r2.<SIP domain> that resolves to the IP address of the Standard Edition server hosting Device Update Web service. In the situation where a UC device is turned on, but a user has never logged into the device, the A record allows the device to discover the server hosting Device Update Web service and obtain updates. Otherwise, devices obtain the server information though in-band provisioning the first time a user logs in. For details, see [Device Update Web service in Lync Server 2013](device-update-web-service.md) in the Operations documentation.  <br/> |
|A reverse proxy to support HTTP traffic  <br/> |An external A record that resolves the external web farm FQDN to the external IP address of the reverse proxy. Clients and UC devices use this record to connect to the reverse proxy. For details, see [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md) in the Planning documentation.  <br/> |
   
## See also

#### 

[DNS requirements for automatic client sign-in in Lync Server 2013](dns-requirements-for-automatic-client-sign-in.md)
  
[Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md)
#### 

[Device Update Web service in Lync Server 2013](device-update-web-service.md)

