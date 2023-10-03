---
title: "Get-CcApplianceLogDirectory"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 8f16d8ea-8161-4b07-9c79-d57e786b3e78
description: "The Get-CcApplianceLogDirectory cmdlet shows the current directory where logs for a Skype for Business Cloud Connector Edition appliance are stored."
---

# Get-CcApplianceLogDirectory
 
The Get-CcApplianceLogDirectory cmdlet shows the current directory where logs for a Skype for Business Cloud Connector Edition appliance are stored.
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```powershell
Get-CcApplianceLogDirectory
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the current folder where logs for the current appliance of Cloud Connector are stored:
  
```powershell
Get-CcApplianceLogDirectory
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Get-CcApplianceLogDirectory cmdlet shows the current directory where logs for a Cloud Connector appliance are stored. The default folder is C:\Users\%userprofile%\CloudConnector\ApplianceRoot\Logs. 
  
You can change the directory by using the Set-CcApplianceDirectory cmdlet. 
  
Note: There is no cmdlet that changes only the log folder location without changing the appliance directory.
  
## Input Types
<a name="InputTypes"> </a>

None. The Get-CcApplianceLogDirectory cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

This command returns a file path.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcApplianceDirectory](set-ccappliancedirectory.md)
  

