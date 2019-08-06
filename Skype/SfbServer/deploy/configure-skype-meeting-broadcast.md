---
title: "Configure your on-premises deployment for Skype Meeting Broadcast"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- IT_Skype16
- IT_Skype4B_Hybrid
ms.assetid: 2979802e-fc6b-4555-bc43-7cd48f6a1d88
description: "Summary: Learn about the steps you need to perform to configure Skype Meeting Broadcast for your on-premises Skype for Business Server hybrid deployment."
---

# Configure your on-premises deployment for Skype Meeting Broadcast
 
**Summary:** Learn about the steps you need to perform to configure Skype Meeting Broadcast for your on-premises Skype for Business Server hybrid deployment.
  
Skype Meeting Broadcast is an online service that is part of Office 365. If you are running Skype for Business Server on-premises and want to use Skype Meeting Broadcast in your environment, you'll need to follow the configuration steps in this topic. Before you begin, your environment needs to be configured for hybrid with Skype for Business Online. For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md?toc=/SkypeForBusiness/sfbhybridtoc/toc.json) and [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](../skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity.md).
  
## Configure your hybrid environment for Skype Meeting Broadcast

You'll need to do the following to prepare your environment for Skype Meeting Broadcast:
  
- Configure federation with Skype for Business Online resources
    
- Configure SIP federated domains
    
### Configure federation with Skype for Business Online resources

To enable federation with Skype for Business Online resources, you need to configure External Access for a SIP Federated Provider. To do this by using the Skype for Business Server Control Panel follow these steps:
  
1. Start the Skype for Business Server Control Panel and select **External Access** on the left.
    
2. Select **SIP Federated Providers** and click **New**.
    
3. Configure the new provider with the following settings:
    
|||
|:-----|:-----|
|**Enable communications with this provider:** <br/> |Selected  <br/> |
|**Provider name:** <br/> |LyncOnlineResources  <br/> |
|**Access Edge service (FQDN):** <br/> |sipfed.resources.lync.com  <br/> |
|**Default verification level:** <br/> |Allow users to communicate with everyone using this provider.  <br/> |
   
You can also enable federation with Skype for Business Online resources by running the following cmdlet in the Skype for Business Server Management Shell:
  
```
New-CsHostingProvider -Identity LyncOnlineResources -ProxyFqdn sipfed.resources.lync.com -VerificationLevel AlwaysVerifiable -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $True -IsLocal $False
```

### Configure SIP federated domains

Next, you need to add SIP Federated domains to the allowed domain list. Repeat these steps for each of the domains listed, creating 4 new SIP federated domains. These domains include are for the regional data centers used in Skype for Business Online.
  
1. Start the Skype for Business Server Control Panel and select **External Access** on the left.
    
2. Select **SIP Federated Domains** and click **New**.
    
3. For the **Domain name (or FQDN):**, enter the domain, repeating this procedure for each of the following domains:
    
   - noammeetings.lync.com
    
   - emeameetings.lync.com
    
   - apacmeetings.lync.com
    
   - resources.lync.com
    
You can also configure the external access for SIP federated domains by running the following cmdlets in the Skype for Business Server Management Shell:
  
```
New-CsAllowedDomain -Identity "noammeetings.lync.com"
New-CsAllowedDomain -Identity "emeameetings.lync.com"
New-CsAllowedDomain -Identity "apacmeetings.lync.com"
New-CsAllowedDomain -Identity "resources.lync.com"
```

Once you've completed these configuration steps you can start using Skype Meeting Broadcast in your deployment. For more information about Skype Meeting Broadcast, see [What is a Skype Meeting Broadcast?](https://go.microsoft.com/fwlink/?LinkId=617071) and [Skype Meeting Broadcast Admin Guide](https://go.microsoft.com/fwlink/?LinkId=617075).
  

