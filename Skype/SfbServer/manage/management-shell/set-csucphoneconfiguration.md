---
title: "Set-CsUCPhoneConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f77456aa-992a-47d2-bdc7-5e3cbbfb6926
description: "Enables you to modify management options for UC phones. This includes such things as the required security mode and whether or not the phone should automatically be locked after a specified period of inactivity. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsUCPhoneConfiguration
 
Enables you to modify management options for UC phones. This includes such things as the required security mode and whether or not the phone should automatically be locked after a specified period of inactivity. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsUCPhoneConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 sets the SIP security mode of the global UC phone settings to Medium. 
  
```
Set-CsUCPhoneConfiguration -Identity global -SIPSecurityMode "Medium"
```

### EXAMPLE 2

Example 2 modifies the UC phone settings configured for the Redmond site. In this case, the PhoneLockTimeout property is set to 30 minutes; this is done by including the PhoneLockTimeout parameter and the parameter value "00:30:00" (00 hours: 30 minutes: 00 seconds). 
  
```
Set-CsUCPhoneConfiguration -Identity site:Redmond -PhoneLockTimeout "00:30:00"
```

### EXAMPLE 3

Example 3 is a variation of the command shown in Example 2. This time, however, the PhoneLockTimeout property is modified for all the UC phone settings configured at the site scope. To do this, the command starts off by calling the **Get-CsUCPhoneConfiguration** cmdlet; the Filter parameter and the filter value "site:*" limit the returned data to phone settings configured at the site scope. This filtered collection is then piped to the **Set-CsUCPhoneConfiguration** cmdlet, which uses the PhoneLockTimeout parameter and the parameter value "00:30:00" (00 hours: 30 minutes: 00 seconds) to set the phone lock timeout value for each item in the collection to 30 minutes.
  
```
Get-CsUCPhoneConfiguration -Filter "site:*" | Set-CsUCPhoneConfiguration -PhoneLockTimeout "00:30:00"
```

### EXAMPLE 4

Example 4 configures the EnforcePhoneLock and the PhoneLockTimeout properties for all the UC phone settings where the SIP security mode is set to either Low or Medium. To perform this task, the command first uses the **Get-CsUCPhoneConfiguration** cmdlet to return all the UC phone configuration settings in the organization; this information is then piped to the **Where-Object** cmdlet, which picks out only those settings where the SIPSecurityMode property is not equal to High. (Because SIP security can only be set to Low, Medium, or High, this clause will select all the settings where SIPSecurityMode is set to either Low or Medium.) The filtered collection is then piped to the **Set-CsUCPhoneConfiguration** cmdlet, which uses the EnforcePhoneLock and the PhoneLockTimeout parameters to modify the phone locking and phone lock timeout properties.
  
```
Get-CsUCPhoneConfiguration | Where-Object {$_.SIPSecurityMode -ne "High"} | Set-CsUCPhoneConfiguration -EnforcePhoneLock $True -PhoneLockTimeout "00:30:00"
```

### EXAMPLE 5

In Example 5, the phone lock timeout value is set to 10 minutes for all the UC phone settings where the PhoneLockTimeout property is currently less than 10 minutes. (In effect, this makes 10 minutes the minimum phone lock timeout for the entire organization.) To do this, the command first uses the **Get-CsUCPhoneConfiguration** cmdlet to return a collection of all the UC phone settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the PhoneLockTimeout property is less than 10 minutes (00 hours: 10 minutes: 00 seconds). In turn, the filtered collection is piped to the **Set-CsUCPhoneConfiguration** cmdlet, which sets the PhoneLockTimeout value for each item in the collection to 10 minutes.
  
```
Get-CsUCPhoneConfiguration | Where-Object {$_.PhoneLockTimeout -lt "00:10:00"} | Set-CsUCPhoneConfiguration -PhoneLockTimeout "00:10:00"
```

## Detailed Description

UC phones represent the merging of the telephone and Skype for Business Server 2015. UC phones use special hardware (that is, a Skype for Business-compatible telephone) that can function as a Voice over Internet Protocol (VoIP) telephone. In addition, this hardware can also act as a Skype for Business-like endpoint: you can set your current status; check the status of your Skype for Business contacts; search for new contacts; and carry out many of the other activities you are used to doing with Skype for Business. 
  
The **CsUCPhoneConfiguration** cmdlets enable you to use configuration settings to manage phones running Skype for Business. For example, you can control such things as the minimum length of the personal identification number (PIN) used to log on to the phone and whether or not the phone will automatically lock itself after a specified period of inactivity.
  
Unified communications (UC) phone configuration settings can be applied at either the global scope or at the site scope. When you first install Skype for Business Server 2015, a single set of UC phone configuration settings is created and applied at the global scope. However, at any time after that you can use the **New-CsUCPhoneConfiguration** cmdlet to create a collection of settings that are applied at the site scope. This lets you tailor UC phone management to the unique needs of each individual site.
  
In addition to creating new collections of UC phone settings, you can use the **Set-CsUCPhoneConfiguration** cmdlet to modify the property values of an existing collection. For example, by default logging is disabled for UC phones. To enable logging at the global level, you can use the **Set-CsUCPhoneConfiguration** cmdlet to change the value of the global collection's LoggingLevel property to True.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CalendarPollInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Indicates how often the UC device retrieves information from your Outlook calendar. The value must be specified using the format hours:minutes:seconds; for example, to set the time interval to 1 hour (the maximum allowed interval) use this syntax: -CalendarPollInterval "01:00:00". The default value is 3 minutes (00:03:00).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnforcePhoneLock_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether or not UC phones are automatically locked after the number of minutes specified by PhoneLockTimeout. The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Represents the unique identifier assigned to the collection of UC phone configuration settings. To refer to the global settings, use this syntax:  <br/>  `-Identity global` <br/> To refer to a collection configured at the site scope use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> Note that you cannot use wildcard characters when specifying an Identity.  <br/> If this parameter is omitted, then the **Set-CsUCPhoneConfiguration** cmdlet will modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |UcPhoneSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _LoggingLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LoggingLevel  <br/> |Enables logging on the UC device. Valid values are Off; Low; Medium; and High. The default value is Off.  <br/> |
| _MinPhonePinLength_ <br/> |Optional  <br/> |System.Byte  <br/> |Specifies the minimum number of digits required for personal identification numbers (PINs).  <br/> Minimum value: 4  <br/> Maximum value: 15  <br/> Default: 6  <br/> |
| _PhoneLockTimeout_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the length of time, in minutes, that a UC phone will remain idle before automatically locking.  <br/> This value must be less than 01:00:00 (1 hour). The default value is 00:10:00 (10 minutes).  <br/> |
| _SIPSecurityMode_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Voice.SIPSecurityMode  <br/> |Specifies the level of security that the server applies to SIP sessions initiated by a UC phone.  <br/> Valid values are:  <br/> Low (allow any type of authorization or transport).  <br/> Medium (NTLM or Kerberos is required for user authentication).  <br/> High (NTLM or Kerberos is required for user authentication and TLS is required for SIP connections).  <br/> The default value is High.  <br/> |
| _Voice8021p_ <br/> |Optional  <br/> |System.Byte  <br/> |Specifies the user priority value (the 802.1p value) for voice traffic within the Skype for Business Server 2015 deployment.  <br/> This setting is effective only for networks in which switches and bridges are 802.1p-capable. The minimum value for this property is 0 and the maximum value is 7. The default value is 0.  <br/> |
| _VoiceDiffServTag_ <br/> |Optional  <br/> |System.Byte  <br/> |Specifies the decimal representation of the 6-bit DiffServ Code Point (DSCP) priority marking. This marking defines the Per Hop Behavior (PHB) for IP packets passed by the UC phones that are managed by this server.  <br/> This value must be between 0 and 63, inclusive. The default value is 40.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings object. The **Set-CsUCPhoneConfiguration** cmdlet accepts pipelined instances of the UC phone settings object.
  
## Return Types

The **Set-CsUCPhoneConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings object.
  
## See also

#### 

[Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)
  
[New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)
  
[Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)

