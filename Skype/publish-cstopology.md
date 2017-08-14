---
title: Publish-CsTopology
ms.prod: SKYPEFORBUSINESS
ms.assetid: d8f5dfd9-0ab6-4703-9d50-2fa50b3fd58b
---


# Publish-CsTopology
[]
Publishes the Skype for Business Server 2015 topology retrieved by using the **Get-CsTopology** cmdlet. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Publish-CsTopology -FileName <String> <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The commands shown in Example 1 retrieve and then republish the current topology. To carry out these tasks, the first command in the example uses the **Get-CsTopology** cmdlet and the AsXml parameter to retrieve the current topology; the Windows PowerShell redirection symbol > is then used to save the retrieved data to a file named C:\\Topologies\\Topology.xml. (Note, too, that the ToString method is used to convert the retrieved topology to a string value.) The second command in the example then uses the **Publish-CsTopology** cmdlet to republish the newly retrieved topology.
  
    
    

```

(Get-CsTopology -AsXml).ToString() > C:\\Topologies\\Topology.xml
Publish-CsTopology -FileName "C:\\Topologies\\Topology.xml"
```


## Detailed Description

After you have installed Skype for Business Server 2015, you will eventually need to make changes to the Skype for Business Server 2015 infrastructure; for example, you might need to add a new site, delete an existing Registrar pool, or add an additional Archiving Server. These infrastructure changes must be made by using Topology Builder. After you have made the changes in Topology Builder, you can then publish and enable those changes using that same tool. These latter two steps are very important: although you can make as many modifications as you want using the Topology Builder, those modifications do not actually take effect, and your Skype for Business Server 2015 infrastructure will not actually change, until the modifications have been published and the new topology has been enabled. 
  
    
    
When changes are published, the new information (for example, a new site or a new server role) is written to the Central Management store. However, these new (or the newly modified) objects do not immediately join your topology; that occurs only when the updated topology has been enabled. If you select the Publish option in Topology Builder both of these steps will take place: the changes will be published (written to the Central Management store) and then the new topology will be enabled.
  
    
    
The **Publish-CsTopology** cmdlet is no longer the recommended way to publish topologies created by using Topology Builder; instead, publishing should be done within Topology Builder, using the steps outlined in the previous paragraph. This is because Topology Builder now uses the Topology Builder XML file format (.tbxml); this file format cannot be published by using the **Publish-CsTopology** cmdlet. The only thing you can do with the **Publish-CsTopology** cmdlet is republish a topology retrieved by using the **Get-CsTopology** cmdlet. After publishing the topology in this manner, you will then need to reconfigure your simple URLs.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Document_ <br/> |Required  <br/> |System.Xml.Linq.XElement  <br/> |Enables you to publish an XML element rather than an XML file. This XML element must be configured as a System.XML.Linq.XElement object.  <br/> |
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Full path to the XML file containing the new topology information.  <br/> |
| _FinalizeUninstall_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Used only when uninstalling Skype for Business Server 2015.After the Central Management Server has been removed, use Publish-CsTopology and the FinalizeUninstall parameter to publish an empty topology. Among other things, this removes all the Active Directory entries for the Central Management Server.  <br/> |
| _BackupFileName_ <br/> |Optional  <br/> |System.String  <br/> |Full path to the backup file automatically created when you run the **Publish-CsTopology** cmdlet. If this parameter is not specified, then the **Publish-CsTopology** cmdlet will create a backup file in your Temp folder (%temp%) similar to this: Publish-CsTopology-Backup-[2010_10_01][08_30_00]. In that file name, 2010_10_01 represents the date that publication took place: year (2010), month (10), and day (01). In addition, 08_30_00 represents the time of day when publication took place: hour (08), minutes (30), and seconds (00). <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Publish-CsTopology** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\\Logs\\Publish_Topology.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

None. The **Publish-CsTopology** cmdlet does not accept pipelined input.
  
    
    

## Return Types

None. Instead, the **Publish-CsTopology** cmdlet publishes instances of the Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology object.
  
    
    

## See also


#### 


  
    
    
 [Enable-CsTopology](enable-cstopology.md)
  
    
    
 [Get-CsTopology](get-cstopology.md)
  
    
    
 [New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)
  
    
    
 [Test-CsTopology](test-cstopology.md)
