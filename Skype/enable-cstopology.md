---
title: Enable-CsTopology
ms.prod: SKYPEFORBUSINESS
ms.assetid: 5aedffa0-9ca1-4aec-b4ad-c3e409c0ffb2
---


# Enable-CsTopology
[]
Enables the most recently published Skype for Business Server 2015 topology. After you have made changes to your topology, the changes will not take effect until they have been both published and enabled. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Enable-CsTopology [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 enables the most recently published topology.
  
    
    

```

Enable-CsTopology
```


## Detailed Description

After you have installed Skype for Business Server 2015 you will eventually need to make changes to the infrastructure; for example, you might need to add a new site, delete an existing Registrar pool, or add an additional Archiving Server. These infrastructure changes must be made by using Topology Builder. After you have made the changes in Topology Builder, you can then publish and enable those changes using that same tool. These latter two steps are very important: although you can make as many modifications as you want using Topology Builder, those modifications do not actually take effect, and your infrastructure will not actually change, until the modifications have been published and the new topology has been enabled.
  
    
    
When changes are published, the new information (for example, a new site or a new server role) is written to the Central Management store. However, these new (or newly modified) objects do not immediately join your topology; that occurs only when the updated topology has been enabled. If you select the Publish option in Topology Builder you can carry out both of these steps at the same time: the changes will be published (written to the Central Management store) and the new topology will be enabled.
  
    
    
There might be times, however, when you would prefer to publish your changes and enable your topology as separate steps; doing so gives you an opportunity to confirm that deployment has succeeded before you bring the new objects into the topology. To separately publish and then enable topology changes, you must do the following:
  
    
    
Publish the modified topology in Topology Builder. (Due to late changes in the product, we recommend that publishing always take place using Topology Builder.)
  
    
    
Use the **Enable-CsTopology** cmdlet to cause the published changes to take effect.
  
    
    
From time-to-time you might also need to call the **Enable-CsTopology** cmdlet in order to enable changes made outside Topology Builder. For example, the cmdlet must be run after you have used the CsKerberosAccountAssignment cmdlets to modify Kerberos web authentication.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsTopology** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\\Logs\\Enable_Topology.html"  <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True ($True) the **Enable-CsTopology** cmdlet will skip its initial preparation check. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The **Enable-CsTopology** cmdlet does not accept pipelined input.
  
    
    

## Return Types

None. Instead, the **Enable-CsTopology** cmdlet enables instances of the Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsTopology](get-cstopology.md)
  
    
    
 [Grant-CsSetupPermission](grant-cssetuppermission.md)
  
    
    
 [Publish-CsTopology](publish-cstopology.md)
  
    
    
 [Test-CsSetupPermission](test-cssetuppermission.md)
  
    
    
 [Test-CsTopology](test-cstopology.md)
