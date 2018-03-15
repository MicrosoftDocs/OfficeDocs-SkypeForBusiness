---
title: "Configuring Autodiscover in Lync Server 2013 for mobility with hybrid deployments"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f838af79-d8b4-4122-b81c-7889573d143e
description: "Hybrid Deployments are configurations that use both the Skype for Business Online cloud service and the on premises deployment. In this type of configuration, the Autodiscover service must be able to locate where the user is actually located. That is to say, Autodiscover aids in finding the user account and where the server that hosts the user's account is, regardless if it is in the on premises deployment or in the Skype for Business Online deployment."
---

# Configuring Autodiscover in Lync Server 2013 for mobility with hybrid deployments
[]
Hybrid Deployments are configurations that use both the Skype for Business Online cloud service and the on premises deployment. In this type of configuration, the Autodiscover service must be able to locate where the user is actually located. That is to say, Autodiscover aids in finding the user account and where the server that hosts the user's account is, regardless if it is in the on premises deployment or in the Skype for Business Online deployment.
  
For example, if a user's account is hosted on a server in Skype for Business Online, the attempt to locate the user will happen as follows, in a process known as discoverability:
  
- User initiates a connection attempt to the on premises deployment, **contoso.com**.
    
- The attempt is sent to lyncdiscover.contoso.com, the DNS name associated with the Autodiscover service.
    
- Autodiscover refers to the assumed registrar pool at the contoso.com on premises deployment and is given information on the user's actual home server hosted in Skype for Business Online. Autodiscover then sends the user a referral to the **lync.com** online Autodiscover service. 
    
- The user initiates a connection attempt to the lync.com online Autodiscover service and is able to locate the user's account and the user's home server.
    
To enable mobile clients to discover the deployment where the user home server is located, you must configure the Autodiscover service with a new uniform resource locator (URL). Do the following to configure the Autodiscover service.
  
### Configuring Autodiscover for Hybrid Deployments

1. You use Get-CsHostingProvider to retrieve the value of the attribute ProxyFQDN.
    
2. From the Lync Server Management Shell, type
    
  ```
  Set-CsHostingProvider -Identity [identity] -AutodiscoverUrl https://webdir.online.lync.com/autodiscover/autodiscoverservice.svc/root
  ```

    Where [identity] is replaced with the domain name of the shared SIP address space.
    
## See also

#### 

[Get-CsHostingProvider](get-cshostingprovider.md)
  
[Set-CsHostingProvider](set-cshostingprovider.md)

