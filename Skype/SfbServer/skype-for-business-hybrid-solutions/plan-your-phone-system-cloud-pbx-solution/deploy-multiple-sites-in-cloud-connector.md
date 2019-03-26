---
title: "Deploy multiple sites in Cloud Connector"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: e62413fd-f68e-4825-8384-c983076bdf23
description: "Learn about deploying multiple PSTN sites in Cloud Connector Edition."
---

# Deploy multiple sites in Cloud Connector
 
Learn about deploying multiple PSTN sites in Cloud Connector Edition.
  
This section describes how to deploy multiple Public Switched Telephone Network (PSTN) sites. Sites are deployed one at a time using the same steps as deploying a single site. This topic describes the considerations for and differences between sites in a multiple site deployment. 
  
## Multiple Public Switched Telephone Network (PSTN) Sites

The following shows an example configuration to deploy Skype for Business Cloud Connector Edition for different PSTN sites. Make sure your configuration settings are correct before you start a deployment.
  
PSTN Site 1
  
```
[Common]
SiteName=Site1
[EdgeServer]
InternalMachineName= cc-edge1
InternalPoolName=cc-edgepool
InternalMachineIPs=192.168.0.241

ExternalSIPPoolName=access1
ExternalSIPIPs=192.168.1.4

ExternalMRFQDNPoolName=mr1
ExternalMRIPs=192.168.1.4
ExternalMRPublicIPs=23.99.115.35
```

PSTN Site 2
  
```
[Common]
SiteName=Site2
[EdgeServer]
InternalMachineName= cc-edge2
InternalPoolName=cc-edgepool
InternalMachineIPs=192.168.0.242

ExternalSIPPoolName=access2
ExternalSIPIPs=192.168.1.5

ExternalMRFQDNPoolName=mr2
ExternalMRIPs=192.168.1.5
ExternalMRPublicIPs=104.42.226.134
```

For each PSTN site that you want to add, follow the steps in [Deploy a single site in Cloud Connector](deploy-a-single-site-in-cloud-connector.md).
  
> [!IMPORTANT]
> The shared folder for preparing High Availability (HA) is per PSTN site. The shared folder **must** be different between PSTN sites. Do not use the same shared folder for multiple sites.> 
  
## Single site with High Availability (HA) compared to multi-site deployments
<a name="BKMK_SingleSitecomparedtomulti-site"> </a>

The following table lists the differences between single site with HA support and a multiple site deployment.
  
|**Category**|**Item**|**Single-Site with HA**|**Multi-Site**|
|:-----|:-----|:-----|:-----|
|Configure  <br/> |Appliance Host Name <br/> |**Different** across appliances <br/> |**Different** across PSTN sites <br/> |
|Setup  <br/> |Shared folder  <br/> |Requires the **same** shared folder across appliances <br/> |Requires a **different** shared folder across appliances <br/> |
|Configure  <br/> |VirtualMachineDomain  <br/> |Requires the **same** domain across appliances <br/> |Requires the **same** domain across PSTN sites <br/> |
|Configure  <br/> |SIPDomains  <br/> |Domain names and order should be the **same** across appliances <br/> |Domain names and order should be the **same** across PSTN sites <br/> |
|Configure  <br/> |Site name  <br/> |**Same** Site Name across appliances <br/> |**Different** Site Name across PSTN sites <br/> |
|Configure  <br/> |Server names  <br/> |**Different** across appliances <br/> |**Different** across PSTN sites <br/> |
|Configure  <br/> |Internal pool FQDNs  <br/> |**Same** across appliances <br/> |**Same** across PSTN sites <br/> |
|Configure  <br/> |Internal IPs  <br/> |**Different** across appliances <br/> |**Different** across PSTN sites <br/> |
|Configure  <br/> |External FQDN  <br/> |**Same** across appliances <br/> |**Different** across PSTN sites <br/> |
|Configure  <br/> |External IPs  <br/> |**Different** across appliances <br/> |**Different** across PSTN sites <br/> |
|Configure  <br/> |PSTN GW settings  <br/> |**Same** across appliances <br/> |**Different** across PSTN sites <br/> |
|Configure  <br/> |DNS record  <br/> |Add records with the **same** External Access FQDNs and **different** IP addresses <br/> |Add records with **different** External Access FQDNs and **different** IP addresses <br/> |
|Setup  <br/> |Hybrid tenant  <br/> |Set HybridPSTNSite  <br/> Set PeerDestination for fallback  <br/> |Set HybridPSTNSite  <br/> Set PeerDestination for fallback  <br/> |
|Setup  <br/> |Gateway  <br/> |MS GW **M:N** mapping in this site <br/> |PSTN gateway(s) in each PSTN site should only connect to the Mediation Server(s) in the same site  <br/> |
|Setup  <br/> |User  <br/> |Set UserPSTNSettings  <br/> |Set UserPSTNSettings  <br/> |
   

