---
title: "Exit-CcUpdate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 463dce1e-fb60-487d-bcf1-69e7b03ecd14
description: "The Exit-CcUpdate cmdlet exits update maintenance mode on the Skype for Business Cloud Connector Edition host server."
---

# Exit-CcUpdate
 
The Exit-CcUpdate cmdlet exits update maintenance mode on the Skype for Business Cloud Connector Edition host server. 
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2. 
  
```
Exit-CcUpdate
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following command puts the appliance on which it runs back into production mode: 
  
```
Exit-CcUpdate
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you have appliances that you have put in maintenance mode by specifying the Enter-CcUpdate cmdlet, the Exit-CcUpdate cmdlet will put these back into production mode. 
  
For more information about putting appliances in maintenance mode, see Enter-CcUpdate.
  
## Input Types
<a name="InputTypes"> </a>

None. The Exit-CcUpdate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None 
  
## See also
<a name="ReturnTypes"> </a>

[Enter-CcUpdate](enter-ccupdate.md)
  

