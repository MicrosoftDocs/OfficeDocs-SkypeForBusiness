---
title: "Get-CcVersion"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 6/30/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7d370abd-0c01-4490-88a1-55b42e51b663
description: "Returns the version of the Cloud Connector appliance. Get-CCVersion can only be used on the host machine of Cloud Connector."
---

# Get-CcVersion
 
Returns the version of the Cloud Connector appliance. Get-CCVersion can only be used on the host machine of Cloud Connector.
  
```
Get-CcVersion [[-VersionType] <String>] [<CommonParameters>]
```

## Detailed Description

Returns the version of the Cloud Connector appliance based on PowerShell scripts installed, files in the Appliance directory, and the virtual machines deployed on host server.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|VersionType  <br/> |Optional  <br/> |System.String  <br/> |Type of version. Value of parameter can be RunningScripts, RunningBits, BackupBits or All. Default value is RunningScripts.  <br/> |
   
## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the Cloud Connector version of the currently running script in your open PowerShell console:
  
```
Get-CcVersion
```

### Example 2

The following example shows the Cloud Connector version of the currently running binaries deployed to the virtual machines. You can see the version in the running virtual machine names in Hyper-v Manager:
  
```
Get-CCVersion -VersionType RunningBits
```

## Input Types
<a name="Examples"> </a>

None. The Get-CcVersion cmdlet does not accept pipelined input.
  
## Return Types
<a name="Examples"> </a>

None.
  
## See also
<a name="Examples"> </a>

None.
  

