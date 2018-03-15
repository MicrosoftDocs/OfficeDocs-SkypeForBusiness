---
title: "Get-CsAnnouncement"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d692b377-8df2-4668-b9d3-06458dd4d96d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAnnouncement
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the Lync Server announcements configured for use in your organization. Announcements are played when users dial a valid but unassigned phone number. An announcement can be a message (such as "This number is temporarily out of service") or a busy signal. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAnnouncement [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns all of the announcements configured for use in the organization. This is done by calling the **Get-CsAnnouncement** cmdlet without any parameters. 
  
```
Get-CsAnnouncement
```

### EXAMPLE 2

The command shown in Example 2 returns a single announcement: the announcement with the Identity ApplicationServer:redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90. For an alternate (and arguably easier) way to retrieve a specific announcement, see Example 5.
  
```
Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com/1951f734-c80f-4fb2-965d-51807c792b90" 
```

### EXAMPLE 3

The command shown in Example 3 returns information about all of the announcements that have been configured for use on the service ApplicationServer:redmond.litwareinc.com.
  
```
Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com"
```

### EXAMPLE 4

In Example 4, information is returned for all of the announcements configured for use in the Redmond site (on all domains). This is done by including the Filter parameter and the filter value "\*ApplicationServer:Redmond\*", which limits the returned data to announcements that have an Identity that contains the string value "ApplicationServer:Redmond". By definition, those are announcements configured for use in the Redmond site.
  
```
Get-CsAnnouncement -Filter "*ApplicationServer:Redmond*"
```

### EXAMPLE 5

Example 5 shows an alternate way to return a specific announcement or set of announcements; in this case, all announcements named Welcome Announcement. To do this, the **Get-CsAnnouncement** cmdlet is first called, without any parameters, in order to return a collection of all the announcements in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out those announcements that have a Name equal to (-eq) "Welcome Announcement". 
  
```
Get-CsAnnouncement | Where-Object {$_.Name -eq "Welcome Announcement"}
```

### EXAMPLE 6

Example 6 in similar to Example 5, but this example shows another way to return a single announcement. We once again call the **Get-CsAnnouncement** cmdlet, but this time we specify an Identity of ApplicationServer:redmond.litwareinc.com. This will return a collection of all announcements associated with that service. As in Example 5, this collection is then piped to the **Where-Object** cmdlet, which picks out those announcements that have a Name equal to (-eq) "Welcome Announcement". Because announcement names must be unique within an Application service, this command will never return more than a single item. 
  
```
Get-CsAnnouncement -Identity "ApplicationServer:redmond.litwareinc.com" | Where-Object {$_.Name -eq "Welcome Announcement"}
```

### EXAMPLE 7

This example is similar to Example 5 in that we retrieve all the announcements, then pipe the collection of announcements to the **Where-Object** cmdlet. However, in Example 5 we used the -eq operator in the where clause to find an identical match for the name. In this example we've used the -like operator and a wildcard value to find all announcements that, in this case, begin with the string Welcome. 
  
```
Get-CsAnnouncement | Where-Object {$_.Name -like "Welcome*"}
```

### EXAMPLE 8

In Example 8, information is returned for all the announcements that use a text-to-speech (TTS) prompt (either as the primary announcement or as a fallback to an audio file) but do not use U.S. English as their language. To carry out this task, the command first calls the **Get-CsAnnouncement** cmdlet in order to return a collection of all the announcements currently configured. This collection is then piped to the **Where-Object** cmdlet, which selects all the announcements where the TextToSpeechPrompt property is not empty (not equal to $Null) and where the Language property is not equal to (-ne) en-US. 
  
```
Get-CsAnnouncement | Where-Object {($_.TextToSpeechPrompt -ne $Null) -and ($_.Language -ne "en-US")}
```

## Detailed Description
<a name="sectionSection1"> </a>

An organization can own phone numbers that are not assigned to users or phones, but that are still valid numbers that can be called. By default, when someone dials one of those numbers, that person will receive a busy signal and the call may result in an error returned to the SIP client. By applying announcement settings to unassigned numbers, administrators have the option of playing a message, returning a busy signal, or redirecting the call. This cmdlet retrieves one or more of these announcement settings.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsAnnouncement** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAnnouncement"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter allows you to perform a wildcard search on the Identity of all announcements configured for the organization. Use the wildcard character (\*) to filter on any part of the Identity.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |An identifier for the Announcement you want to retrieve. If you omit this parameter and the Filter parameter, all instances of announcements configured for the organization will be displayed. The value for the Identity parameter can be supplied in one of two ways:  <br/> - Enter the Identity of the Application service for the announcements you want to retrieve. This will retrieve all announcements configured with the given service Identity. For example, ApplicationServer:Redmond.litwareinc.com.  <br/> - Enter the full Identity of the single announcement you want to retrieve. This value will always be in the format \<serviceID\>/\<GUID\>, where serviceID is the Identity of the Application Server running the Announcement Service and GUID is a globally unique identifier associated with this announcement. For example: ApplicationServer:Redmond.litwareinc.com/bef5fa3b-3c97-4af0-abe7-611deee7616c.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the announcement information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns one or more instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AnnouncementServiceSettings.Announcement object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsAnnouncement](new-csannouncement.md)
  
[Remove-CsAnnouncement](remove-csannouncement.md)
  
[Set-CsAnnouncement](set-csannouncement.md)
  
[Import-CsAnnouncementFile](import-csannouncementfile.md)

