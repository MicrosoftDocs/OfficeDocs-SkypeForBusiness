---
title: Set-CsUserServicesConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 51d76f29-4b2b-4208-962c-c5420414ad1b
---


# Set-CsUserServicesConfiguration
[]
Modifies an existing collection of User Services configuration settings. The User Services service is used to help maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsUserServicesConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 modifies the User Services configuration settings for the Redmond site (-Identity site:Redmond). In this example, the AnonymousUserGracePeriod is set to 30 minutes (00 hours: 30 minutes: 00 seconds).
  
    
    

```

Set-CsUserServicesConfiguration -Identity site:Redmond -AnonymousUserGracePeriod "00:30:00"
```


### EXAMPLE 2

In Example 2, the MaintenanceTimeOfDay property is modified for the User Services configuration settings applied to the Redmond site. This is done by using the MaintenanceTimeOfDay parameter and the parameter value 13:30. That sets the maintenance time of day to 1:30 PM (13 hours and 30 minutes on a 24-hour clock).
  
    
    

```
Set-CsUserServicesConfiguration -Identity site:Redmond -MaintenanceTimeOfDay "13:30"
```


### EXAMPLE 3

Example 3 retrieves all the User Services configuration settings applied at the service scope and then modifies the allowed number of contacts for each of these items. To carry out this task, the command first uses the **Get-CsUserServicesConfiguration** cmdlet and the Filter parameter to retrieve all the settings configured at the service scope; the filter value "service:*" limits the returned data to settings that have an Identity that begins with the characters "service:". This filtered collection is then passed to the **Set-CsUserServicesConfiguration** cmdlet, which takes each item in the collection and sets the MaxContacts property to 300.
  
    
    

```
Get-CsUserServicesConfiguration -Filter "service:*" | Set-CsUserServicesConfiguration -MaxContacts 300
```


### EXAMPLE 4

In Example 4, all User Services configuration settings that allow users more than 300 contacts are modified; after the modifications are made, no settings will allow for more than 300 contacts. To do this, the command first calls the **Get-CsUserServicesConfiguration** cmdlet without any additional parameters. This returns a collection of all the User Services configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the MaxContacts property is greater than 300. In turn, the filtered collection is piped to the **Set-CsUserServicesConfiguration** cmdlet, which takes each item in the filtered collection and changes the maximum number of allowed contacts to 300.
  
    
    

```
Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 300} | Set-CsUserServicesConfiguration -MaxContacts 300
```


## Detailed Description

Skype for Business Server 2015 relies on the User Services service to help maintain presence information for users and to manage meetings and conferences. In turn, the **CsUserServicesConfiguration** cmdlets are used to administer User Services configuration settings at the global, site, and service scope. (Note that the only service that can host User Services configuration settings is the User Services service itself.) These settings help determine such things as the number of contacts a user can have, the number of meetings a user can have scheduled at any one time, and the length of time that a given meeting can remain active.
  
    
    
The **Set-CsUserServicesConfiguration** cmdlet provides a way for administrators to modify information about any (or all) of the User Services configuration settings currently in use.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowNonRoomSystemNotification_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _AnonymousUserGracePeriod_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Represents the amount of time an anonymous (unauthenticated) user can remain in a meeting without an authenticated user being present in that same meeting. For example, if this value is set to 15 minutes an anonymous user can stay in the meeting for, at most, 15 minutes before an authenticated user must join. If an authenticated user does not join before the grace period expires then the anonymous user will be removed from the meeting. This setting applies to both scheduled meetings and to ad-hoc meetings created by clicking Meet Now in Skype for Business.  <br/> The AnonymousUserGracePeriod must be specified using the following format: days.hours:minutes:seconds (for example, 0.00:30:00 for 30 minutes). The grace period can be set to any value between 0 second and 1 day; the default value is 90 minutes (01:30:00).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DeactivationGracePeriod_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time that a meeting can remain active. This value must be specified using the following format: days.hours:minutes:seconds. For example, to enable a meeting to last for 60 hours you would use this format: 2.12:00:00 (2 days: 12 hours: 00 minutes: 00 seconds.)  <br/> The DeactivationGracePeriod must be between 8 hours and 365 days, inclusive. The default value is 1 day.  <br/> |
| _DefaultSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. If no such request is issued, then the subscription is set to the value specified by the DefaultSubscriptionExpiration property.  <br/> The default subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 28800 seconds (8 hours).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the User Services configuration settings to be modified. To modify the global settings, use this syntax:  <br/>  `-Identity global` <br/> To modify settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To modify settings at the service level, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> |
| _Instance_ <br/> |Optional  <br/> |UserServicesSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MaintenanceTimeOfDay_ <br/> |Optional  <br/> |System.DateTime  <br/> |Indicates the time of day when regularly-scheduled database maintenance (such as the purging of outdated records) takes place. This value must be specified as a date-time value; you can use either the 24-hour format (for example, "14:00") or the 12-hour format (for example, "2:00 PM").  <br/> The default value for MaintenanceTimeOfDay is 1:00 AM (01:00:00).  <br/> |
| _MaxContacts_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of contacts a user can have; the default value is 250. The MaxContacts property represents the absolute maximum number of contacts a user can have. However, you can use the **CsClientPolicy** cmdlets to limit certain users to a maximum number of contacts lower than the value of MaxContacts. <br/> |
| _MaxPersonalNotes_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum number of personal notes that are stored in the user's note history. By default, the last 3 personal notes are maintained in the note history. The maximum number of notes that can be maintained in the history is 10.  <br/> |
| _MaxScheduledMeetingsPerOrganizer_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum number of meetings that a single user can serve as organizer for at a given time. The default value is 1000; this means that, if a user is already the organizer for 1000 meetings, his or her attempt to schedule a new meeting (meeting number 1001) will fail.  <br/> |
| _MaxSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. The MaxSubscriptionExpiration property represents the maximum amount of time that clients can be granted. For example, if the maximum time is set to 28800 seconds and a client requests a timeout interval of 86400 seconds, the client will be given the maximum allowed expiration period: 28800 seconds.  <br/> The maximum subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 43200 seconds (12 hours).  <br/> |
| _MaxSubscriptions_ <br/> |Optional  <br/> |System.UInt16  <br/> |The maximum number of SIP subscribe dialogs a user can have open at any one time. A subscribe dialog represents a request for SIP resources.  <br/> |
| _MinSubscriptionExpiration_ <br/> |Optional  <br/> |System.Int64  <br/> |Subscriptions are created any time a user makes a request for data such as presence information. When the request is made, the user (or, more correctly, the user's client application) can request the length of time that the subscription remains valid before it must be renewed. The MinSubscriptionExpiration property represents the minimum amount of time that clients can be granted. For example, if the minimum time is set to 1200 seconds and a client requests a timeout interval of 200 seconds, the client will be given the minimum allowed expiration period: 1200 seconds.  <br/> The minimum subscription time must be expressed as an integer value between 300 seconds (5 minutes) and 86400 seconds (24 hours), inclusive. The default value is 1200 seconds (20 minutes).  <br/> |
| _PresenceProviders_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of presence providers for the User Service configuration settings. Presence providers are best added to a collection of User Service configuration settings by using the **New-CsPresenceProvide** r cmdlet. <br/> |
| _SubscribeToCollapsedDG_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True (the default value), client applications will be allowed to subscribe to distribution groups that are not currently expanded in the Contacts list. This enables the client to maintain up-to-minute presence information for each member of the group. If set to False, client applications will not be allowed to subscribe to "collapsed" groups.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _StateReplicationFlag_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _TestFeatureList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _TestParameterList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object. The **Set-CsUserServicesConfiguration** cmdlet accepts pipelined instances of the user services settings object.
  
    
    

## Return Types

The **Set-CsUserServicesConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
    
    
 [New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)
  
    
    
 [Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)
