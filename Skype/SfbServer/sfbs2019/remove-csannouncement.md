---
title: "Remove-CsAnnouncement"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a3c62d15-1b0a-49d3-973f-abc06c730bb2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsAnnouncement
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing Lync Server announcement. Announcements are played when users dial a valid but unassigned phone number. An announcement can be a message (such as "This number is temporarily out of service") or a busy signal. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsAnnouncement -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the announcement that has the Identity "ApplicationServer:Redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90". Because Identities must be unique, this command will remove, at most, a single announcement.
  
```
Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90"
```

### EXAMPLE 2

In Example 2, all the announcements that have been applied to the service ApplicationServer:Redmond.litwareinc.com are deleted. To do this, the **Remove-CsAnnouncement** cmdlet is called along with the Identity parameter. Specifying the parameter value "ApplicationServer:Redmond.litwareinc.com" (without the appended GUID that identifies a unique announcement) removes all the announcements configured for the specified service. 
  
```
Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

An organization can own phone numbers that are not assigned to users or phones, but that are still valid numbers that can be called. By default when someone dials one of those numbers, that person will receive a busy signal and the call may result in an error returned to the SIP client. By applying announcement settings to unassigned numbers, administrators have the option of playing a message, returning a busy signal, or redirecting the call. This cmdlet removes one or more of these announcement settings.
  
If you attempt to remove an announcement that is associated with an unassigned number range, by default you'll receive a prompt asking if you really want to remove the announcement. If you delete the announcement, the AnnouncementName property of that range will be displayed as Null and no announcement will be played when those numbers are reached, only a busy signal will be heard. However, the AnnouncementId property value (the GUID of the Announcement that was removed) will remain visible.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsAnnouncement** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAnnouncement"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the Announcement you want to remove. The value for the Identity parameter can be supplied in one of two ways:  <br/> - Enter the Identity of the Application service for the announcements you want to remove. This will remove all announcements configured with the given service Identity. For example, ApplicationServer:Redmond.litwareinc.com.  <br/> - Enter the full Identity of the single announcement you want to remove. This value will always be in the format \<serviceID\>/\<GUID\>, where serviceID is the Identity of the Application Server running the Announcement Service and GUID is a globally unique identifier associated with this announcement. For example: ApplicationServer:Redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsAnnouncement](new-csannouncement.md)
  
[Set-CsAnnouncement](set-csannouncement.md)
  
[Get-CsAnnouncement](get-csannouncement.md)

