---
title: "Set-CsUserDatabaseState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c4d8fe5e-ebc1-443b-943d-fc54649e94fd
description: "Enables or disables one or more Skype for Business Server 2015 user databases. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsUserDatabaseState
[]
Enables or disables one or more Skype for Business Server 2015 user databases. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsUserDatabaseState -RegistrarPool <Fqdn> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 takes the user database UserDatabase:atl-sql-001.litwareinc.com offline. This is done by setting the Online property to $False.
  
```
Set-CsUserDatabaseState -Identity "UserDatabase:atl-sql-001.litwareinc.com" -Online $False
```

### EXAMPLE 2

In Example 2, all the user databases on the Registrar pool atl-cs-001.litwareinc.com are taken offline.
  
```
Set-CsUserDatabaseState -RegistrarPool atl-cs-001.litwareinc.com -Online $False
```

### EXAMPLE 3

Example 3 locates all the user databases that are currently offline and then brings them back online. To do this, the command first calls the **Get-CsUserDatabaseState** cmdlet without any parameters in order to return a collection of all the user databases in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those databases where the Online property is equal to False. The filtered collection is then piped to the **ForEach-Object** cmdlet, which takes each database in the collection and sets the Online property to True. Note that the collection of offline databases must be piped to the **ForEach-Object** cmdlet rather than the **Set-CsUserDatabaseState** cmdlet. That is because the latter cmdlet cannot directly accept pipelined information.
  
```
Get-CsUserDatabaseState | Where-Object {$_.Online -eq $False} | ForEach-Object {Set-CsUserDatabaseState -Identity $_.Identity -Online $True}
```

## Detailed Description

Skype for Business Server 2015 employs the user database (also known as the user store) to maintain presence and routing information for Skype for Business Server 2015 users. The **Set-CsUserDatabaseState** cmdlet provides a way for you change the state of one or more user databases: you can use the cmdlet to take a database offline or to bring a disabled database back online.
  
Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Skype for Business Server 2015. In turn, that means that you will not be able to run the **Set-CsUserDatabaseState** cmdlet from a remote instance of Windows PowerShell. That's because your command will not be able to traverse the firewall and access the SQL Server Express database. You can still run the cmdlet locally (that is, on the Standard Edition server itself). However, to run the **Set-CsUserDatabaseState** cmdlet remotely you will need to manually enable the firewall exceptions for SQL Server Express.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier of the user database whose online status is to be modified. For example:  <br/>  `-Identity "UserDatabase:atl-sql-001.litwareinc.com"` <br/> You cannot use both Identity and RegistrarPool in the same command, nor can you use wildcards with either parameter.  <br/> |
| _Online_ <br/> |Required  <br/> |System.Boolean  <br/> |When set to True ($True), makes a database available online. When set to False ($False), takes a database offline.  <br/> |
| _RegistrarPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the Registrar pool hosting the user databases whose online status is to be modified. For example:  <br/>  `-RegistrarPool atl-cs-001.litwareinc.com` <br/> You cannot use both -Identity and -RegistrarPool in the same command, nor can you use wildcards with either parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

String. The **Set-CsUserDatabaseState** cmdlet accepts a string value representing the Identity of the user database to be updated.
  
## Return Types

None. Instead, the **Set-CsUserDatabaseState** cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.UserStoreState object.
  
## See also

#### 

[Get-CsUserDatabaseState](get-csuserdatabasestate.md)
  
[Update-CsUserDatabase](update-csuserdatabase.md)

