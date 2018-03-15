---
title: "DNS requirements for automatic client sign-in in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3bcd4bb3-a022-4ffa-b005-1a95ad2b1796
description: "This section explains the Domain Name System (DNS) records that are required for automatic client sign-in. When you deploy your Standard Edition servers or Front End pools, you can configure your clients to use automatic discovery to sign in to the appropriate Standard Edition server or Front End pool. If you plan to require your clients to connect manually to Lync Server 2013, you can skip this topic."
---

# DNS requirements for automatic client sign-in in Lync Server 2013
[]
This section explains the Domain Name System (DNS) records that are required for automatic client sign-in. When you deploy your Standard Edition servers or Front End pools, you can configure your clients to use automatic discovery to sign in to the appropriate Standard Edition server or Front End pool. If you plan to require your clients to connect manually to Lync Server 2013, you can skip this topic.
  
To support automatic client sign-in, you must:
  
- Designate a single server or pool to distribute and authenticate client sign-in requests. This can be an existing server or pool in your organization that hosts users, or you can designate a dedicated server or pool for this purpose that hosts no users. For high availability, we recommend that you designate a Front End pool for this function.
    
- Create an internal DNS SRV record to support automatic client sign-in for this server or pool.
    
    > [!NOTE]
    > In the following record requirements, SIP domain refers to the host portion of the SIP URIs assigned to users. For example, if SIP URIs are of the form \*@contoso.com, contoso.com is the SIP domain. The SIP domain is often different from the internal Active Directory domain. An organization can also support multiple SIP domains. 
  
To enable automatic configuration for your clients, you must create an internal DNS SRV record that maps one of the following records to the fully qualified domain name (FQDN) of the Front End pool or Standard Edition server that distributes sign-in requests from Lync clients:
  
- _sipinternaltls._tcp. _\<domain\>_ - for internal TLS connections 
    
You only need to create a single SRV record for the Front End pool or Standard Edition server or that will distribute sign-in requests.
  
The following table shows some example records required for the fictitious company Contoso, which supports SIP domains of contoso.com and retail.contoso.com.
  
**Example of DNS Records Required for Automatic Client Sign-in with Multiple SIP Domains**

|**FQDN of Front End pool used to distribute sign-in requests**|**SIP domain**|**DNS SRV record**|
|:-----|:-----|:-----|
|pool01.contoso.com  <br/> |contoso.com  <br/> |An SRV record for _sipinternaltls._tcp.contoso.com domain over port 5061 that maps to pool01.contoso.com  <br/> |
|pool01.contoso.com  <br/> |retail.contoso.com  <br/> |An SRV record for _sipinternaltls._tcp.retail.contoso.com domain over port 5061 that maps to pool01.contoso.com  <br/> |
   
> [!NOTE]
> By default, queries for DNS records adhere to strict domain name matching between the domain in the user name and the SRV record. If you prefer that client DNS queries use suffix matching instead, you can configure the DisableStrictDNSNaming Group Policy. For details, see [Planning for clients and devices in Lync Server 2013](planning-for-clients-and-devices-in-lync-server.md) in the Planning documentation. 
  
## Example of the Certificates and DNS Records Required for Automatic Client Sign-In

This example uses the same example names in the preceding table. The Contoso organization supports the SIP domains of contoso.com and retail.contoso.com, and all of its users have a SIP URI in one of the following forms:
  
-  _\<user\>_@retail.contoso.com
    
-  _\<user\>_@contoso.com
    

