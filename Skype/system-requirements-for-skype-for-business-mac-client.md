---
title: System Requirements for Skype for Business Mac client
ms.prod: SKYPEFORBUSINESS
ms.assetid: 790d3e89-2b68-411b-b282-38de5d34dd10
---


# System Requirements for Skype for Business Mac client
[]Read this topic to learn about hardware, software, and infrastructure requirements for running Skype for Business on a Mac.
> [!NOTE]
> This article is provided as pre-release information and is subject to change. 
  
    
    


## Hardware and software requirements for Skype for Business on the Mac

The Skype for Business on the Mac client requires Mac OS X El Capitan and higher, and uses at least 100MB of disk space. We support the use of all built-in audio and video devices. External devices must be on the  [list of qualified devices for use with Lync](https://go.microsoft.com/fwlink/p/?LinkId=798223). 
  
    
    

> [!NOTE]
> This list is preliminary and some devices may be qualified for Lync, but not supported on Skype for Business on the Mac. 
  
    
    


## Infrastructure requirements for Skype for Business on the Mac
<a name="Infrastructure"> </a>

The Skype for Business on the Mac client leverages both the Unified Communications Management Platform (UCMP) as well as the Unified Communications Web API (UCWA) that our mobility clients use.
  
    
    
The client has the same requirements as our mobility clients in that you must have an Access Edge Server and Reverse Proxy deployed in a supported configuration. In addition, your account must be enabled for Mobility.
  
    
    

### Authentication

The Skype for Business on the Mac client supports NTLM authentication. Additionally, the client supports Microsoft Modern Authentication and Multi-Factor Authentication when deployed and enabled.
  
    
    

> [!NOTE]
> Due to a current limitation, the user's Exchange credentials must be the same as their Skype for Business credentials. 
  
    
    


### Certificates

Certificates in use on the Access Edge, Reverse Proxy and Front End servers must not use the SHA-512 hash algorithm.
  
    
    
The HTTP Certificate Revocation List must be defined and accessible by the client. For example, we don't support an LDAP entry in the certificate as your Certificate Revocation List.
  
    
    

### DNS

Mobility must be properly deployed for the Skype for Business on the Mac client to function properly. A common failure scenario is to have both of the following DNS entries resolvable on the internal network:
  
    
    
lyncdiscoverinternal.<sipdomain>
  
    
    
lyncdiscover.<sipdomain>
  
    
    
Additionally, the External Web Services FQDN for the Front End pools in your organization must be resolvable on the internal corporate network.
  
    
    
For more information, refer to:  [Deploying Mobility in Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=798224) and the [Microsoft Lync Server 2010 Mobility Guide](https://go.microsoft.com/fwlink//p/?LinkId=798226).
  
    
    

## See also
<a name="Infrastructure"> </a>


#### 


  
    
    
 [Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=798227)
  
    
    
 [Known issues ](https://go.microsoft.com/fwlink/p/?LinkId=798228)
