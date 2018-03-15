---
title: "Get-CsConfigurationStoreLocation"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: abfda147-02fa-46a5-a988-d83daf4cc455
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsConfigurationStoreLocation
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Reports back the location of the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsConfigurationStoreLocation [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns the SQL Server path to the computer (or pool) hosting the Central Management store.
  
```
Get-CsConfigurationStoreLocation
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the Report parameter is included in order to specify a path for the report generated when you run the **Get-CsConfigurationStoreLocation** cmdlet. 
  
```
Get-CsConfigurationStoreLocation -Report "C:\Logs\ConfigurationStore.html"
```

## Detailed Description
<a name="sectionSection1"> </a>

Active Directory Domain Services uses service control points (SCP) to help computers locate services. For example, when you install Lync Server, a service control point is created that provides location information for the Central Management store used to maintain Lync Server data. Computers that need access to the database connect to Active Directory and use the information contained in the SCP to help them locate the correct computer and the correct instance of SQL Server.
  
The **Get-CsConfigurationStoreLocation** cmdlet is used to report back the SQL Server path (for example, atl-sql-001.litwareinc.com/rtc) to the computer running the Central Management store. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller where global settings are stored. If global settings are stored in the Active Directory System container, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\ConfigurationStore.html"  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsConfigurationStoreLocation** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

String. The **Get-CsConfigurationStoreLocation** cmdlet reports back the location of the configuration store. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)
  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

