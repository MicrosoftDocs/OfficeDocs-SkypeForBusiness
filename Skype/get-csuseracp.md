---
title: Get-CsUserAcp
ms.prod: SKYPEFORBUSINESS
ms.assetid: de65eafe-e306-4ada-8509-9688e81491f9
---


# Get-CsUserAcp
[]
Returns information about the audio conferencing providers assigned to a user or group of users. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsUserAcp [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-Filter <String>] [-LdapFilter <String>] [-ResultSize <Unlimited>]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 returns audio conferencing provider information for all the users in your organization.
  
    
    

```

Get-CsUserAcp
```


### EXAMPLE 2

Example 2 returns audio conferencing provider information for a single user: the user with the Identity Ken Myer. In this case, the identity is specified by using the user's Active Directory display name.
  
    
    

```
Get-CsUserAcp -Identity "Ken Myer"
```


### EXAMPLE 3

Example 3 returns information for all the users who have been assigned at least one audio conferencing provider. To do this, the Filter parameter is included along with the filter value {AcpInfo -ne $Null}; this filter value limits the returned data to users who have an AcpInfo property value that is not equal to a null value. To return information about users who have not been assigned an audio conferencing provider use this filter value:
  
    
    
{AcpInfo -eq $Null}
  
    
    



```
Get-CsUserAcp -Filter {AcpInfo -ne $Null}
```


### EXAMPLE 4

Example 4 returns audio conferencing provider information for any user who has been assigned the audio conferencing provider Fabrikam ACP. To carry out this task the command first uses the **Get-CsUserAcp** cmdlet without any parameters in order to return audio conferencing provider information for all the users in your organization. This information is then piped to the **Where-Object** cmdlet, which picks out any user whose AcpInfo property includes (-match) the string value "Fabrikam ACP".
  
    
    

```
Get-CsUserAcp | Where-Object {$_.AcpInfo -match "Fabrikam ACP"}
```


### EXAMPLE 5

In Example 5, detailed information is displayed about the audio conferencing providers assigned to the user Ken Myer. To do this, the **Get-CsUserAcp** cmdlet is first called in order to return audio conferencing provider information for Ken Myer. This data is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to "expand" the value of the AcpInfo property. When a property value is expanded, that means that all the information stored in that value is displayed in easy-to-read format.
  
    
    

```
Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo
```


## Detailed Description

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers provide a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.
  
    
    
Skype for Business Server 2015 does not allow for complete integration with audio conferencing providers. The **CsUserAcp** cmdlets enable administrators to set a phone number and passcode, and to configure other information that can be used for audio conferencing provider integration any time a user schedules a meeting. However, because these cmdlets were not designed for the on-premises version of Skype for Business Server 2015 (instead, they are primarily intended for use with Skype for Business Online) no additional audio conferencing provider integration is provided beyond assigning property values.
  
    
    
The **Get-CsUserAcp** cmdlet enables you to return information about the audio conferencing providers that have been assigned to a user or a group of users. To return audio conferencing provider information for a single user, simply include the Identity parameter followed by the Identity of the user whose information is to be returned. To return information for multiple users, you can use either the LdapFilter or the Filter parameters. The LdapFilter parameter enables you to use generic Active Directory attributes such as Department or Title when specifying user account information; for example, the parameter value "Title=Accountant" restricts the returned information to users who have the job title Accountant. The Filter parameter enables you to use Skype for Business Server 2015-specific attributes (for example, VoicePolicy or EnterpriseVoiceEnabled) to filter the returned data. For example, the filter value {EnterpriseVoiceEnabled -eq $True} limits the user accounts returned by the **Get-CsUserAcp** cmdlet to users who have been enabled for Enterprise Voice.
  
    
    
Alternatively, you can call the **Get-CsUserAcp** cmdlet without any parameters in order to return audio conferencing provider information for all your users. Note that the **Get-CsUserAcp** cmdlet returns audio conferencing provider information for all your users, including users who have not been enabled for Skype for Business Server 2015.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the **Get-CsUserAcp** cmdlet under alternate credentials. This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with contact objects. <br/> To use the Credential parameter you must first create a PSCredential object using the **Get-Credential** cmdlet. For details, see the **Get-Credential** cmdlet help topic. <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on attributes specific to Skype for Business Server 2015. For example, you can limit returned data to users who have been assigned a specific voice policy, or users who have not been assigned a specific voice policy.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the **Where-Object** cmdlet. For example, a filter that returns only users who have been enabled for Enterprise Voice would look like this, with EnterpriseVoiceEnabled representing the Active Directory Domain Services attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value: <br/>  `{EnterpriseVoiceEnabled -eq $True}` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be retrieved. You can specify a user's identity using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory Domain Services display name (for example, Ken Myer). You can also references a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity "* Smith" returns all the users with a display name that ends with the string value " Smith".  <br/> |
| _LdapFilter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on generic Active Directory attributes (that is, attributes that are not specific to Skype for Business Server 2015). For example, you can limit returned data to users who work in a specific department, or users who have a specified manager or job title.  <br/> The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns only users who work in the city of Redmond would look like this: "l=Redmond", with "l" (a lowercase L) representing the Active Directory attribute (locality); "=" representing the comparison operator (equal to); and "Redmond" representing the filter value.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by a command. For example, to return seven users (regardless of how many users are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which 7 users will be returned. If you set the ResultSize to 7 but you have only three users in your forest, the command will return those three users, and then complete without error.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned.  <br/> |
   

## Input Types

String. The **Get-CsUserAcp** cmdlet accepts a pipelined string value representing the Identity of a user account that has been enabled for Skype for Business Server 2015.
  
    
    

## Return Types

The **Get-CsUserAcp** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.ADUserAcp object.
  
    
    

## See also


#### 


  
    
    
 [Remove-CsUserAcp](remove-csuseracp.md)
  
    
    
 [Set-CsUserAcp](set-csuseracp.md)
