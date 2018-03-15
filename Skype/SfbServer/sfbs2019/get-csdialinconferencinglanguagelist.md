---
title: "Get-CsDialInConferencingLanguageList"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 39355144-c8de-4ad3-9568-6426d3b97ccb
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsDialInConferencingLanguageList
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns a list of languages, including regional/minority languages, supported for use with Lync Server dial-in conferences. These languages are used to relay audio messages and instructions to users participating in a conference by using a telephone. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDialInConferencingLanguageList [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 demonstrates how you can query the **Get-CsDialInConferencingLanguageList** cmdlet to see if a particular language appears in the list of supported languages. In this example, the **Get-CsDialInConferencingLanguageList** cmdlet is called in order to return information about all the supported languages; the Windows PowerShell operator -contains is then used to see if the language code "en-US" is contained within that list of supported languages. If it is, the **Get-CsDialInConferencingLanguageList** cmdlet will report back the value "True". If "en-US" cannot be found in the list of supported languages, then the cmdlet will report back the value "False". 
  
```
(Get-CsDialInConferencingLanguageList).Languages -contains "en-US"
```

### EXAMPLE 2

The command shown in Example 2 returns the complete list of supported languages. The DialInConferencingLanguageList object stores this information in the Languages property. In order to display each language on the screen, this command first uses the **Get-CsDialInConferencingLanguageList** cmdlet to return a collection of all the language lists and their properties. This call to the **Get-CsDialInConferencingLanguageList** cmdlet is enclosed in parentheses to ensure that Windows PowerShell carries out this operation before doing anything else. After the information has been returned, standard "dot notation" (the object name followed by a period followed by a property name) is used to display all the values stored in the Languages property. 
  
```
(Get-CsDialInConferencingLanguageList).Languages
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server enables users to join conferences by using a telephone; these dial-in users cannot view video or exchange instant messages, but they can participate fully in the audio portion of the meeting. When users connect to a conference over the phone, they first hear a welcome message and then are given instructions on how to join the meeting. (For example, depending on how the conference has been configured, they might be asked to state their name and then press the pound (#) key.) At various times Lync Server might need to issue additional messages or instructions; for example, if a user presses 1 on their telephone keypad the system will read a list of all the other keypad options available to them.
  
Administrators can configure the language, or languages, used in a dial-in conference to relay messages and instructions. The **Get-CsDialInConferencingLanguageList** cmdlet returns a list of the supported languages. The list itself is returned using 5-character language codes (for example, ca-ES to indicate Catalan). 
  
The supported language list is read-only. There is no way for you to add new languages to the list; that's because there is no way for you to add a new, supported language to dial-in conferencing. Note, too that the list of available languages is configured at the global scope; you cannot assign different lists to different sites. (However, you can assign different languages to different dial-in conferencing access numbers.)
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsDialInConferencingLanguageList** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsDialInConferencingLanguageList"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying a dial-conferencing language list. Because there is only one such object (global), you can return the language list without using either the Filter or the Identity parameter.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the dial-in conferencing language list to be returned. At this point in time there is only one such object: global. Because of this, you do not need to include this parameter when calling the **Get-CsDialInConferencingLanguageList** cmdlet.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the languages list from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsDialInConferencingLanguageList** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsDialInConferencingLanguageList** cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingLanguageList object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)
  
[Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

