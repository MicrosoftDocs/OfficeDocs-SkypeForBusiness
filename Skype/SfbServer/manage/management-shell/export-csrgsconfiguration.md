---
title: "Export-CsRgsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 754513a4-0b46-44b7-8910-f865b1e0f037
description: "Exports data from an existing Response Group application configuration. This data, saved as a .ZIP file, can later be imported using the Import-CsRgsConfiguration cmdlet. The ability to export and import Response Group configuration data is particularly useful disaster recovery scenarios. This cmdlet was introduced in Lync Server 2013."
---

# Export-CsRgsConfiguration
 
Exports data from an existing Response Group application configuration. This data, saved as a .ZIP file, can later be imported using the **Import-CsRgsConfiguration** cmdlet. The ability to export and import Response Group configuration data is particularly useful disaster recovery scenarios. This cmdlet was introduced in Lync Server 2013.
  
```
Export-CsRgsConfiguration -FileName <String> -Source <RgsIdentity> [-Force <SwitchParameter>] [-Owner <RgsIdentity>] [-RemoveExportedConfiguration <SwitchParameter>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 exports the Response Group configuration settings from the pool atl-rgs-001.litwareinc.com to a file with the path C:\Exports\Rgs.zip.
  
```
Export-CsRgsConfiguration -Source "ApplicationServer:atl-rgs-001.litwareinc.com" -FileName "C:\Exports\Rgs.zip"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Export-CsRgsConfiguration** cmdlet and the[Import-CsRgsConfiguration](import-csrgsconfiguration.md) cmdlet enable you to export data about your current implementation of the Response Group application (including such things as workflows, queues, agent groups, holiday sets and business hours, as well as audio files and service configuration settings) and then later import (or re-import) that information. This can be extremely useful in a disaster recovery scenario (for example, in a case where the server hosting the Response Group application has failed) or if you simply need to transfer the Response Group application to a different pool.
  
Note that the **Export-CsRgsConfiguration** cmdlet and the **Import-CsRgsConfiguration** cmdlet are designed to work only with Lync Server 2013 and Skype for Business Server 2015. If you want to migrate Response Group data from Microsoft Lync Server 2010 to Skype for Business Server 2015, you should use the [Move-CsRgsConfiguration](move-csrgsconfiguration.md) cmdlet instead.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Export-CsRgsConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Path to the .ZIP file to be created when you run the **Export-CsRgsConfiguration** cmdlet. For example: <br/>  `-FileName "C:\Exports\RgsConfig.zip"` <br/> Note that your command will fail if this file already exists.  <br/> |
| _Source_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |Identity of the Response Group instance whose configuration settings are being exported. For example:  <br/>  `-Source "ApplicationServer:atl-rgs-001.litwareinc.com"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Owner_ <br/> |Optional  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |If specified, configuration information for all the Response Group instances found on the designated pool will be exported. For example:  <br/>  `-Owner "atl-rgs-001.litwareinc.com"` <br/> |
| _RemoveExportedConfiguration_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, the Response Group instance will be deleted after the configuration information has been exported.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Export-CsRgsConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Export-CsRgsConfiguration** cmdlet creates compressed files with the .ZIP file extension.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Import-CsRgsConfiguration](import-csrgsconfiguration.md)

