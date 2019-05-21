---
title: "Convert-CcIsoToVhdx"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 216abec2-d354-4ee3-9999-0a6b350a4a5f
description: "The Convert-CcIsoToVhdx cmdlet creates a base virtual hard disk file (VHDX) using a customer supplied Windows Server 2012 R2 ISO file. The VHDX file will be used during the deployment of Skype for Business Cloud Connector Edition."
---

# Convert-CcIsoToVhdx
 
The Convert-CcIsoToVhdx cmdlet creates a base virtual hard disk file (VHDX) using a customer supplied Windows Server 2012 R2 ISO file. The VHDX file will be used during the deployment of Skype for Business Cloud Connector Edition.
  
```
Convert-CcIsoToVhdx [[-IsoFilePath] <string>] [-GeneralizeOnly] [-PauseBeforeUpdate]
```

## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|IsoFilePath  <br/> | Required <br/> |System.String  <br/> | The path to the Windows Server 2012 R2 ISO file. <br/> |
|GeneralizeOnly  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If the conversion process fails during Windows update, you can try to configure a network/proxy and update Windows manually. After the manual work is done, you can run this cmdlet with the -GeneralizeOnly parameter and it will complete the remaining jobs.  <br/> |
|PauseBeforeUpdate  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |To update Windows, some manual network/proxy configuration on the base VM might be necessary. The conversion process will pause before Windows update if this parameter is provided. After the manual configuration is done, you can resume the process.  <br/> |
   
## Examples
<a name="Examples"> </a>

### Example 1

The following example prepares the base VHDX file using a Windows Server 2012 R2 ISO file located at "C:\Windows_Server_2012_R2-EN-US-x64.ISO": 
  
```
Convert-CcIsoToVhdx -IsoFilePath "C:\Windows_Server_2012_R2-EN-US-x64.ISO" 
```

### Example 2

If the Convert-CcIsoToVhdx cmdlet fails during Windows update, it's probably because of incorrect network/proxy configuration. You can follow the instructions in the error message and log on to the base virtual machine to fix the issue and update Windows manually. After the manual work is done, run the cmdlet again with the -GeneralizeOnly parameter to complete the remaining jobs: 
  
```
Convert-CcIsoToVhdx -IsoFilePath "C:\Windows_Server_2012_R2-EN-US-x64.ISO" -GeneralizeOnly
```

### Example 3

If manual configuration is necessary to update Windows, you can use the -PauseBeforeUpdate parameter. With this parameter, Cloud Connector will pause before the Windows update process. You can then complete the manual configuration and resume the conversion process as follows:
  
```
Convert-CcIsoToVhdx -IsoFilePath "C:\Windows_Server_2012_R2-EN-US-x64.ISO" -PauseBeforeUpdate 
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Convert-CcIsoToVhdx cmdlet creates a base VM first, installs some basic components that Cloud Connector depends on, and then installs Windows updates. Finally, it generalizes the virtual machine (sysprep) to get a base VHDX file that will be used by the virtual machines of a Cloud Connector appliance. 
  
## Input Types
<a name="InputTypes"> </a>

None. The Convert-CcIsoToVhdx cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

None
  

