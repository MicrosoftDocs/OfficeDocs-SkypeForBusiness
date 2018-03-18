---
title: "Remove-CsUserAcp"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: dec450bb-d523-468d-aee4-07fdc3d567c4
description: "Removes one or more audio conferencing providers assigned to a user or group of users. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsUserAcp
 
Removes one or more audio conferencing providers assigned to a user or group of users. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUserAcp -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Name <String>] [-ParticipantPasscode <String>] [-PassThru <SwitchParameter>] [-TollNumber <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 removes all the audio conferencing providers that have been assigned to the user Ken Myer.
  
```
Remove-CsUserAcp -Identity "Ken Myer"
```

### EXAMPLE 2

Example 2 shows how you can remove all of the audio conferencing providers that have been assigned to all the users enabled for Skype for Business Server 2015. To do this, the command first uses the **Get-CsUser** cmdlet to retrieve a collection of all the users who have been enabled for Skype for Business Server 2015. That collection is then piped to the **Remove-CsUserAcp** cmdlet, which removes all the audio conferencing providers that have been assigned to each user in the collection.
  
```
Get-CsUser | Remove-CsUserAcp
```

### EXAMPLE 3

In Example 3, all the audio conferencing providers that have the Name "Fabrikam ACP" are removed from Ken Myer's user account.
  
```
Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"
```

### EXAMPLE 4

Example 4 removes the audio conferencing provider that has the toll number "14255551298" from all the user accounts that have been assigned an audio conferencing provider. To carry out this task, the command first uses the **Get-CsUserAcp** cmdlet to return information about all the audio conferencing providers assigned to all your users. This information is then piped to the **Where-Object** cmdlet, which selects only those accounts where the AcpInfo property includes (-match) the telephone number "14255551298". This filtered collection is then piped to the **Remove-CsUserAcp** cmdlet, which removes the corresponding audio conferencing provider from each account in the filtered collection.
  
```
Get-CsUserAcp | Where-Object {$_.AcpInfo -match "14255551298"} | Remove-CsUserAcp
```

## Detailed Description

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers provide a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.
  
Skype for Business Server 2015 does not allow for complete integration with audio conferencing providers. The **CsUserAcp** cmdlets do enable administrators to set a phone number and passcode, and to configure other information that can be used for audio conferencing provider integration any time a user schedules a meeting. However, because these cmdlets were not designed for the on-premises version of Skype for Business Server 2015 (instead, they are primarily intended for use with Skype for Business Online) no additional audio conferencing provider integration is provided beyond assigning property values.
  
Any audio conferencing provider assigned to a user can later be removed by using the **Remove-CsUserAcp** cmdlet. Calling the **Remove-CsUserAcp** cmdlet without any parameters (other than the Identity parameter, which indicates the user account to be modified) removes all the audio conferencing providers assigned to a user. Alternatively, you can use the optional parameters included with the **Remove-CsUserAcp** cmdlet to remove selected providers from a user account. For example, this command finds the Ken Myer user account and removes all the audio conferencing providers that have a Name equal to "Fabrikam ACP":
  
```
Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

```

To provide finer-grained removal of audio conferencing providers, simply include additional parameters. For example this command removes any audio conferencing providers that have the Name "Fabrikam ACP" and also have a TollNumber equal to "14255551298" as follows:
  
```
Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP" -TollNumber "14255551298"

```

## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account from which the audio conferencing provider is to be removed. You can specify a user's identity using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory Domain Services display name (for example, Ken Myer). User Identities can also be reference by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the users with a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name of the audio conferencing provider. For example:  <br/>  `-Name "Fabrikam Conference Services"` <br/> |
| _ParticipantPasscode_ <br/> |Optional  <br/> |System.String  <br/> |Passcode required when connecting to a conference by using the audio conferencing provider. For example:  <br/>  `-PassCode "0712"` <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user who is having the audio conferencing provider removed. By default, the **Remove-CsUserAcp** cmdlet does not pass objects through the pipeline. <br/> |
| _TollNumber_ <br/> |Optional  <br/> |System.String  <br/> |Non-toll-free phone number used for audio conferences. For example:  <br/>  `-TollNumber "14255551298"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

String or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Remove-CsUserAcp** cmdlet accepts a pipelined string value representing the Identity of a user account that has been enabled for Skype for Business Server 2015. The cmdlet also accepts pipelined instances of the Active Directory user object.
  
## Return Types

None.
  
## See also

#### 

[Get-CsUserAcp](get-csuseracp.md)
  
[Set-CsUserAcp](set-csuseracp.md)

