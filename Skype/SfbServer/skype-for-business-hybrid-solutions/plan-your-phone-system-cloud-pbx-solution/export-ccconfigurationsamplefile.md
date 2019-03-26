---
title: "Export-CcConfigurationSampleFile"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0aaacc05-3430-4579-acbf-d7c7670c3864
description: "The Export-CcConfigurationSampleFile cmdlet exports a Skype for Business Cloud Connector Edition sample configuration file (.ini) to the appliance directory of a Cloud Connector appliance. You can modify and rename the file to use for your deployment."
---

# Export-CcConfigurationSampleFile
 
The Export-CcConfigurationSampleFile cmdlet exports a Skype for Business Cloud Connector Edition sample configuration file (.ini) to the appliance directory of a Cloud Connector appliance. You can modify and rename the file to use for your deployment.
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Export-CcConfigurationSampleFile
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example downloads a sample configuration file from the Microsoft site and writes it to the appliance directory of the Cloud Connector appliance:
  
```
Export-CcConfigurationSampleFile
```

## Detailed Description
<a name="DetailedDescription"> </a>

The current version of Cloud Connector requires you to provide several parameters in the .ini file; for example, parameters such as the IP addresses of virtual machines for the Cloud Connector components, component names, gateway parameters, and so on.
  
This cmdlet, when run on the host machine of Cloud Connector, downloads a sample .ini file with configuration examples from the Microsoft site. The cmdlet writes the file to the appliance directory of the Cloud Connector appliance. The appliance directory is specified by using the Set-CcApplianceDirectory cmdlet.
  
## Input Types
<a name="InputTypes"> </a>

None. The Export-CcConfigurationSampleFile cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcApplianceDirectory](set-ccappliancedirectory.md)
  

