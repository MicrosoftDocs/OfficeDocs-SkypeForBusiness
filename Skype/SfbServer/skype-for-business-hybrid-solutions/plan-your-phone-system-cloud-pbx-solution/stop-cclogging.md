---
title: "Stop-CcLogging"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fee9eda7-ad15-40d2-b9fe-21c5462d3309
description: "The Stop-CcLogging cmdlet stops generating the incoming and outgoing call log for a Skype for Business Cloud Connector Edition appliance."
---

# Stop-CcLogging
 
The Stop-CcLogging cmdlet stops generating the incoming and outgoing call log for a Skype for Business Cloud Connector Edition appliance.
  
```
Stop-CcLogging [-RemoveCache]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example stops generating the incoming and outgoing call log: 
  
```
Stop-CcLogging
```

### Example 2

The next example stops generating the incoming and outgoing call log and cleans up the cache files:
  
```
Stop-CcLogging -RemoveCache
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Stop-CcLogging cmdlet stops logging of incoming and outgoing calls on an appliance. By default, logging will automatically stop after four hours.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| RemoveCache <br/> | Optional <br/> | System.Management.Automation.SwitchParameter <br/> |Removes the logging cache files.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Stop-CcLogging cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Search-CcLog](search-cclog.md)
  
[Start-CcLogging](start-cclogging.md)
  

