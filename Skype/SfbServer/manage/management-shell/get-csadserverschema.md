---
title: "Get-CsAdServerSchema"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fba777e5-886c-4914-a492-f2237721c57c
description: "Returns information indicating whether your Active Directory schema has been correctly configured to allow for the installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsAdServerSchema
 
Returns information indicating whether your Active Directory schema has been correctly configured to allow for the installation of Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdServerSchema [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns the current state of the Active Directory server schema. If the schema is up to date, the command returns the following value: SCHEMA_VERSION_STATE_CURRENT.
  
```
Get-CsAdServerSchema
```

### EXAMPLE 2

Example 2 also returns the current state of the Active Directory server schema. In addition, the command writes more detailed information about that schema to a file named C:\Logs\Server_Schema.html. This information includes details such as the schema major version and minor version.
  
```
Get-CsAdServerSchema -Report C:\Logs\Server_Schema.html
```

## Detailed Description

Skype for Business Server 2015 cannot be installed until your Active Directory schema has been properly extended; that means that objects and attributes specific to Skype for Business Server 2015 must be added to Active Directory Domain Services before installation can take place. For example, user account objects must be modified to allow for attributes that do such things as indicate the voice policy assigned to a user or report whether or not that account has been enabled for Enterprise Voice.
  
The **Get-CsAdServerSchema** cmdlet returns a single value that tells you whether or not Active Directory has been extended and is prepared for the installation of Skype for Business Server 2015. If the **Get-CsAdServerSchema** cmdlet returns the value SCHEMA_VERSION_STATE_CURRENT, the schema has been extended. If the cmdlet returns any other value, then the schema has not been extended.
  
The **Get-CsAdServerSchema** cmdlet typically runs as part of the Setup Wizard; if Setup determines that the schema is not correctly prepared, you will receive an error message and Setup will stop. However, you can also run the **Get-CsAdServerSchema** cmdlet independently of the Setup Wizard, giving you the opportunity to verify the schema status before you try to install Skype for Business Server 2015.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\SchemaPrep.html"` <br/> |
   
## Input Types

None. The **Get-CsAdServerSchema** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsAdServerSchema** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.SchemaVersionState object.
  
## See also

#### 

[Install-CsAdServerSchema](install-csadserverschema.md)

