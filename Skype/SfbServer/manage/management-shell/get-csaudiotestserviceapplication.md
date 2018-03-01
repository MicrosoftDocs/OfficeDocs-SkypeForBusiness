---
title: "Get-CsAudioTestServiceApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ef36a059-bf9b-4066-a817-db8d82c41e49
description: "Enables you to return information about the Audio Test service application used in your organization. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsAudioTestServiceApplication
 
Enables you to return information about the Audio Test service application used in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAudioTestServiceApplication [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

```

## Examples

### EXAMPLE 1

In Example 1, the **Get-CsAudioTestServiceApplication** cmdlet is called without any additional parameters in order to return a collection of all the Audio Test service contacts currently in use in the organization.
  
```
Get-CsAudioTestServiceApplication
```

### EXAMPLE 2

In Example 2, a single Audio Test service contact is returned: the contact that has the Identity sip:RedmondAudioTest@litwareinc.com.
  
```
Get-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com"
```

### EXAMPLE 3

Example 3 returns all the Audio Test service contacts that have a display name that includes the string value "Redmond". To do this, the command uses the Filter parameter and the filter value {DisplayName -like "\*Redmond\*"}; that filter value limits the returned data to contacts that have a display name that includes the string value "Redmond". This command returns contacts with display names such as "Redmond Audio Test Service Contact", "Redmond Audio Bot", and "Test Contact for Redmond".
  
```
Get-CsAudioTestServiceApplication -Filter {DisplayName -like "*Redmond*"}
```

## Detailed Description

The Audio Test service enables Skype for Business Server 2015 users to test their voice connections before they make a voice call. To do this, users click the Check call quality button found on the Audio Device tab of the Skype for Business Server 2015 Options dialog box. When a user clicks this button, a call will be made to the automated audio test service. The call will be answered and, after an introductory prompt is played, the caller will be asked to record a brief message. That recording will then be replayed, enabling the caller to hear what he or she sounds like over the current connection.
  
The Audio Test service relies, in part, on Active Directory contact objects. These objects are automatically created for you when you install Audio Bot; there is no way to manually create these objects. However, administrators can use the **Get-CsAudioTestServiceApplication** cmdlet to retrieve information about the various test service contacts currently in use in the organization. Administrators can also use the **Set-CsAudioTestServiceApplication** to modify the properties of these contacts.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the cmdlet under alternate credentials. This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with contact objects.  <br/> To use the Credential parameter, you must first create a PSCredential object by using the **Get-Credential** cmdlet. For details, see the **Get-Credential** cmdlet help topic. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve contact information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-cs-001) or its fully qualified domain name (FQDN) (for example, atl-cs-001.litwareinc.com).  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering for attributes specific to Skype for Business Server 2015. For example, you can limit returned data to audio test contact objects that have a specific display name or use a particular language.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax used by the **Where-Object** cmdlet. For example, a filter that returns only contacts that have the display name Audio Test Service Contacts would look like the following, with DisplayName representing the Active Directory attribute, -eq representing the comparison operator (equal to), and "Audio Test Service Contact" representing the filter value: <br/>  `-Filter {DisplayName -eq "Audio Test Service Contact"}` <br/> You cannot use both the Filter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |SIP address of the audio test service contact.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Enables you to return contacts from a specific Active Directory organizational unit (OU). The OU parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs, such as AccountsPayable and AccountsReceivable, users will be returned from each of these three OUs.  <br/> When specifying an OU, use the distinguished name (DN) of that container; for example:  `-OU "OU=Finance,dc=litwareinc,dc=com"`.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |Enables you to limit the number of records returned by a command. For example, to return seven users (regardless of how many users are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven users will be returned. If you set the ResultSize to 7, but you have only three users in your forest, the command will return those three users, and then complete without error.  <br/> The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned.  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsAudioTestServiceApplication** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact object.
  
## See also

#### 

[Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

