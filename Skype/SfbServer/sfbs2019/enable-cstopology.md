---
title: "Enable-CsTopology"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5aedffa0-9ca1-4aec-b4ad-c3e409c0ffb2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Enable-CsTopology
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables the most recently published Lync Server topology. After you have made changes to your topology, the changes will not take effect until they have been both published and enabled. This cmdlet was introduced in Lync Server 2010.
  
```
Enable-CsTopology [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 enables the most recently published topology.
  
```
Enable-CsTopology
```

## Detailed Description
<a name="sectionSection1"> </a>

After you have installed Lync Server you will eventually need to make changes to the infrastructure; for example, you might need to add a new site, delete an existing Registrar pool, or add an additional Archiving Server. These infrastructure changes must be made by using Topology Builder. After you have made the changes in Topology Builder, you can then publish and enable those changes using that same tool. These latter two steps are very important: although you can make as many modifications as you want using Topology Builder, those modifications do not actually take effect, and your infrastructure will not actually change, until the modifications have been published and the new topology has been enabled.
  
When changes are published, the new information (for example, a new site or a new server role) is written to the Central Management store. However, these new (or newly modified) objects do not immediately join your topology; that occurs only when the updated topology has been enabled. If you select the Publish option in Topology Builder you can carry out both of these steps at the same time: the changes will be published (written to the Central Management store) and the new topology will be enabled.
  
There might be times, however, when you would prefer to publish your changes and enable your topology as separate steps; doing so gives you an opportunity to confirm that deployment has succeeded before you bring the new objects into the topology. To separately publish and then enable topology changes, you must do the following:
  
Publish the modified topology in Topology Builder. (Due to late changes in the product, we recommend that publishing always take place using Topology Builder.)
  
Use the **Enable-CsTopology** cmdlet to cause the published changes to take effect. 
  
From time-to-time you might also need to call the **Enable-CsTopology** cmdlet in order to enable changes made outside Topology Builder. For example, the cmdlet must be run after you have used the CsKerberosAccountAssignment cmdlets to modify Kerberos web authentication. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Enable-CsTopology** cmdlet locally: RTCUniversalServerAdmins. However, if setup permissions have not been delegated, then you must be a domain administrator in order to run the cmdlet. In order to give RTCUniversalServerAdmins the right to actually use the **Enable-CsTopology** cmdlet, you must run the **Grant-CsSetupPermission** cmdlet against every Active Directory container that contains computers running Lync Server services. Note that this restriction also applies to enabling a topology through Topology Builder. If you have not delegated permissions by using the **Grant-CsSetupPermission** cmdlet, then only a domain administrator will be able to enable a topology through Topology Builder. 
  
In addition, you must be a local administrator on any computer where Lync Server file shares are to be created; this is required in order to set the necessary security permissions on the shared folders. Alternatively, you can run the **Enable-CsTopology** cmdlet if you have full control over the file share. That enables the cmdlet to create the shared folders and set share-level security permissions. However, a local administrator will then need to add the share-level security permissions. 
  
To verify that setup permissions have been delegated, run the **Test-CsSetupPermission** cmdlet against any Active Directory containers containing computers running Lync Server services. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsTopology** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\Enable_Topology.html"  <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True ($True) the **Enable-CsTopology** cmdlet will skip its initial preparation check.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Enable-CsTopology** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Enable-CsTopology** cmdlet enables instances of the Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsTopology](get-cstopology.md)
  
[Grant-CsSetupPermission](grant-cssetuppermission.md)
  
[Publish-CsTopology](publish-cstopology.md)
  
[Test-CsSetupPermission](test-cssetuppermission.md)
  
[Test-CsTopology](test-cstopology.md)

