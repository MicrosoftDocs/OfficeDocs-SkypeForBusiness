---
title: "Export-CsUserData"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 52c411e1-76da-48b8-b1e3-ddc7c7f86e3d
description: "Exports user data in a format that can be imported into Skype for Business Server 2015. The data will be exported as a .ZIP file containing a pair of XML documents. This cmdlet was introduced in Lync Server 2013."
---

# Export-CsUserData
 
Exports user data in a format that can be imported into Skype for Business Server 2015. The data will be exported as a .ZIP file containing a pair of XML documents. This cmdlet was introduced in Lync Server 2013.
  
```
Export-CsUserData -SqlInstanceName <String> [-DbName <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 exports user data from the pool atl-cs-001.litwareinc.com to a file named C:\Logs\ExportedUserData.zip.
  
```
Export-CsUserData -PoolFqdn "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Export-CsUserData** cmdlet provides a way for administrators to export user data and/or conference directory for a Skype for Business Server 2015 pool. That data, which can be saved in the user data format used by either Skype for Business Server 2015 or Microsoft Lync Server 2010 can then be imported by using the [Import-CsUserData](import-csuserdata.md) cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Export-CsUserData** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |Full path to the .ZIP file that the **Export-CsUserData** cmdlet will create; this file will contain the exported user data. For example: <br/>  `-FileName "C:\Logs\ExportedData.zip"` <br/> |
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the pool where the User database containing the user data to be exported is installed. For example:  <br/>  `-Identity "atl-sql-001.litwareinc.com"` <br/> Note that you can retrieve fully qualified domain names for your User database pools by running this command:  <br/>  `Get-CsService -UserDatabase` <br/> |
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the Registrar pool containing the user data to be exported. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _SqlInstanceName_ <br/> |Required  <br/> |System.String  <br/> |Name of the SQL Server instance containing the user data to be exported. For example:  <br/>  `-SqlInstanceName "rtc"` <br/> |
| _ConfDirectoryFilter_ <br/> |Optional  <br/> |System.String  <br/> |When specified, allows you to export conference directory information for the specified conference directory. For example, to export data from the conference directory with the ID 13 use this syntax:  <br/>  `-ConfDirectoryFilter 13` <br/> You can return conference directory IDs by using this command:  <br/>  `Get-CsConferenceDirectory` <br/> |
| _DbName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the SQL Server database containing the user data to be exported.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the FQDN of the domain controller to be used when running the **Export-CsUserData** cmdlet. If not specified, the cmdlet will use the first available domain controller. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _LegacyFormat_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, data is saved in the format used by Microsoft Lync Server 2010.  <br/> |
| _UserFileFilter_ <br/> |Optional  <br/> |System.String  <br/> |Full path to a text file containing a list of user URIs for whom data should be exported.  <br/> |
| _UserFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to export data for a single user. That user is in dictated by specifying his or her SIP address, minus the sip: prefix. For example:  <br/>  `-UserFilter "kenmyer@litwareinc.com"` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Export-CsUserData** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Export-CsUserData** cmdlet creates new .ZIP files.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Convert-CsUserData](convert-csuserdata.md)
  
[Import-CsUserData](import-csuserdata.md)
  
[Sync-CsUserData](sync-csuserdata.md)
  
[Update-CsUserData](update-csuserdata.md)

