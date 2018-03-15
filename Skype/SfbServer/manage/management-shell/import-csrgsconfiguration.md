---
title: "Import-CsRgsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c4977e34-7a62-4cb7-b8ec-bacb471b3de4
description: "Imports Response Group configuration data that was previously exported using the Export-CsRgsConfiguration cmdlet. The ability to export and import Response Group configuration data is particularly useful disaster recovery scenarios. This cmdlet was introduced in Lync Server 2013."
---

# Import-CsRgsConfiguration
 
Imports Response Group configuration data that was previously exported using the **Export-CsRgsConfiguration** cmdlet. The ability to export and import Response Group configuration data is particularly useful disaster recovery scenarios. This cmdlet was introduced in Lync Server 2013.
  
```
Import-CsRgsConfiguration -Destination <RgsIdentity> -FileName <String> [-Force <SwitchParameter>] [-OverwriteOwner <SwitchParameter>] [-ReplaceExistingRgsSettings <SwitchParameter>] [-ResolveNameConflicts <SwitchParameter>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 imports a previously exported collection of Response Group application settings, and then applies those settings to the Response Group installation hosted by the Application Server on atl-cs-001.litwareinc.com.
  
```
Import-CsRgsConfiguration -FileName "C:\Export\RgsExport.zip" -Destination "ApplicationServer:atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The [Export-CsRgsConfiguration](export-csrgsconfiguration.md) cmdlet and the **Import-CsRgsConfiguration** cmdlet enable you to export data about your current implementation of the Response Group application (including such things as workflows, queues, agent groups, holiday sets and business hours, as well as audio files and service configuration settings) and then later import (or re-import) that information. This can be extremely useful in a disaster recovery scenario (for example, in a case where the server hosting the Response Group application has failed) or if you simply need to transfer the Response Group application to a different pool.
  
Note that the **Export-CsRgsConfiguration** cmdlet and the **Import-CsRgsConfiguration** cmdlet are designed to work only with Lync Server 2013 and Skype for Business Server 2015. If you want to migrate Response Group data from Microsoft Lync Server 2010 to Skype for Business Server 2015, you should use the [Move-CsRgsConfiguration](move-csrgsconfiguration.md) cmdlet instead.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Import-CsRgsConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Destination_ <br/> |Required  <br/> |Microsoft.Rtc.Rgs.Management.RgsIdentity  <br/> |Identity of the Response Group instance where the configuration settings are being imported. For example:  <br/>  `-Destination "ApplicationServer:atl-rgs-001.litwareinc.com"` <br/> |
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Path to the .ZIP file created by the **Export-CsRgsConfiguration** cmdlet. For example: <br/>  `-FileName "C:\Exports\RgsConfig.zip"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OverwriteOwner_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present the current owner of the Response Group objects will be overwritten with the service identity of the new Response Group pool.  <br/> |
| _ReplaceExistingRgsSettings_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, all the existing service settings for the destination pool are replaced with the imported settings. If not specified, then service settings will remain as-is and only Response Group object (such as workflows and agent groups) will be imported.  <br/> |
| _ResolveNameConflicts_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, duplicate names will be resolved by appending a unique identifying number. For example, if there are two workflows named Help Desk Workflow one of the two will be renamed Help Desk Workflow (2).  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Import-CsRgsConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Export-CsRgsConfiguration](export-csrgsconfiguration.md)

