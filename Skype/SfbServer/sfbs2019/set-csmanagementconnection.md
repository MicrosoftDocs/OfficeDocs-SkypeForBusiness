---
title: "Set-CsManagementConnection"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f7cf19ba-6c56-4f74-9757-843e1ca0c9a1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsManagementConnection
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies the management connection to the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsManagementConnection -Connection <String> -StoreProvider <FileSystem | Sql | Memory> [-Confirm [<SwitchParameter>]] [-EnableCaching <$true | $false>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 changes the management connection to the SQL Server instance rtcbackup found on the computer atl-sql-001.litwareinc.com.
  
```
Set-CsManagementConnection -StoreProvider Sql -Connection "atl-sql-001.litwareinc.com\rtcbackup"
```

### EXAMPLE 2

In Example 2, the management connection is set to file system and, more specifically, to the folder C:\TestTopology on the local computer.
  
```
Set-CsManagementConnection -StoreProvider FileSystem -Connection "C:\TestTopology"
```

## Detailed Description
<a name="sectionSection1"> </a>

Configuration data for Lync Server is stored in the Central Management store. It is crucial that both Windows PowerShell and the management replica services be able to locate this database. When you install Lync Server, a service control point is created in Active Directory Domain Services that provides location information for this database. Typically, computers rely on this service control point in order to connect to the Central Management store. To see the details behind this connection (that is, if you want to know which computer the Central Management store is running on, as well information about the SQL Server connection to that Central Management store) all you have to do is run the **Get-CsManagementConnection** cmdlet. 
  
For the most part, after your management connection has been set you will not need to change it. However, in case of hardware or software failure, you might need to temporarily use a connection; for example, you can configure a computer to work from the local replica. The **Set-CsManagementConnection** cmdlet provides a way for you to provide a new location for the Central Management store. 
  
Note that any changes you make to Lync Server while using a temporary management connection will not persist if and when you switch back to your original connection. (You can switch back by running the **Remove-CsManagementConnection** cmdlet.) For example, suppose you decide to temporarily use the file system as your store provider. You change the management connection, and then create several new voice policies (each of which will be instantiated as XML files). When you switch back to your original management connection, these new voice policies will disappear because they were never recorded in the Central Management store now being used. 
  
You should also keep in mind that any changes made by running this cmdlet only affect the local computer. You cannot use the **Set-CsManagementConnection** cmdlet to change the management connection on other computers. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsManagementConnection** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Connection_ <br/> |Required  <br/> |System.String  <br/> |Location information for the SQL Server instance or the file system folder being used as the management connection.  <br/> For example, if the new management connection is to a SQL Server instance named rtcbackup on the computer atl-sql-001.litwareinc.com then use this syntax: -Connection "atl-sql-001.litwareinc.com\rtcbackup".  <br/> If you want to create a management connection to the folder C:\TestTopology then use this syntax: -Connection "C:\TestTopology". If the folder does not exist, the **Set-CsManagementConnection** cmdlet will create it.  <br/> |
| _StoreProvider_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Store.StoreProvider  <br/> |Indicates the type of back-end store used for configuration information. To store configuration data in SQL Server, set the StoreProvider like this: -StoreProvider Sql. To store configuration data to the file system, use this syntax: -StoreProvider FileSystem. You should not modify the StoreProvider property unless instructed to do so by Microsoft support personnel.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableCaching_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), caching is enabled for the management connection.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsManagementConnection** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsManagementConnection** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.Store.StoreProvider object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsManagementConnection](get-csmanagementconnection.md)
  
[Remove-CsManagementConnection](remove-csmanagementconnection.md)
  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

