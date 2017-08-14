---
title: New-CsArchivingConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 66cab8b7-c3b3-4c1b-a77a-28f295ff6010
---


# New-CsArchivingConfiguration
[]
Creates a new set of instant messaging (IM) archiving settings. These settings can be used to enable or disable the automatic saving of IM sessions; these settings also enable you to block any instant messages that cannot be archived. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsArchivingConfiguration -Identity <XdsIdentity> [-ArchiveDuplicateMessages <$true | $false>] [-BlockOnArchiveFailure <$true | $false>] [-CachePurgingInterval <UInt32>] [-Confirm [<SwitchParameter>]] [-EnableArchiving <None | ImOnly | ImAndWebConf>] [-EnableExchangeArchiving <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepArchivingDataForDays <UInt32>] [-PurgeExportedArchivesOnly <$true | $false>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 creates a new collection of archiving configuration settings and applies these settings to the Redmond site. By adding the EnableArchiving parameter and setting the parameter value to "ImOnly", the command also enables IM session archiving (but not web conference archiving) for the Redmond site.
  
    
    

```

New-CsArchivingConfiguration -Identity site:Redmond -EnableArchiving "ImOnly"
```


### EXAMPLE 2

Example 2 demonstrates the use of the InMemory parameter to create a collection of archiving configuration settings that initially exist only in memory. To do this, the example creates a new collection of settings (with the Identity site:Redmond) and stores this collection in a variable named $x. Note that, after this first command runs, the collection exists only in memory; if you run the command the **Get-CsArchivingConfiguration** cmdlet you will not see an entry for site:Redmond.
  
    
    
In the second command, the EnableArchiving property for this virtual collection of settings is set to "ImOnly", which enables IM session archiving. Finally, the last command uses the **Set-CsArchivingConfiguration** cmdlet to transform the virtual archiving settings into an actual collection of settings applied to the Redmond site. If you do not call the **Set-CsArchivingConfiguration** cmdlet, these settings will remain in memory only and will disappear when your Windows PowerShell session is terminated or the variable $x is deleted.
  
    
    



```
$x = New-CsArchivingConfiguration -Identity site:Redmond -InMemory
$x.EnableArchiving = "ImOnly"
Set-CsArchivingConfiguration -Instance $x
```


## Detailed Description

Many organizations find it useful to keep a transcript of all the IM sessions carried out by their users. For other organizations, it's mandatory to keep such transcripts; for example, many organizations in the financial world are required by law to keep copies of all their electronic communications.
  
    
    
Skype for Business Server 2015 gives you flexibility when it comes to archiving IM and web conferencing sessions. If you have deployed Archiving Server, you can use the various **CsArchivingConfiguration** cmdlets to enable and disable IM session archiving and to manage your archiving database. You can also suspend IM should archiving fail; this helps to ensure that you keep a record of all your electronic communications.
  
    
    
When you install Skype for Business Server 2015, a collection of global archiving settings will be created for you; by default, these settings will apply to your entire organization. Alternatively, you can use the **New-CsArchivingConfiguration** cmdlet to create custom configuration settings on a site-by-site basis.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier to be assigned to the new collection of archiving configuration settings. In Skype for Business Server 2015 you can create new collections at the site scope or at the service scope. To create new settings at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To create settings at the service scope (for the Registrar service only) use syntax like this:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> |
| _ArchiveDuplicateMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies how cross-pool instant messages should be archived. For example, Ken Myer (with an account in Pool 1) sends an instant message to Pilar Ackerman (who has an account in Pool 2). Pilar, in turn, sends a reply to Ken's instant message. If ArchiveDuplicateMessages is set to False, then (based on a built-in algorithm) the session transcript will be logged in either Pool 1 or Pool 2, but not both. If ArchiveDuplicateMessages is set to True (the default value), the transcript will be logged in both pools.  <br/> |
| _BlockOnArchiveFailure_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, then the IM service will be suspended any time your instant message sessions cannot be archived. If set to False (the default value), instant messaging will continue even if sessions cannot be archived.  <br/> |
| _CachePurgingInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates how often (in hours) the system is purged of transcripts where none of the participants have been enabled for archiving. By design, all group IM sessions and conferencing sessions are recorded when they take place. At the specified interval, the system will determine whether any of the participants in these sessions have been enabled for archiving. If the system finds a session where none of the participants have been enabled for archiving, then that transcript will be deleted from the database.  <br/> The CachePurgeInterval property can be set to any integer value between 4 and 168, inclusive. The default value is 24.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableArchiving_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.EnableArchiving  <br/> |Indicates which items (if any) are saved to the archiving database. Valid values are:  <br/> None. No items are archived to the database. This is the default value.  <br/> ImOnly. IM sessions are archived to the database.  <br/> ImAndWebConf. Both IM and web conferencing sessions are archived to the database.  <br/> |
| _EnableExchangeArchiving_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, Skype for Business Server 2015 instant message and conferencing transcripts are stored in Exchange rather than a separate SQL Server database. Note that if you enable Exchange archiving then users will be managed by the Exchange archiving policies instead of Skype for Business Server 2015 archiving policies.  <br/> The default value is False.  <br/> |
| _EnablePurging_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, archived instant messages will periodically be removed from the database, provided that these instant messages: 1) are older than the value specified in the KeepArchivingDataForDays property; or, 2) have been exported and marked for deletion.  <br/> If False, instant messages will not be automatically deleted from the database.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _KeepArchivingDataForDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |Number of days (between 1 and 2562) that archived instant messages are kept in the database before being automatically deleted. The default value is 14.  <br/> This property takes effect only if EnablePurging has been set to True.  <br/> |
| _PurgeExportedArchivesOnly_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, then the system will only purge instant messages that have been exported (and, as a result, have been marked for deletion). Instant messages that have not been exported will remain in the database, even if those messages are older than the value specified by the KeepArchivingDataForDays property.  <br/> |
| _PurgeHourOfDay_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the time of day when expired records are deleted from the archiving database. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 AM) and 23 representing 11:00 PM. Note that you can only specify the hour of the day. This means that you can schedule purging to take place at 4:00 AM, but you cannot schedule it to take place at, for instance, 4:30 AM or 4:15 AM. The default value is 2 (2:00 AM).  <br/> Database purging takes place only if the EnablePurging property is set to True.  <br/> |
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

None. The **New-CsArchivingConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsArchivingConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)
  
    
    
 [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)
  
    
    
 [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)
  
    
    
 [Set-CsArchivingServer](set-csarchivingserver.md)
