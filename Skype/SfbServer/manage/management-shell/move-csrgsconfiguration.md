---
title: "Move-CsRgsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 8/5/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 983eadb8-baee-41ba-bba4-2f2b01471250
description: "Enables you to migrate Response Group configuration settings from Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server 2010 to Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Move-CsRgsConfiguration
 
Enables you to migrate Response Group configuration settings from Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server 2010 to Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Move-CsRgsConfiguration -Destination <String> -Source <String> [-Force <SwitchParameter>] [-ResolveNameConflicts <SwitchParameter>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 migrates the Response Group application from atl-ocsrgs-001.litwareinc.com to redmond-lyncrgs-001.litwareinc.com.
  
```
Move-CsRgsConfiguration -Source atl-ocsrgs-001.litwareinc.com -Destination redmond-lyncrgs-001.litwareinc.com 
```

## Detailed Description

The Response Group application provides a way for you to automatically route phone calls to entities such as a help desk or customer support line. When someone calls a designated phone number, that call can be automatically routed to the appropriate set of Response Group agents. Alternatively, the call might be routed to an interactive voice response (IVR) queue. In that queue, the caller would be asked a series of questions (for example, "Are you calling about an existing order?") and then, based on the answers to those questions, be given the asked-for information or be routed to a Response Group agent.
  
If you are currently running the Response Group application on Office Communications Server 2007 R2 or on Lync Server 2010, the **Move-CsRgsConfiguration** cmdlet provides a way for you to migrate this service to Skype for Business Server 2015. To migrate the service, you need to call the **Move-CsRgsConfiguration** cmdlet and specify: 1) the fully qualified domain name (FQDN) for the existing version of the Response Group application (the Source); and, 2) the FQDN for the new Skype for Business Server 2015 version of the service (the Destination). **Move-CsRgsConfiguration** will then move all the configuration settings, audio files, and contact objects from the existing version (either Office Communications Server 2007 R2 or Lync Server 2010) to Skype for Business Server 2015. After the service has been migrated, all calls to a Response Group phone number will be handled by Skype for Business Server 2015. Calls will no longer be handled by the previous version of the service.
  
Before you can run **Move-CsRgsConfiguration**, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. The file OCSWMIBC.msi can be found on the installation DVD in the Setup folder.
  
If Office Communications Server 2007 is running Microsoft SQL Server 2005 then, before you attempt to migrate the Response Group application, you must install the Microsoft SQL Server 2005 Native Client on the computer where you will be running the **Move-CsRgsConfiguration** cmdlet. If the Native Client is not installed you will receive the error message "Cannot access WMI settings" when you call **Move-CsRgsConfiguration**.
  
The **Move-CsRgsConfiguration** cmdlet is only for migrating from Office Communications Server 2007 R2 or Lync Server 2010 to Skype for Business Server 2015; you cannot use this cmdlet to migrate from one instance of Skype for Business Server 2015 to a new instance of Skype for Business Server 2015. That type of migration can only be done by using the new **Import-CsRgsConfiguration** and **Export-CsRgsConfiguration** cmdlets.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Destination_ <br/> |Required  <br/> |System.String  <br/> |FQDN of the computer where the Skype for Business Server Response Group application is to be hosted (the "copy to" location).  <br/> |
| _Source_ <br/> |Required  <br/> |System.String  <br/> |FQDN of the pool where the Office Communications Server 2007 R2 or Lync Server 2010Response Group application is currently hosted (the "copy from" location).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _ResolveNameConflicts_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   
## Input Types

None. **Move-CsRgsConfiguration** does not accept pipelined input.
  
## Return Types

 **Move-CsRgsConfiguration** moves instances of the Microsoft.Rtc.Management.WritableSettings.ServiceSettings from one service to another.
  
## See also

#### 

[Get-CsRgsConfiguration](get-csrgsconfiguration.md)
  
[Move-CsRgsConfiguration](move-csrgsconfiguration.md)

