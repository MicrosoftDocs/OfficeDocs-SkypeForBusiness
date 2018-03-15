---
title: "New-CsUnassignedNumber"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 81b5d355-56d4-4325-8518-653de8e1fab4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsUnassignedNumber
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new range of unassigned numbers and the routing rules that apply to those numbers. Running this cmdlet will add an entry to the unassigned number routing table. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsUnassignedNumber -AnnouncementName <String> -AnnouncementService <String> -Identity <XdsGlobalRelativeIdentity> -NumberRangeEnd <String> -NumberRangeStart <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example creates an unassigned number range with the name UNSet1. We use the NumberRangeStart (+14255551000) and NumberRangeEnd (+14255551100) parameters to define the range of unassigned numbers to which the specified announcement will apply. Finally, we specify the Announcement by first supplying the AnnouncementService parameter with the service ID of the Announcement service, and then passing the value "Welcome Announcement" to the parameter AnnouncementName. Keep in mind that an Announcement with that name must already exist in the system.
  
```
New-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551100" -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Welcome Announcement"
```

### EXAMPLE 2

This example creates an unassigned number range with the name UNSet2. As in Example 1 we use the NumberRangeStart (+14255552100) and NumberRangeEnd (+14255552200) parameters to define the range of unassigned numbers to which the specified announcement will apply. However, in this example, instead of using the Announcement service, this number range will use the Exchange UM Auto Attendant. (The Auto Attendant is a single number designated as the organization's main number that guides users through voice prompts to help them reach the appropriate party.) We pass a phone number to the ExUmAutoAttendantPhoneNumber parameter to complete this command. Note that Exchange UM must be set up and this number must be an existing contact object phone number in Active Directory Domain Services. The contact must be an Auto Attendant contact (the AutoAttendant property for the contact must be True).
  
```
New-CsUnassignedNumber -Identity UNSet2 -NumberRangeStart "+14255552100" -NumberRangeEnd "+14255552200" -ExUmAutoAttendantPhoneNumber "+12065551234"
```

### EXAMPLE 3

Example 3 is almost identical to Example 2: It creates an unassigned number range with the name UNSet2. The difference in this example is that we've added the Priority parameter, in this case with a value of 2. This means that if an unassigned number range has been defined that overlaps this one and that number range has a higher priority (a lower priority number, such as 1), calls will be routed based on the settings for that range rather than this one.
  
```
New-CsUnassignedNumber -Identity UNSet2 -NumberRangeStart "+14255552100" -NumberRangeEnd "+14255552200" -ExUmAutoAttendantPhoneNumber "+12065551234" -Priority 2
```

## Detailed Description
<a name="sectionSection1"> </a>

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Lync Server can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet creates the settings that define that routing.
  
Before running this cmdlet, your system must already either have Announcements defined or an Exchange Unified Messaging (UM) Auto Attendant set up. To determine whether you have Announcements, call the **Get-CsAnnouncement** cmdlet. To create a new Announcement, call the **New-CsAnnouncement** cmdlet. To check on Exchange UM Auto Attendant settings, run the **Get-CsExUmContact** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsUnassignedNumber** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsUnassignedNumber"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AnnouncementName_ <br/> |Required  <br/> |System.String  <br/> |The name of the Announcement that will be used to handle calls to this range of numbers.  <br/> |
| _AnnouncementService_ <br/> |Required  <br/> |System.String  <br/> |The fully qualified domain name (FQDN) or service ID of the Announcement service. This parameter is required only if you have not specified a value for the ExUmAutoAttendantPhoneNumber parameter.  <br/> |
| _ExUmAutoAttendantPhoneNumber_ <br/> |Required  <br/> |System.String  <br/> |The phone number of the Exchange UM Auto Attendant to route calls in this range to. This field is required only if you are not using an Announcement Service (in which case you do not supply values for the AnnouncementService or AnnouncementName parameters). The Exchange UM Auto Attendant contact must already be set up in order to assign a value to this parameter.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A unique name for the range of unassigned numbers being created. All unassigned number ranges have a global scope, so the name specified here must be unique throughout the Lync Server deployment.  <br/> |
| _NumberRangeEnd_ <br/> |Required  <br/> |System.String  <br/> |The last number in the range of unassigned numbers. Must be greater than or equal to the number supplied for NumberRangeStart. To specify a range of one number, use the same number for the NumberRangeStart and NumberRangeEnd.  <br/> The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don't specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.  <br/> |
| _NumberRangeStart_ <br/> |Required  <br/> |System.String  <br/> |The first number in the range of unassigned numbers. Must be less than or equal to the value supplied for NumberRangeEnd.  <br/> The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don't specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |It is possible for unassigned number ranges to overlap. If a number falls within more than one range, the range with the highest priority will take effect.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Creates an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsUnassignedNumber](remove-csunassignednumber.md)
  
[Set-CsUnassignedNumber](set-csunassignednumber.md)
  
[Get-CsUnassignedNumber](get-csunassignednumber.md)
  
[New-CsAnnouncement](new-csannouncement.md)
  
[Get-CsAnnouncement](get-csannouncement.md)
  
[Get-CsExUmContact](get-csexumcontact.md)

