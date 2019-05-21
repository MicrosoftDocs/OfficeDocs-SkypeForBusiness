---
title: "Import-CcConfiguration"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 10/11/2017
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 461361a0-9aa9-469d-ace0-dc70b95cd4a3
description: "Imports the Skype for Business Cloud Connector Edition configuration from a local file to the Cloud Connector host server."
---

# Import-CcConfiguration
 
Imports the Skype for Business Cloud Connector Edition configuration from a local file to the Cloud Connector host server.
  
```
Import-CcConfiguration [-Force] [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example copies the CloudConnector.ini from the appliance directory of the Cloud Connector instance to %SystemDrive%\ProgramData\CloudConnector directory:
  
```
Import-CcConfiguration
```

## Detailed Description
<a name="Examples"> </a>

This cmdlet copies the CloudConnector.ini from the appliance directory of the Cloud Connector appliance to the %SystemDrive%\ProgramData\CloudConnector directory. The appliance directory is specified by using the Set-CcApplianceDirectory cmdlet. The cmdlet will overwrite any existing file in %SystemDrive%\ProgramData\CloudConnector. This command applies to Cloud Connector Edition version 2.0.1 and later.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Force  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Overwrite existing file in %SystemDrive%\ProgramData\CloudConnector without notification.  <br/> |
   
## Input Types
<a name="Examples"> </a>

None. The Import-CcConfiguration cmdlet does not accept pipelined input.
  
## Return Types
<a name="Examples"> </a>

None.
  
## See also
<a name="Examples"> </a>

Export-CcConfiguration
  

