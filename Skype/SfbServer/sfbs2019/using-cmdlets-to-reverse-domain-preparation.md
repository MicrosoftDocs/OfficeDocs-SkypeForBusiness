---
title: "Using cmdlets to reverse domain preparation for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 014dba5d-fcb3-44c9-9d63-ae0755276dac
description: "Use the Disable-CsAdDomain cmdlet to reverse the domain preparation step."
---

# Using cmdlets to reverse domain preparation for Lync Server 2013
[]
Use the **Disable-CsAdDomain** cmdlet to reverse the domain preparation step. 
  
### To use cmdlets to reverse domain preparation

1. Log on to any server in the domain as a member of the Domain Admins group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Disable-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] 
  [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] 
  ```

    For example:
    
  ```
  Disable-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.net -Force
  ```

    If the Force parameter is present, domain preparation is rolled back, even if one or more Front End Servers or A/V Conferencing Servers in the domain are activated. If the Force parameter is not present, domain preparation rollback is terminated if any Front End Servers or A/V Conferencing Servers in the domain are activated.
    
    > [!NOTE]
    > The parameter GlobalSettingsDomainController allows you to indicate where global settings are stored. If your settings are stored in the System container (which is typical with upgrade deployments that have not had the global setting migrated to the Configuration container), you define a domain controller in the root of your Active Directory forest. If the global settings are in the Configuration container (which is typical with new deployments or upgrade deployments where the settings have been migrated to the Configuration container), you define any domain controller in the forest. If you do not specify this parameter, the cmdlet assumes that the settings are stored in the Configuration container and refers to any domain controller in AD DS. 
  
## See also

#### 

[Running domain preparation for Lync Server 2013](running-domain-preparation.md)
#### 

[Preparing domains for Lync Server 2013](preparing-domains.md)

