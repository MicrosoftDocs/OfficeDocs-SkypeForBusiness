---
title: "Import-CsUserData"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f39ef951-ee5b-4200-b6fb-68a4d4d6e86f
description: "Imports user data previously exported by using the Export-CsUserData cmdlet. This cmdlet was introduced in Lync Server 2013."
---

# Import-CsUserData
[]
Imports user data previously exported by using the Export-CsUserData cmdlet. This cmdlet was introduced in Lync Server 2013.
  
> [!NOTE]
> You must restart the Front End service on all servers within the pool to see the results of this command. 
  
```
Import-CsUserData -PoolFqdn <Fqdn> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 imports user data from a file named C:\Logs\ExportedUserData.zip to the pool atl-cs-001.litwareinc.com.
  
```
Import-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Import-CsUserData cmdlet is used to import previously-saved user data and/or conference directory data to Skype for Business Server 2015. Note that this data must have been exported by using the [Export-CsUserData](export-csuserdata.md) cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Import-CsUserData** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Full path to the input file containing the exported user data. For example:  <br/>  `-InputFile "C:\Data\ExportedUsers.xml"` <br/> |
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Service Identity of the user database where the data should be imported. For example:  <br/>  `-Identity "UserDatabase:atl-sql-001.litwareinc.com"` <br/> You cannot use both the Identity and the PoolFqdn parameters in the same command.  <br/> |
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the Registrar pool for the user data being imported. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _ConfDirectoryFilter_ <br/> |Optional  <br/> |System.String  <br/> |When specified, allows you to import conference directory information for the specified conference directory. For example, to import data from the conference directory with the ID 13 use this syntax:  <br/>  `-ConfDirectoryFilter 13` <br/> You can return conference directory IDs by using this command:  <br/>  `Get-CsConferenceDirectory` <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running the **Import-CsUserData** cmdlet. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _LegacyFormat_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that the data to be imported was exported from a previous version of Lync Server or Office Communications Server.  <br/> |
| _RoutingGroupFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the imported data to users who belong to the same routing group. Routing groups are used by Skype for Business Server 2015 to determine the Front End server that users register with.  <br/> |
| _UserFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to import user data for a single user. To convert data for a specified user (and only for that user), set the UserFilter parameter to the SIP address of that user, being sure to omit the sip: prefix. For example:  <br/>  `-UserFilter "kenmyer@litwareinc.com"` <br/> This parameter allows you to import data one user at a time.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Import-CsUserData** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Convert-CsUserData](convert-csuserdata.md)
  
[Export-CsUserData](export-csuserdata.md)
  
[Sync-CsUserData](sync-csuserdata.md)
  
[Update-CsUserData](update-csuserdata.md)

