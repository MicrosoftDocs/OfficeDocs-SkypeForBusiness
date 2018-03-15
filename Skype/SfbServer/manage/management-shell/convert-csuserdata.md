---
title: "Convert-CsUserData"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e52f8037-19f3-49c9-8dfc-79b0c27d8b94
description: "Converts exported user data to the data format used by either Microsoft Lync Server 2010 or Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013."
---

# Convert-CsUserData
 
Converts exported user data to the data format used by either Microsoft Lync Server 2010 or Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2013.
  
```
Convert-CsUserData -InputFile <String> -OutputFile <String> -TargetVersion <Lync2010 | Current> [-ConfDirectoryFilter <String>] [-Force <SwitchParameter>] [-UserFilter <String>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 converts the user data stored in the file C:\Logs\Lync2013Data.zip to the user data format used in Lync Server 2010. The converted data is stored in the XML file C:\Logs\Lync2010Data.xml.
  
```
Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010Data.xml" -TargetVersion Lync2010
```

### Example 2

Example 2 shows how you can convert data for a single user; in this example, the user with the SIP address kenmyer@litwareinc.com. This is done by including the UserFilter parameter followed by the user's SIP address (minus the sip: prefix).
  
```
Convert-CsUserData -InputFile "C:\Logs\Lync2013Data.Zip" -OutputFile "C:\Logs\Lync2010data.xml" -TargetVersion Lync2010 -UserFilter "kenmyer@litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Convert-CsUserData** cmdlet takes data exported by using the [Export-CsUserData](export-csuserdata.md) cmdlet and then converts that data to the user data format used by either Microsoft Lync Server 2010 or Skype for Business Server 2015. In turn, that enables the **Import-CsUserData** cmdlet to import that data to the appropriate server version.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Convert-CsUserData** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _InputFile_ <br/> |Required  <br/> |System.String  <br/> |Full path to the .ZIP file or .XML file containing the user data to be converted. For example:  <br/>  `-InputFile "C:\Data\Lync2010.zip"` <br/> |
| _OutputFile_ <br/> |Required  <br/> |System.String  <br/> |Full path to the file that will store the converted data. If you are outputting the data using the Microsoft Lync Server 2010 format then the output file must use a .XML file extension; for example:  <br/>  `-OutputFile "C:\Data\ConvertedLync2010Data.xml"` <br/> If you are using the Skype for Business Server 2015 format, the output file must use a .ZIP file extension:  <br/>  `-OutputFile "C:\Data\ConvertedLyncData.zip"` <br/> |
| _TargetVersion_ <br/> |Required  <br/> |Microsoft.Rtc.Management.BlobStore.Cmdlets.ConvertTarget  <br/> |Indicates the format for the converted data. Allowed values are:  <br/> Lync2010  <br/> Current  <br/> |
| _ConfDirectoryFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to convert conference directory data. To do this, include the ConfDirectoryFilter parameter and specify the Identity of the conference directory:  <br/>  `-ConfDirectoryFilter 13` <br/> You can retrieve conference directory Identities by using this command:  <br/>  `Get-CsConferenceDirectory | Select-Object Identity, ServiceId` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _UserFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to convert data for a single user. That user specified by using his or her SIP address, minus the sip: prefix. For example:  <br/>  `-UserFilter "kenmyer@litwareinc.com"` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Convert-CsUserData** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Convert-CsUserData** cmdlet creates either XML or ZIP files, depending on whether the converted data is to be used with Lync Server 2010 or with Skype for Business Server 2015.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Export-CsUserData](export-csuserdata.md)
  
[Import-CsUserData](import-csuserdata.md)
  
[Sync-CsUserData](sync-csuserdata.md)
  
[Update-CsUserData](update-csuserdata.md)

