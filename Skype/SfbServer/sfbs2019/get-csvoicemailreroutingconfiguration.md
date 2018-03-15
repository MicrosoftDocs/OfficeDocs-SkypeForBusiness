---
title: "Get-CsVoicemailReroutingConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 25e401eb-6a84-468f-b0eb-5b794f20b5bc
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsVoicemailReroutingConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves all of the voice mail rerouting configuration settings defined in this deployment of Lync Server. For example, if there are three branch offices where a Survivable Branch Appliance is deployed, this command will return three voice mail rerouting configuration sets.
  
```
Get-CsVoicemailReroutingConfiguration
```

### EXAMPLE 2

This example retrieves the voice mail rerouting configuration settings for the site BranchOffice_Portland.
  
```
Get-CsVoicemailReroutingConfiguration -Identity site:BranchOffice_Portland
```

### EXAMPLE 3

This example retrieves all the voice mail rerouting settings for all sites with site names beginning with the string BranchOffice (for example, BranchOffice_Portland, BranchOffice_Sacramento). 
  
```
Get-CsVoicemailReroutingConfiguration -Filter *:BranchOffice*
```

### EXAMPLE 4

This example retrieves all the voice mail rerouting configurations that are not enabled. The first part of this command is a call to the **Get-CsVoicemailReroutingConfiguration** cmdlet, which retrieves a collection of all the voice mail rerouting configurations. That collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows that collection down to include only the configurations that have an Enabled property equal to (-eq) False. 
  
```
Get-CsVoicemailReroutingConfiguration | Where-Object {$_.Enabled -eq $False}
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet retrieves settings that determine where Auto Attendant and Subscriber Access calls are rerouted to when IP connectivity from Lync Server in the branch site to the Exchange UM Server located in the data center is not available.
  
Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) so that outside callers can navigate a company's phone system to reach the department or employee they want or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).
  
Calling this cmdlet with no parameters will return all voice mail rerouting configurations.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsVoicemailReroutingConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |The Filter parameter allows you to retrieve configuration settings for a particular set of sites based on wildcard matching.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to retrieve. For this cmdlet the Identity will be either Global or Site:\<site name\>, where \<site name\> is the name of the site to which the settings are applied.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice mail rerouting configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)
  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)
  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)

