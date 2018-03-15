---
title: "Set-CsUserServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f4dd845a-5c78-4455-93eb-722b603ff154
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsUserServer
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to modify an existing User Services pool. Among other things, the User Services pool provides presence information and helps to manage conferences. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsUserServer [-Identity <XdsGlobalRelativeIdentity>] [-ConfDirManagementWcfTcpPort <UInt16>] [-ConferenceServer <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-McuFactorySipPort <UInt16>] [-UserDatabase <String>] [-UserPinManagementWcfHttpPort <UInt16>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 changes the McuFactorySipPort for a single User Services pool: the pool with the Identity UserServer:atl-cs-001.litwareinc.com. In this example, the port is changed to 445.
  
```
Set-CsUserServer -Identity "UserServer:atl-cs-001.litwareinc.com" -McuFactorySipPort 445
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the McuFactorySipPort is modified for all the User Services pools in the organization. To do this, the command starts off by using the **Get-CsService** cmdlet and the UserServer parameter to return a collection of all the User Services pool currently in use. This collection is then piped to the **ForEach-Object** cmdlet, which takes each pool in the collection and sets the McuFactorySipPort to 445. The data must be piped to the **ForEach-Object** cmdlet because the **Set-CsUserServer** cmdlet cannot accept pipelined data itself. 
  
```
Get-CsService -UserServer | ForEach-Object {Set-CsUserServer -Identity $_.Identity -McuFactorySipPort 445}
```

## Detailed Description
<a name="sectionSection1"> </a>

User Services is a catch-all component that performs a number of key Lync Server roles; for example, User Services provides presence information; helps to manage conferences (through the Focus and Focus Factory); handles user authorization and user-level routing; and serves as the primary interface to the back-end database. User Services also assists with provisioning user accounts.
  
Because of this, it is important for administrators to know exactly how their User Services pools have been configured and, if necessary, to modify those configurations. You can retrieve information about your User Services pools by using this command:
  
Get-CsService -UserServer
  
Likewise, you can use the **Set-CsUserServer** cmdlet to make changes to any of these pools. The **Set-CsUserServer** cmdlet enables administrators to change the user database and/or the conferencing server associated with a pool. The cmdlet also lets you modify the port used for connections to the Focus Factory. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsUserServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsUserServer"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ConfDirManagementWcfTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Windows Communication Foundation (WCF) port used for managing conference directories. The default value is 9001.  <br/> |
| _ConferenceServer_ <br/> |Optional  <br/> |System.String  <br/> |Service ID for the conferencing server associated with the User Services pool. For example: -ConferenceServer "ConferenceServer:atl-cs-001.litwareinc.com".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the User Services pool to be modified. For example: -Identity "UserServer:atl-cs-001.litwareinc.com".  <br/> Note that you can leave off the prefix "UserServer:" when specifying a User server. For example: -Identity "atl-cs-001.litwareinc.com".  <br/> |
| _McuFactorySipPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for connecting to the Focus Factory (McuFactory). The Focus Factory allocates media control units (MCUs) in order to add specific media types such as audio to conferences.  <br/> |
| _UserDatabase_ <br/> |Optional  <br/> |System.String  <br/> |Service ID for the user database associated with the User Services pool. For example: -UserDatabase "UserDatabase:atl-cs-001.litwareinc.com".  <br/> |
| _UserPinManagementWcfHttpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used by Windows Communication Foundation (WCF) when managed user PINs. The default value is 443.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsUserServer** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsUserServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayUserServer object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsService](get-csservice.md)

