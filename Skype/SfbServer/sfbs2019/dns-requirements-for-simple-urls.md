---
title: "DNS requirements for simple URLs in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3a3c9b22-892f-45a7-b05c-539d358a1a86
description: "In this articleSimple URL Option 1Simple URL Option 2Simple URL Option 3Disaster Recovery Option for Simple URLs"
---

# DNS requirements for simple URLs in Lync Server 2013
[]
 **In this article**
  
[Simple URL Option 1](#sectionSection0)
  
[Simple URL Option 2](#sectionSection1)
  
[Simple URL Option 3](#sectionSection2)
  
[Disaster Recovery Option for Simple URLs](#sectionSection3)
  
Lync Server 2013 supports simple URLs, which make joining meetings easier for your users, and make getting to Lync Server administrative tools easier for your administrators. For details about simple URLs, see [Planning for simple URLs in Lync Server 2013](planning-for-simple-urls.md). 
  
Lync Server supports the following three simple URLs: Meet, Dial-In, and Admin. You are required to set up simple URLs for Meet and Dial-In, and the Admin simple URL is optional. The Domain Name System (DNS) records that you need to support simple URLs depend on how you have defined these simple URLs, and whether you want to support disaster recovery for Simple URLs. 
  
## Simple URL Option 1
<a name="sectionSection0"> </a>

In Option 1, you create a new base URL for each simple URL.
  
> [!NOTE]
> When a user clicks a simple URL meeting link, the server that the DNS A record resolves to determines the correct client software to start. After the client software is started, it automatically communicates with the pool where the conference is hosted. This way, users are directed to the appropriate server for meeting content no matter which server or pool the simple URL DNS A records resolve to. 
  
**Simple URL Option 1**

|||
|:-----|:-----|
|**Simple URL** <br/> |**Example** <br/> |
|Meet  <br/> |https://meet.contoso.com, https://meet.fabrikam.com, and so on (one for each SIP domain in your organization)  <br/> |
|Dial-in  <br/> |https://dialin.contoso.com  <br/> |
|Admin  <br/> |https://admin.contoso.com  <br/> |
   
If you use Option 1, you must define the following:
  
- For each Meet simple URL, you need a DNS A record that resolves the URL to the IP address of the Director, if you have one deployed. Otherwise, it should resolve to the IP address of the load balancer of a Front End pool. If you have not deployed a pool and are using a Standard Edition server deployment, the DNS A record must resolve to the IP address of one Standard Edition server in your organization.
    
    If you have more than one SIP domain in your organization and you use this option, you must create Meet simple URLs for each SIP domain and you need a DNS A record for each Meet simple URL. For example, if you have both contoso.com and fabrikam.com, you will create DNS A records for both https://meet.contoso.com and https://meet.fabrikam.com.
    
    Alternatively, if you have multiple SIP domains and you want to minimize the DNS record and certificate requirements for these simple URLs, use Option 3 as described later in this topic.
    
- For the Dial-in simple URL, you need a DNS A record that resolves the URL to the IP address of the Director, if you have one deployed. Otherwise, it should resolve to the IP address of the load balancer of a Front End pool. If you have not deployed a pool and are using a Standard Edition server deployment, the DNS A record must resolve to the IP address of one Standard Edition server in your organization.
    
- The Admin simple URL is internal only. It requires a DNS A record that resolves the URL to the IP address of the Director, if you have one deployed. Otherwise, it should resolve to the IP address of the load balancer of a Front End pool. If you have not deployed a pool and are using a Standard Edition server deployment, the DNS A record must resolve to the IP address of one Standard Edition server in your organization.
    
## Simple URL Option 2
<a name="sectionSection1"> </a>

With Option 2, the Meet, Dial-in, and Admin simple URLs all have a common base URL, such as lync.contoso.com. Therefore, you need only one DNS A record for these simple URLs, which resolves lync.contoso.com to the IP address of a Director pool or Front End pool. If you have not deployed a pool and are using a Standard Edition server deployment, the DNS A record must resolve to the IP address of one Standard Edition server in your organization.
  
Note that if you have more than one SIP domain in your organization, you must still create Meet simple URLs for each SIP domain and you need a DNS A record for each Meet simple URL. In this example, while three simple URLs are all based on lync.contoso.com, an additional Meet simple URL for fabrikam.com is set up with a different base URL. In this example, you must create DNS A records for both https://lync.contoso.com and https://lync.fabrikam.com. Simple URL Option 3 shows another way to handle naming and DNS A records if you have multiple SIP domains.
  
**Simple URL Option 2**

|||
|:-----|:-----|
|**Simple URL** <br/> |**Example** <br/> |
|Meet  <br/> |https://lync.contoso.com/Meet, https://lync.fabrikam.com/Meet, and so on (one for each SIP domain in your organization)  <br/> |
|Dial-in  <br/> |https://lync.contoso.com/Dialin  <br/> |
|Admin  <br/> |https://lync.contoso.com/Admin  <br/> |
   
## Simple URL Option 3
<a name="sectionSection2"> </a>

Option 3 is most useful if you have many SIP domains, and you want them to have separate simple URLs but want to minimize the DNS record and certificate requirements for these simple URLs. In this example, you need only one DNS A record, which resolves lync.contoso.com to the IP address of a Director pool or Front End pool. 
  
**Simple URL Option 3**

|||
|:-----|:-----|
|**Simple URL** <br/> |**Example** <br/> |
|Meet  <br/> |https://lync.contoso.com/contosoSIPdomain/Meet  <br/> https://lync.contoso.com/fabrikamSIPdomain/Meet  <br/> |
|Dial-in  <br/> |https://lync.contoso.com/contosoSIPdomain/Dialin  <br/> |
|Admin  <br/> |https://lync.contoso.com/contosoSIPdomain/Admin  <br/> |
   
## Disaster Recovery Option for Simple URLs
<a name="sectionSection3"> </a>

If you have multiple sites that contain Front End pools and your DNS provider supports GeoDNS, you can set up your DNS records for Simple URLs to support disaster recovery, so that Simple URL functionality continues even if one entire Front End pool goes down. This disaster recovery feature supports the Meet and Dial-In simple URLs.
  
To configure this, create two GeoDNS addresses. Each address has two DNS A or CNAME records that resolve to two pools which are paired together for disaster recovery purposes. One GeoDNS address is used for internal access, and resolves to the internal web FQDN or load balancer IP address for the two pools. The other GeoDNS address is used for external access and resolves to the external web FQDN or load balancer IP address for the two pools. The following is an example for the Meet simple URL, using the FQDNs for the pools. 
  
```
Meet-int.geolb.contoso.com
     Pool1InternalWebFQDN.contoso.com
     Pool2InternalWebFQDN.contoso.com
```

```
Meet-ext.geolb.contoso.com
     Pool1ExternalWebFQDN.contoso.com
     Pool2ExternalWebFQDN.contoso.com
```

Then create CNAME records that resolve your Meet simple URL (such as meet.contoso.com) to the two GeoDNS addresses.
  
> [!NOTE]
> If your network uses hairpinning (routing all your Simple URL traffic through the external link, including traffic that comes from within your organization), then you can just configure the external GeoDNS address and resolve your Meet simple URL to only that external address. 
  
When you use this method, you can configure each GeoDNS address to use either a round robin method to distribute requests to the two pools, or to connect primarily to one pool (such as the pool located geographically closer) and use the other pool only in case of connectivity failure. 
  
You can set up the same configuration for the Dial-In simple URL. To do so, create additional records like those in the previous example, substituting  `dialin` for  `meet` in the DNS records. For the Admin simple URL, use one of the three options listed earlier in this section. 
  
Once this configuration is set up, you must use a monitoring application to set up HTTP monitoring to watch for failures. For external access, monitor to make sure that HTTPS GET autodiscovery requests to the the external web FQDN or load balancer IP address for the two pools are successful. For example, the following requests must not contain any **ACCEPT** header and must return **200 OK**. 
  
```
HTTPS GET Pool1ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root
HTTPS GET Pool2ExternalWebFQDN.contoso.com/autodiscover/autodiscoverservice.svc/root

```

For internal access, you must monitor port 5061 on the internal web FQDN or load balancer IP address for the two pools. If any connectivity failures are detected, the VIP for these pools must close ports 80, 443 and 444.
  

