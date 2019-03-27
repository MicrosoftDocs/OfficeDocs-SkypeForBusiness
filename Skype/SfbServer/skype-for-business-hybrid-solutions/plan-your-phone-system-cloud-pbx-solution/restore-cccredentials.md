---
title: "Restore-CcCredentials"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aeca610b-db0a-45cf-95b9-ae9a6bbccb45
description: "The Restore Cc-Credentials cmdlet restores all credentials of the current Skype for Business Cloud Connector Edition deployment."
---

# Restore-CcCredentials
 
The Restore Cc-Credentials cmdlet restores all credentials of the current Skype for Business Cloud Connector Edition deployment. 
  
This cmdlet applies to Skype for Business Cloud Connector Edition 2.1.
  
```
Restore-CcCredentials 
```

## Detailed Description

The Restore-CcCredentials cmdlet cleans up all credentials and prompts you to re-enter all the credentials used for the current Skype for Business Cloud Connector deployment.
  
## Parameters

None
  
## Input Types

None. The Restore-CcCredentials cmdlet does not accept pipelined input.
  
## Return Types

None.
  
## Example

The following example restores all credentials of the current Cloud Connector deployment:
  
```
    PS C:\>Restore-CcCredentials
```

## See also

[Get-CcCredential](get-cccredential.md)
  
[Set-CcCredential](set-cccredential.md)
  

