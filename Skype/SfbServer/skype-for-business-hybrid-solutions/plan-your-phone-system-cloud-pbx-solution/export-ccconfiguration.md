---
title: "Export-CcConfiguration"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e3775bd6-682c-4f62-aafc-974fe3a65c61
description: "Exports the Skype for Business Cloud Connector Edition configuration to a local file on the Skype for Business Cloud Connector Edition host server."
---

# Export-CcConfiguration
 
Exports the Skype for Business Cloud Connector Edition configuration to a local file on the Skype for Business Cloud Connector Edition host server.
  
```
Export-CcConfiguration [-Path] <String> [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example sets the Path parameter as a full file path and exports configurations to that file.
  
```
Export-CcConfiguration -Path "C:\test\CloudConnector.ini" 
```

## Detailed Description
<a name="Examples"> </a>

The Export-CcConfiguration cmdlet allows you to save the Cloud Connector configuration to a file in a selected path. This command was introduced in Cloud Connector Edition version 2.0.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Path  <br/> |Required  <br/> |System.String  <br/> |Full file path where the Cloud Connector configurations will be stored.  <br/> |
   
## Input Types
<a name="Examples"> </a>

None. The Export-CcConfiguration cmdlet does not accept pipelined input.
  
## Return Types
<a name="Examples"> </a>

None.
  
## See also
<a name="Examples"> </a>

Import-CcConfiguration
  

