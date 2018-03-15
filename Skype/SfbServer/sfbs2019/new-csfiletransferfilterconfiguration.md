---
title: "New-CsFileTransferFilterConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d1050fb-5df9-4186-94b9-8ef8a9103958
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsFileTransferFilterConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new file transfer filter configuration. File transfer filter configurations are used to block a user's ability to transfer certain types of files (for example, files with a .vbs or .ps1 file extension) using a Lync Server client. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsFileTransferFilterConfiguration -Identity <XdsIdentity> [-Action <BlockAll | Block>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Extensions <PSListModifier>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **New-CsFileTransferFilterConfiguration** cmdlet is used to create a new instant message file transfer filter configuration with the Identity site:Redmond. Because no additional parameters were specified, the configuration will be created using the default values. 
  
```
New-CsFileTransferFilterConfiguration -Identity site:Redmond

```

### EXAMPLE 2

In this command, the **New-CsFileTransferFilterConfiguration** cmdlet is used to create a new file transfer filter configuration with the Identity site:Redmond. Because the Extensions parameter has been specified, the new configuration will contain all the default values plus an additional file extension: .ps1. This new extension is added by using the Extensions parameter and the list modifier Add followed by the file extension to be added. (Note that you must include the period as part of the file extension.) To add multiple file extensions, simply separate those extensions by using commas: @{Add=".ps1",".ps2",".ps3"} 
  
```
New-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Add=".ps1"}
```

### EXAMPLE 3

In Example 3, the **New-CsFileTransferFilterConfiguration** cmdlet is used to create a new file transfer filter configuration with the Identity site:Redmond. This example is similar to Example 2 except that the Replace list modifier has been used instead of the Add modifier. This means that the complete set of file extensions will be replaced by the two specified file extensions: .vbs and .ps1. In this case the only files blocked at the Redmond site will be .vbs and .ps1. 
  
```
New-CsFileTransferFilterConfiguration -Identity site:Redmond -Extensions @{Replace=".vbs",".ps1"}
```

### EXAMPLE 4

Example 4 demonstrates the use of the InMemory parameter to create a file transfer filter configuration that initially resides in memory only. To do this the first command in the example uses the **New-CsFileTransferFilterConfiguration** cmdlet and the InMemory parameter to create a new file transfer filter configuration with the Identity site:Redmond. At this point in time, the new settings exist only in memory; users in the Redmond site will still be governed by the global file transfer filter settings. 
  
In the second command, the value of the Action property for this in-memory instance is set to BlockAll. Finally, the third command in the example uses the **Set-CsFileTransferFilterConfiguration** cmdlet to create the new collection of settings and apply them to the Redmond site. 
  
Note that this same task can be accomplished in one step with the following command:
  
```
New-CsFileTransferFilterConfiguration -Identity site:Redmond -Action "BlockAll"
$x = New-CsFileTransferFilterConfiguration -Identity site:Redmond -InMemory 
$x.Action = "BlockAll"
Set-CsFileTransferFilterConfiguration -Instance $x
```

## Detailed Description
<a name="sectionSection1"> </a>

When sending instant messages, users can attach and send files to the other participants in the conversation. Lync Server can be configured so that files with certain extensions--typically extensions of file types that could potentially prove harmful--are not allowed to be sent using a Lync Server client.
  
When you install Lync Server, a single file transfer filter configuration (which is configured at the global scope) is created for you. By default, the global configuration applies to all the users in your organization. In addition, you can use the **New-CsFileTransferFilterConfiguration** cmdlet to create custom file transfer filter configurations for individual sites. If a configuration exists for a given site then those file transfer settings will be applied to all the users in that site. If no such collection exists for a site then the global settings will be applied instead. 
  
Note that you cannot create new a file transfer filter configuration at the global scope; however, you can use the **Set-CsFileTransferFilterConfiguration** cmdlet to modify the global settings. Likewise, you cannot create a new configuration for a site that already has one defined; if you try that, your command will fail. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsFileTransferFilterConfiguration** cmdlet locally: RTCUniversalServerAdministrator. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsFileTransferFilterConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier to be given to the file transfer filter configuration. The Identity for the new configuration is simply the prefix "site:" followed by the site name. For example, to create a new configuration for the Redmond site, you would use this syntax: -Identity site:Redmond.  <br/> |
| _Action_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileFilterAction  <br/> |Determines the action to be taken if file transfer filtering is enabled. If set to BlockAll then all file transfers will be prohibited, regardless of file extension. If set to Block (the default value) file transfers will be allowed unless the file extension appears as one of the prohibited file types listed in the Extensions property.  <br/> To allow unrestricted file transfers (that is, to allow users to exchange any type of file, regardless of file extension), set the Enabled property of this policy to False.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Enables or disables file transfer filtering. If this parameter is set to True, files with the specified extensions (or all files, depending on the value of the Action property) cannot be transferred by a Lync Server client. If this parameter is set to False, any file can be transferred.  <br/> Default: True.  <br/> |
| _Extensions_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |List of file extensions that will be blocked. If you attempt to use a Lync Server client to transfer a file that has a file extension matching one of the extensions in this list, that transfer will be blocked and the file will not be transferred. This list is ignored if Action is set to BlockAll (all file transfers are blocked) or if Enabled is set to False (no file transfers are blocked).  <br/> By default, the following file extensions are included in the Extensions property: .ade, .adp, .app, .asp, .bas, .bat, .cer, .chm, .cmd, .com, .cpl, .crt, .csh, .exe, .fxp, .grp, .hlp, .hta, .inf, .ins, .isp, .its, .js, .jse, .ksh, .lnk, .mad, .maf, .mag, .mam, .maq, .mar., mas., .mat, .mau, .mav, .maw, .mda, .mdb. .mde, .mdt, .mdw, .mdz, .msc, .msi, .msp, .mst, .ocx, .ops, .pcd, .pif, .pl, .pnp, .prf, .prg, .pst, .reg, .scf, .scr, .sct, .shb, .shs, .tmp, .url, .vb, .vbe, .vbs, .vsd, .vsmacros, .vss, .vst, .vsw, .ws, .wsc. .wsf, .wsh  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> | Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsFileTransferFilterConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)
  
[Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)
  
[Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)

