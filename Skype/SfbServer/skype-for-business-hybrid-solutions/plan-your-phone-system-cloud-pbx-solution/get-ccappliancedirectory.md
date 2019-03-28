---
title: "Get-CcApplianceDirectory"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c2fda202-db2f-4122-b630-7df11a697c5f
description: "The Get-CcApplianceDirectory cmdlet retrieves the working directory on the Skype for Business Cloud Connector Edition host server. All deployment files are stored in this directory."
---

# Get-CcApplianceDirectory
 
The Get-CcApplianceDirectory cmdlet retrieves the working directory on the Skype for Business Cloud Connector Edition host server. All deployment files are stored in this directory. 
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Get-CcApplianceDirectory
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the current folder where configuration and virtual machine files of Cloud Connector components are stored:
  
```
Get-CcApplianceDirectory
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Get-CcApplianceDirectory cmdlet shows where all configuration and virtual machine files, logs, and external certificates are stored for the Cloud Connector appliance.
  
Each Cloud Connector appliance has four components: Mediation Server, Central Management Store, Edge Server, and a Domain Controller. The default folder is C:\Users\%userprofile%\CloudConnector\ApplianceRoot. You can change this folder by using the Set-CCApplianceDirectory cmdlet.
  
## Input Types
<a name="InputTypes"> </a>

None. The Get-CCApplianceDirectory cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The command returns a file path.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcApplianceDirectory](set-ccappliancedirectory.md)
  

