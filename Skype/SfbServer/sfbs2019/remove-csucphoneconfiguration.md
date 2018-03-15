---
title: "Remove-CsUCPhoneConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1b2d9601-3206-48d9-a846-4486b606aad0
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsUCPhoneConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified collection of Lync Phone Edition configuration settings. These settings include such things as the required security mode and whether the phone should automatically be locked after a specified period of inactivity. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUCPhoneConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 removes the UC phone configuration settings for the Redmond site (-Identity site:Redmond). When settings are removed from a site scope, users in that site will have their UC phones governed by the global phone configuration settings.
  
```
Remove-CsUCPhoneConfiguration -Identity site:Redmond
```

### EXAMPLE 2

Example 2 removes all the UC phone settings that have been configured at the site scope. To do this, the command first uses the **Get-CsUCPhoneConfiguration** cmdlet and the Filter parameter to return all the settings configured at the site scope; the filter value "site:*" limits the returned data to settings where the Identity property (the only property you can filter on) begins with the string value "site:". This filtered collection is then piped to the **Remove-CsUCPhoneConfiguration** cmdlet, which removes each item in the collection. 
  
```
Get-CsUCPhoneConfiguration -Filter site:* | Remove-CsUCPhoneConfiguration
```

### EXAMPLE 3

In Example 3, all the UC phone settings that do not enforce phone locking are removed. To carry out this task, the command first uses the **Get-CsUCPhoneConfiguration** cmdlet without any parameters in order to return a collection of all the UC phone settings currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which picks out only those settings where the EnforceLockProperty is equal to False. In turn, that filtered collection is piped to the **Remove-CsUCPhoneConfiguration** cmdlet, which removes each item in the collection. 
  
```
Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration
```

### EXAMPLE 4

Example 4 deletes all the UC phone configuration settings where the SIP security mode is set to either Low or Medium. To do this, the **Get-CsUCPhoneConfiguration** cmdlet is first called in order to return a collection of all the UC phone settings configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the SIPSecurityMode property is set to either Low or Medium; this is done by selecting those settings where the SIPSecurityMode is not equal to High. (There are three possible values for SIPSecurityMode: Low, Medium, and High.) The filtered collection is then piped to the **Remove-CsUCPhoneConfiguration** cmdlet, which deletes all the settings where SIPSecurityMode is not equal to High. 
  
```
Get-CsUCPhoneConfiguration | Where-Object {$_.SIPSecurityMode -ne "High"} | Remove-CsUCPhoneConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Phone Edition represents the merging of the telephone and Lync Server. Lync Phone Edition uses special hardware (that is, a Lync-compatible telephone) that can function as a Voice over Internet Protocol (VoIP) telephone. In addition, this hardware can also act as a Lync-like endpoint: you can set your current status; check the status of your Lync contacts; search for new contacts; and carry out many of the other activities you are used to doing with Lync. 
  
Lync Server ships with a number of cmdlets that enable you to manage phones running Lync Phone Edition; for example, you can control such things as the minimum length of the personal identification number (PIN) used to log on to the phone and whether or not the phone will automatically lock itself after a specified period of inactivity.
  
Unified communications (UC) phone configuration settings can be applied at either the global scope or at the site scope. (Settings applied at the site scope take precedence over settings applied at the global scope.) When you first install Lync Server, a single set of UC phone configuration settings is created and applied at the global scope. However, at any time after that you can use the **New-CsUCPhoneConfiguration** cmdlet to create a collection of settings applied at the site scope. This lets you tailor UC phone management to the unique needs of each individual site. 
  
Settings created by using the **New-CsUCPhoneConfiguration** cmdlet can later be removed by using the **Remove-CsUCPhoneConfiguration** cmdlet. When you remove settings from a site the phones running Lync Phone Edition in that site are not left unmanaged; instead, those phones will automatically come under the jurisdiction of the global settings. 
  
You can also run the **Remove-CsUCPhoneConfiguration** cmdlet against the global settings. If you do that, however, the global settings will not actually be removed: you cannot remove the global UC phone settings. Instead, the properties in the global settings will be reset to their default values. For example, if you have changed the phone lock time interval to 30 minutes, "removing" the global settings will reset the interval to the default value of 10 minutes. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsUCPhoneConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsUCPhoneConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of UC phone configuration settings to be removed. To remove a site collection use syntax similar to this: -Identity "site:Redmond". To remove (reset) the global collection, use the following syntax: -Identity global. Note that you cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings object. The **Remove-CsUCPhoneConfiguration** cmdlet accepts pipelined instances of the UC phone settings object. 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the cmdlet removes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)
  
[New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)
  
[Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)

