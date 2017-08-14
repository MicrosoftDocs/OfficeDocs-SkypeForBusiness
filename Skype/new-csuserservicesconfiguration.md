---
title: New-CsUserServicesConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: bdcb11b5-b8bf-4d63-a8a5-11f2b43686dd
---


# New-CsUserServicesConfiguration
[]
Creates a new collection of User Services configuration settings. The User Services service is used to help maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsUserServicesConfiguration -Identity <XdsIdentity> [-AllowNonRoomSystemNotification <$true | $false>] [-AnonymousUserGracePeriod <TimeSpan>] [-Confirm [<SwitchParameter>]] [-DeactivationGracePeriod <TimeSpan>] [-DefaultSubscriptionExpiration <Int64>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaintenanceTimeOfDay <DateTime>] [-MaxContacts <UInt16>] [-MaxPersonalNotes <UInt32>] [-MaxScheduledMeetingsPerOrganizer <UInt32>] [-MaxSubscriptionExpiration <Int64>] [-MaxSubscriptions <UInt16>] [-MinSubscriptionExpiration <Int64>] [-PresenceProviders <PSListModifier>] [-SubscribeToCollapsedDG <$true | $false>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 creates a new collection of User Services configuration settings for the Redmond site (-Identity site:Redmond). In addition to specifying the Identity, the command also sets the maximum number of contacts (-MaxContacts 500) and the time of day when maintenance occurs (-MaintenanceTimeOfDay "11:00 PM"). Note that this command will fail if User Services settings have already been configured for the Redmond site. That is because you are limited to one collection of settings per site.
  
    
    

```

New-CsUserServicesConfiguration -Identity site:Redmond -MaxContacts 500 -MaintenanceTimeOfDay "11:00 PM"
```


### EXAMPLE 2

Example 2 also creates a new collection of User Services configuration settings for the Redmond site. However, in this example the collection is initially created in memory and is only later applied to the Redmond site. To do this, the first command in the example uses the **New-CsUserServicesConfiguration** cmdlet and the InMemory parameter to create a new collection (with the Identity site:Redmond) that exists only in memory. Because this collection exists only in memory, the User Services object must be stored in a variable. In this case, that's a variable named $x.
  
    
    
After the virtual collection has been created, commands 2 and 3 are used to modify the values of the MaxContacts and the MaintenanceTimeOfDay properties. The final command in the example then uses the **Set-CsUserServicesConfiguration** cmdlet to transform these virtual settings into an actual collection of User Services configuration settings applied to the Redmond site. This final step is crucial: if you do not call the **Set-CsUserServicesConfiguration** cmdlet no settings will be applied to the Redmond site, and your virtual settings will disappear as soon as you terminate your Windows PowerShell session or delete the variable $x.
  
    
    



```
$x = New-CsUserServicesConfiguration -Identity site:Redmond -InMemory
$x.MaxContacts = 500 
$x.MaintenanceTimeOfDay = "11:00 PM"
Set-CsUserServicesConfiguration -Instance $x
```


## Detailed Description

Skype for Business Server 2015 relies on the User Services service to help maintain presence information for users and to manage meetings and conferences. In turn, the **CsUserServicesConfiguration** cmdlets are used to administer User Services configuration settings at the global, site, and service scope. (Note that the only service that can host User Services configuration settings is the User Services service itself.) These settings help determine such things as the number of contacts a user can have, the number of meetings a user can have scheduled at any one time, and the length of time that a given meeting can remain active.
  
    
    
The **New-CsUserServicesConfiguration** cmdlet provides a way for administrators to create a new collection of User Services configuration settings at the site or service scope. (New collections cannot be created at the global scope.) Note that any given site or service can only have, at most, a single collection of User Services configuration settings. Your command will fail if you try to create settings for, say, the Redmond site, and that site already hosts a collection of User Services configuration settings.
  
    
    

  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the User Services configuration settings to be created. To create settings at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To create settings at the service level, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> |
| _AllowNonRoomSystemNotification_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _AnonymousUserGracePeriod_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Represents the amount of time an anonymous (unauthenticated) user can remain in a meeting without an authenticated user being present in that same meeting. For example, if this value is set to 15 minutes an anonymous user can stay in the meeting for, at most, 15 minutes before an authenticated user must join. If an authenticated user does not join before the grace period expires then the anonymous user will be removed from the meeting. This setting applies to both scheduled meetings and to ad-hoc meetings created by clicking Meet Now in Microsoft Lync.  <br/> The AnonymousUserGracePeriod must be specified using the following format: days.hours:minutes:seconds (for example, 0.00:30:00 for 30 minutes). The grace period can be set to any value between 0 second and 1 day; the default value is 90 minutes (01:30:00).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DeactivationGracePeriod_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time that a meeting can remain active. This value must be specified using the following format: days.hours:minutes:seconds. For example, to enable a meeting to last for 60 hours you would use this format: 2.12:00:00 (2 days. 12 hours: 00 minutes: 00 seconds.)  <br/> The DeactivationGracePeriod must be between 8 hours and 365 days, inclusive. The default value is 1 day (1.00:00:00).  <br/> |
| _DefaultSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. If no such request is issued, then the subscription is set to the value specified by the DefaultSubscriptionExpiration property.  <br/> The default subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 28800 seconds (8 hours).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-<cmdlet>**. <br/> |
| _MaintenanceTimeOfDay_ <br/> |Optional  <br/> |System.DateTime  <br/> |Indicates the time of day when regularly-scheduled database maintenance (such as the purging of outdated records) takes place. This value must be specified as a date-time value. You can use either the 24-hour format (for example, "14:00") or the 12-hour format (for example, "2:00 PM").  <br/> The default value for MaintenanceTimeOfDay is 1:00 AM (01:00:00).  <br/> |
| _MaxContacts_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of contacts a user can have; the default value is 250. The MaxContacts property represents the absolute maximum number of contacts a user can have. However, you can use the CsClientPolicy cmdlets to limit certain users to a maximum number of contacts lower than the value of MaxContacts.  <br/> |
| _MaxPersonalNotes_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of personal notes that are stored in the user's note history. By default, the last 3 personal notes are maintained in the note history. The maximum number of notes that can be maintained in the history is 10.  <br/> |
| _MaxScheduledMeetingsPerOrganizer_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum number of meetings that a single user can serve as organizer for at a given time. The default value is 1000. This means that, if a user is already the organizer for 1000 meetings, his or her attempt to schedule a new meeting (meeting number 1001) will fail.  <br/> |
| _MaxSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. The MaxSubscriptionExpiration property represents the maximum amount of time that clients can be granted. For example, if the maximum time is set to 28800 seconds and a client requests a timeout interval of 86400 seconds, the client will be given the maximum allowed expiration period: 28800 seconds.  <br/> The maximum subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 43200 seconds (12 hours).  <br/> |
| _MaxSubscriptions_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of SIP subscribe dialogs that a user can have open at any one time. A subscribe dialog represents a request for SIP resources. The default value is 200.  <br/> |
| _MinSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. The MinSubscriptionExpiration property represents the minimum amount of time that clients can be granted. For example, if the minimum time is set to 1200 seconds and a client requests a timeout interval of 200 seconds, the client will be given the minimum allowed expiration period: 1200 seconds.  <br/> The minimum subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 1200 seconds (20 minutes).  <br/> |
| _PresenceProviders_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of presence providers for the new User Service configuration settings. Presence providers are best added to a collection of User Service configuration settings by using the **New-CsPresenceProvider** cmdlet. <br/> |
| _SubscribeToCollapsedDG_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True (the default value), client applications will be allowed to subscribe to distribution groups that are not currently expanded in the Contacts list. This enables the client to maintain up-to-minute presence information for each member of the group. If set to False, client applications will not be allowed to subscribe to "collapsed" groups.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _StateReplicationFlag_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _TestFeatureList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _TestParameterList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
   

## Input Types

None. The **New-CsUserServicesConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsUserServicesConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
    
    
 [Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)
  
    
    
 [Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)
