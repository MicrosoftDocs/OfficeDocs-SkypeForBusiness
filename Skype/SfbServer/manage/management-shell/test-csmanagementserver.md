---
title: "Test-CsManagementServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: bdeec5b0-3e7e-4098-acd8-9ec5849f4871
description: "Verifies that the Central Management service is working correctly. The Central Management service is responsible for replicating data between the Central Management store and computers running Skype for Business Server."
---

# Test-CsManagementServer
 
Verifies that the Central Management service is working correctly. The Central Management service is responsible for replicating data between the Central Management store and computers running Skype for Business Server.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Test-CsManagementServer [-Report <String>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 tests the Central Management service. Because there can only be a single instance of this service, no additional parameters are required.
  
```
Test-CsManagementServer
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Central Management service is responsible for replicating data between the Central Management store and computers running Skype for Business Server. The Central Management service runs on a single Front End pool (or a single Standard Edition server) and facilitates replication throughout the Skype for Business Server infrastructure. The Test-CsManagementServer cmdlet enables you verify that the Management service is working correctly.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\ManagementServerTestTest.html"` <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The test-CsManagementServer cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The Test-CsManagementServer cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsManagementServer](set-csmanagementserver.md)

