---
title: "Get-CsAdServerSchema"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fba777e5-886c-4914-a492-f2237721c57c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAdServerSchema
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information indicating whether your Active Directory schema has been correctly configured to allow for the installation of Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdServerSchema [-Report <String>]
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

Lync Server cannot be installed until your Active Directory schema has been properly extended; that means that objects and attributes specific to Lync Server must be added to Active Directory Domain Services before installation can take place. For example, user account objects must be modified to allow for attributes that do such things as indicate the voice policy assigned to a user or report whether or not that account has been enabled for Enterprise Voice.
  
The **Get-CsAdServerSchema** cmdlet returns a single value that tells you whether or not Active Directory has been extended and is prepared for the installation of Lync Server. If the **Get-CsAdServerSchema** cmdlet returns the value SCHEMA_VERSION_STATE_CURRENT, the schema has been extended. If the cmdlet returns any other value, then the schema has not been extended. 
  
The **Get-CsAdServerSchema** cmdlet typically runs as part of the Setup Wizard; if Setup determines that the schema is not correctly prepared, you will receive an error message and Setup will stop. However, you can also run the **Get-CsAdServerSchema** cmdlet independently of the Setup Wizard, giving you the opportunity to verify the schema status before you try to install Lync Server. 
  
The **Get-CsAdServerSchema** cmdlet performs the same function as the following Microsoft Office Communications Server 2007 R2 command: Lcscmd.exe /domain /action:CheckSchemaPrepState. 
  
Who can run this cmdlet: By default, any user who has read permissions to Active Directory can run the **Get-CsAdServerSchema** cmdlet locally. Typically all domain members have this permission. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\SchemaPrep.html"  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsAdServerSchema** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsAdServerSchema** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.SchemaVersionState object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Install-CsAdServerSchema](install-csadserverschema.md)

