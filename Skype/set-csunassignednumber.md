---
title: Set-CsUnassignedNumber
ms.prod: SKYPEFORBUSINESS
ms.assetid: e7f52423-58d1-410a-9071-731bde45d3d4
---


# Set-CsUnassignedNumber
[]
Modifies an existing range of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example modifies the unassigned number range with the name UNSet1. We first pass the Identity parameter the value UNSet1, the name of the unassigned number range we want to modify. We then use the NumberRangeStart (+14255551000) and NumberRangeEnd (+14255551900) parameters to modify the range of unassigned numbers to which the specified announcement or Auto Attendant will apply.
  
    
    

```

Set-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"
```


### EXAMPLE 2

This example modifies the Announcement of all unassigned number range settings that currently have an Announcement with the string "Welcome" in the name. First we call the **Get-CsUnassignedNumber** cmdlet to retrieve all unassigned number settings. We pipe that collection of settings to the **Where-Object** cmdlet, which narrows down the collection to only those settings where the AnnouncementName property contains (-match) the string Welcome. Once we have those settings, we pipe them to the **Set-CsUnassignedNumber** cmdlet, where we modify the Application Server ID of the Announcement Service (ApplicationServer:redmond.litwareinc.com) with the AnnouncementService parameter and the name of the new announcement (Help Desk Announcement) with the AnnouncementName parameter. Note that even if the new Announcement has a different name but the same service ID, you must still specify the service ID along with the name.
  
    
    

```
Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Set-CsUnassignedNumber -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Help Desk Announcement"
```


## Detailed Description

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Skype for Business Server 2015 can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet modifies the settings that define that routing.
  
    
    
In order to modify some of the settings for this cmdlet, your system must already either have Announcements defined or an Exchange Auto Attendant set up. To determine whether you have Announcements, call the **Get-CsAnnouncement** cmdlet. To create a new Announcement, call the **New-CsAnnouncement** cmdlet. To check Exchange Auto Attendant settings, run the **Get-CsExUmContact** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AnnouncementName_ <br/> |Required  <br/> |String  <br/> |The name of the Announcement that will be used to handle calls to this range of numbers.  <br/> |
| _AnnouncementService_ <br/> |Required  <br/> |String  <br/> |The fully qualified domain name (FQDN) or service ID of the Announcement server.  <br/> |
| _ExUmAutoAttendantPhoneNumber_ <br/> |Required  <br/> |String  <br/> |The phone number of the Exchange Auto Attendant to route calls in this range to. The Skype for Business Auto Attendant contact must already be set up in order to assign a value to this parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique name for the range of unassigned numbers being modified.  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayAnnouncementVacantNumberRange  <br/> |A reference to an object containing unassigned number settings. This object must be of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange and can be retrieved by calling the **Get-CsUnassignedNumber** cmdlet. <br/> |
| _NumberRangeEnd_ <br/> |Optional  <br/> |String  <br/> |The last number in the range of unassigned numbers. Must be greater than or equal to the number supplied for NumberRangeStart. To specify a range of one number, use the same number for the NumberRangeStart and NumberRangeEnd.  <br/> The number must match the regular expression (tel:)?(\\+)?[1-9]\\d{0,17}(;ext=[1-9]\\d{0,9})?. This means the number may begin with the string tel: (if you don't specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by and extension in the format ;ext= followed by the extension number.  <br/> |
| _NumberRangeStart_ <br/> |Optional  <br/> |String  <br/> |The first number in the range of unassigned numbers. Must be less than or equal to the value supplied for NumberRangeEnd.  <br/> The number must match the regular expression (tel:)?(\\+)?[1-9]\\d{0,17}(;ext=[1-9]\\d{0,9})?. This means the number may begin with the string tel: (if you don't specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.  <br/> |
| _Priority_ <br/> |Optional  <br/> |Int32  <br/> |It is possible for unassigned number ranges to overlap. If a number falls within more than one range, the range with the highest priority will take effect.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange object. Accepts pipelined input of unassigned number objects.
  
    
    

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.
  
    
    

## See also


#### 


  
    
    
 [New-CsUnassignedNumber](new-csunassignednumber.md)
  
    
    
 [Remove-CsUnassignedNumber](remove-csunassignednumber.md)
  
    
    
 [Get-CsUnassignedNumber](get-csunassignednumber.md)
  
    
    
 [New-CsAnnouncement](new-csannouncement.md)
  
    
    
 [Get-CsAnnouncement](get-csannouncement.md)
  
    
    
 [Get-CsExUmContact](get-csexumcontact.md)
