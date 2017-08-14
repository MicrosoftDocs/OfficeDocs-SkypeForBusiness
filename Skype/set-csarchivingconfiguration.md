---
title: Set-CsArchivingConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: f5202dc2-b3b4-48ae-93d2-d19e71847994
---


# Set-CsArchivingConfiguration
[]
Modifies an existing collection of instant messaging (IM) archiving settings. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsArchivingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the **Set-CsArchivingConfiguration** cmdlet is used to modify two properties of the archiving configuration settings that have the Identity site:Redmond. First, the command sets the ArchiveDuplicateMessages property to False; this prevents the server from archiving the same instant message session multiple times. The command also uses the KeepArchivingDataForDays parameter to instruct the server to keep instant messages for 30 days.
  
    
    

```

Set-CsArchivingConfiguration -Identity site:Redmond -ArchiveDuplicateMessages $False -KeepArchivingDataForDays 30
```


### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1: in this case, however, the values of the ArchiveDuplicateMessages and KeepArchivingDataForDays properties are modified for all the archiving settings that have been configured at the site scope. To carry out this task, the command first uses the **Get-CsArchivingConfiguration** cmdlet and the Filter parameter to return a collection of all the archiving settings configured at the site scope; the filter value "site:*" ensures that only settings that have an Identity that begins with the characters "site:" are returned. The filtered collection is then piped to the **Set-CsArchivingConfiguration** cmdlet, which modifies the two property values for each item in the collection.
  
    
    

```
Get-CsArchivingConfiguration -Filter "site:*" | Set-CsArchivingConfiguration -ArchiveDuplicateMessages $False -KeepArchivingDataForDays 30
```


### EXAMPLE 3

In Example 3, all of the archiving configuration settings that allow both IM session and web conferencing archiving are modified; after the command completes, those settings will allow only for IM session archiving. To do this, the command first calls the **Get-CsArchivingConfiguration** cmdlet without any parameters in order to return a collection of all the archiving configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the EnableArchiving property is equal to (-eq) "ImAndWebConf". The filtered collection is then piped to the **Set-CsArchivingConfiguration** cmdlet, which takes each item in the collection and changes the value of EnableArchiving to "ImOnly".
  
    
    

```
Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -eq "ImAndWebConf"} | Set-CsArchivingConfiguration -EnableArchiving "ImOnly"
```


## Detailed Description

Many organizations find it useful to keep a transcript of all the IM sessions and conferences their users participate in. For other organizations, it's mandatory to keep such transcripts; for example, many organizations in the financial world are required by law to keep copies of all their electronic communications.
  
    
    
In order to archive instant messages, you must set up at least one Archiving Server. After the Archiving Server is set up, you must perform two additional steps. First, you need to enable archiving at the global scope (for details, see the **Set-CsArchivingConfiguration** cmdlet help topic). Optionally, you can also configure custom archiving settings for different sites.
  
    
    
Second, you must use archiving policies to indicate which users will have their IM sessions archived. IM sessions will not be archived unless a policy is in force that requires IM sessions to be archived. 
  
    
    
When you install Skype for Business Server 2015, a collection of global archiving configuration settings will be created for you; by default, these settings will apply to your entire organization. Alternatively, you can use the **New-CsArchivingConfiguration** cmdlet to create custom configuration settings on a site-by-site basis. Either way, you can use the **Set-CsArchivingConfiguration** cmdlet to modify the property values of an existing collection or archiving configuration settings.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ArchiveDuplicateMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies how "cross-pool" instant messages should be archived. Consider a simple example: Ken Myer (with an account in Pool 1) sends an instant message to Pilar Ackerman, who has an account in Pool 2. Pilar, in turn, sends a reply to Ken's instant message. If ArchiveDuplicateMessages is set to False, then (based on a built-in algorithm) the session transcript will be logged in either Pool 1 or Pool 2, but not both. If ArchiveDuplicateMessages is set to True (the default value), the transcript will be logged in both pools.  <br/> |
| _BlockOnArchiveFailure_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, then the IM service will be suspended any time instant messages cannot be archived. If set to False (the default value), IM will continue even if instant messages cannot be archived.  <br/> |
| _CachePurgingInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates how often (in hours) the system is purged of transcripts where none of the participants have been enabled for archiving. By design, all group IM sessions and conferencing sessions are recorded when they take place. At the specified interval, the system determines whether any of the participants in these sessions have been enabled for archiving. If the system finds a session where none of the participants have been enabled for archiving, then that transcript will be deleted from the database.  <br/> The CachePurgingInterval property can be set to any integer value between 4 and 168, inclusive. The default value is 24.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableArchiving_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.EnableArchiving  <br/> |Indicates which items (if any) are saved to the archiving database. Valid values are:  <br/> None. No items are archived to the database. This is the default value.  <br/> ImOnly. IM sessions are archived to the database.  <br/> ImAndWebConf. Both IM and web conferencing sessions are archived to the database.  <br/> |
| _EnableExchangeArchiving_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Skype for Business Server 2015 instant message and conferencing transcripts are stored in Exchange rather than a separate SQL Server database. Note that if you enable Exchange archiving then users will be managed by the Exchange archiving policies instead of Skype for Business Server 2015 archiving policies.  <br/> The default value is False.  <br/> |
| _EnablePurging_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, then archived instant messages will periodically be removed from the database, provided that these instant messages: 1) are older than the value specified in the KeepArchivingDataForDays property; or, 2) have been exported and marked for deletion.  <br/> If False, instant messages will not automatically be deleted from the database.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Represents the unique identifier of the collection of archiving configuration settings to be modified. To modify the global settings, either leave out this parameter or use the following syntax:  `-Identity global`. To modify settings at the site scope, use the prefix "site:" followed by the site name. For example:  `-Identity "site:Redmond"`.  <br/> To modify settings assigned to an individual Registrar pool use syntax similar to this:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> |
| _Instance_ <br/> |Optional  <br/> |ArchivingSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _KeepArchivingDataForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |Number of days (between 1 and 2562) that archived instant messages are kept in the database before being automatically deleted. The default value is 14.  <br/> This property takes effect only if EnablePurging has been set to True.  <br/> |
| _PurgeExportedArchivesOnly_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, then the system will only purge instant messages that have been exported (and, as a result, have been marked for deletion). Instant messages that have not been exported will remain in the database, even if those instant messages are older than the value specified by the KeepArchivingDataForDays property.  <br/> |
| _PurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the time of day when expired records are deleted from the archiving database. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 AM) and 23 representing 11:00 PM. Note that you can only specify the hour of the day. This means that you can schedule purging to take place at 4:00 AM but you cannot schedule it to take place at, for instance, 4:30 AM or 4:15 AM. The default value is 2 (2:00 AM).  <br/> Database purging takes place only if the EnablePurging property is set to True.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _PurgeMinuteOfPurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _PurgeTaskWakeupIntervalMinutes_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _UseV2PurgingAlgorithm_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _V2PurgeMaxDegreeOfParallelism_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _V2PurgeMaxRetries_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _V2PurgeReportingIntervalMinutes_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _V2PurgeTimeoutMinutes_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings object. The **Set-CsArchivingConfiguration** cmdlet accepts pipelined input of archiving configuration objects.
  
    
    

## Return Types

The **Set-CsArchivingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)
  
    
    
 [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)
  
    
    
 [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)
  
    
    
 [Set-CsArchivingServer](set-csarchivingserver.md)
