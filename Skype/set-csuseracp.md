---
title: Set-CsUserAcp
ms.prod: SKYPEFORBUSINESS
ms.assetid: f3138d9f-fa3e-4a3c-aa8e-f6dbdda8a834
---


# Set-CsUserAcp
[]
Adds a new audio conferencing provider to a user or group of users, or modifies an existing audio conferencing provider already assigned to a user. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsUserAcp -Identity <UserIdParameter> -Domain <String> -Name <String> -ParticipantPasscode <String> -TollNumber <String> [-Confirm [<SwitchParameter>]] [-IsDefault <$true | $false>] [-PassThru <SwitchParameter>] [-TollFreeNumbers <String[]>] [-Url <String>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, the **Set-CsUserAcp** cmdlet is used to assign a new audio conferencing provider to the user Ken Myer. To do this, the Identity parameter is used to indicate the user account to be modified. In addition, the required parameters TollNumber, ParticipantPassCode, Domain, and Name are included, along with the appropriate parameter values.
  
    
    

```

Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"
```


### EXAMPLE 2

The command shown in Example 2 assigns the same audio conferencing provider to all the users who work in the Finance department. To do this, the command first uses the **Get-CsUser** cmdlet and the LdapFilter (with the filter value "Department=Finance") to return a collection of all the users who work in the Finance department. This collection is then piped to the **Set-CsUserAcp** cmdlet, which assigns the same audio conferencing provider (Fabrikam ACP) to each user in the collection.
  
    
    

```
Get-CsUser -LdapFilter "Department=Finance" | Set-CsUserAcp -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"
```


### EXAMPLE 3

Example 3 assigns the Fabrikam ACP audio conferencing provider to the user Ken Myer. In addition to specifying the TollNumber, ParticipantPassCode, Domain, and Name, this command also includes a pair of toll-free phone numbers. To assign these two values, include the TollFreeNumbers parameter followed by the two phone numbers, separated from one another by a comma.
  
    
    

```
Set-CsUserAcp -Identity "Ken Myer" -TollNumber "14255551298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP" -TollFreeNumbers "18005551010", "18005551020"
```


## Detailed Description

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers offer a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often include high-end services such as live translation, transcription, and live per-conference operator assistance.
  
    
    
Skype for Business Server 2015 does not allow for complete integration with audio conferencing providers. The **CsUserAcp** cmdlets enable administrators to set a phone number and passcode, and to configure other information that can be used for audio conferencing provider integration any time a user schedules a meeting. However, because these cmdlets were not designed for the on-premises version of Skype for Business Server 2015 (instead, they are only intended for use with Skype for Business Online) no additional audio conferencing provider integration is provided beyond assigning property values.
  
    
    
Audio conferencing providers can be assigned to a user account by using the **Set-CsUserAcp** cmdlet. (Note that a user can be assigned multiple audio conferencing providers.) The **Set-CsUserAcp** cmdlet is also used to modify the properties of an existing audio conferencing provider. If you call the **Set-CsUserAcp** cmdlet, the cmdlet uses the parameter information included in the call to check the existing audio conferencing providers assigned to the user. If a match is found, then the existing provider is modified. For example, supposed you issue the following command:
  
    
    



```

Set-CsUserAcp -Identity "Ken Myer" -TollNumber "15554251298" -ParticipantPassCode 13761 -Domain "fabrikam.com" -Name "Fabrikam ACP"

```

Further suppose that Ken Myer has already been assigned an audio conferencing provider named Fabrikam ACP that has the same TollNumber and Domain as those specified in the command. (In other words, the only difference is the ParticipantPassCode,) In that case, the **Set-CsUserAcp** cmdlet will modify the existing Fabrikam ACP provider. If a match is not found, then a new provider will be added to Ken Myer's user account.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Required  <br/> |System.String  <br/> |Domain name of the audio conferencing provider. For example:  <br/>  `-Domain "fabrikam.com"` <br/> The domain name will be given to you by the audio conferencing provider.  <br/> |
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be modified. You can specify a user's identity using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory Domain Services display name (for example, Ken Myer). User identities can also be referenced by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users with a display name that ends in the string value "Smith".  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Name of the audio conferencing provider. For example:  <br/>  `-Name "Fabrikam Conference Services"` <br/> |
| _ParticipantPasscode_ <br/> |Required  <br/> |System.String  <br/> |Passcode required when connecting to a conference by using the audio conferencing provider. For example:  <br/>  `-ParticipantPassCode "0712"` <br/> |
| _TollNumber_ <br/> |Required  <br/> |System.String  <br/> |Non-toll-free phone number used for audio conferences. For example:  <br/>  `-TollNumber "14255551298"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _IsDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not this is the default audio conferencing provider for the user. Each user can only have one default provider.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass an object through the pipeline that represents the user whose account properties are being configured. The PassThru parameter is required in such cases because, by default, the **Set-CsUserAcp** cmdlet does not pass objects through the pipeline. <br/> |
| _TollFreeNumbers_ <br/> |Optional  <br/> |System.String[]  <br/> |Collection of toll-free phone number used for audio conferences. For example:  <br/>  `-TollFreeNumbers "18005551298"` <br/> To add multiple toll-free numbers, separate the individual numbers by using commas:  <br/>  `-TollFreeNumbers "18005551298", "18005559876"` <br/> |
| _Url_ <br/> |Optional  <br/> |System.String  <br/> |Web URL for the audio conferencing provider; for example:  <br/>  `-Url "http://acp.fabrikam.com"` <br/> The web URL enables audio conferencing providers to point users to a webpage containing additional dial-in phone numbers, as well as information about the services offered by the audio conferencing provider.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

String or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Set-CsUserAcp** cmdlet accepts a pipelined string value representing the Identity of a user account that has been enabled for Skype for Business Server 2015. The cmdlet also accepts pipelined instances of the Active Directory user object.
  
    
    

## Return Types

None.
  
    
    

## See also


#### 


  
    
    
 [Get-CsUserAcp](get-csuseracp.md)
  
    
    
 [Remove-CsUserAcp](remove-csuseracp.md)
