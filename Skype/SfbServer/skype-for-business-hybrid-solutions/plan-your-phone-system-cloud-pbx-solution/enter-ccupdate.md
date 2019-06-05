---
title: "Enter-CcUpdate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
ms.date: 3/31/2017
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 330367f2-22b0-43e3-b8fb-3e0d2e3b330e
description: "The Enter-CcUpdate cmdlet prepares the Skype for Business Cloud Connector Edition host server for the update process by putting it in maintenance mode. The appliance isdrained—that is, all existing calls will complete, but new calls are rejected."
---

# Enter-CcUpdate

The Enter-CcUpdate cmdlet prepares the Skype for Business Cloud Connector Edition host server for the update process by putting it in maintenance mode. The appliance immediately stops all services, ending any ongoing calls and rejecting any new calls.
  
```
Enter-CcUpdate
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example prepares the appliance for the update process by entering maintenance mode:
  
```
Enter-CcUpdate 
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Enter-CcUpdate cmdlet will immediately stop all services ending any ongoing calls and the appliance will reject any new calls, which are transferred to other production appliances. You must ensure that the remaining production appliances have enough capacity to handle the calls from the appliance that you are preparing to update.
  
Maintenance mode is useful if your appliance has automatic update enabled, for example, and Microsoft releases a critical hotfix. Maintenance mode is also useful if you decide to turn off automatic updates, but you perform manual updates on a consistent basis.
  
After installing the updates, the appliance can be brought back to production mode by running the Exit-CcUpdate cmdlet.
  
> [!NOTE]
> If you decide to manually update a Cloud Connector appliance, you need to update it within 60 days after Microsoft releases the next version. Microsoft supports the previously-released version of Cloud Connector for 60 days after the new version is released 
  
## Input Types
<a name="InputTypes"> </a>

None. The Enter-CCUpdate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None 
  
## See also
<a name="ReturnTypes"> </a>

[Exit-CcUpdate](exit-ccupdate.md)
  

