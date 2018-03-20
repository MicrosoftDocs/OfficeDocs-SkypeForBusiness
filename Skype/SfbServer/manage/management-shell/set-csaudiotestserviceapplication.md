---
title: "Set-CsAudioTestServiceApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d2c6880b-58df-43d1-9f26-d2b9f54d3f0b
description: "Enables you to modify the property values for any of the Audio Test service application contacts currently in use in your organization. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsAudioTestServiceApplication
 
Enables you to modify the property values for any of the Audio Test service application contacts currently in use in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsAudioTestServiceApplication -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-Enabled <$true | $false>] [-EnabledForFederation <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Type <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the primary language for the Audio Test service contact sip:RedmondAudioTest@litwareinc.com is set to U.S. English (en-US).
  
```
Set-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com" -PrimaryLanguage "en-US" 
```

### EXAMPLE 2

Example 2 clears the value of the PrimaryLanguage property for the Audio Test service contact sip:RedmondAudioTest@litwareinc.com. This is done by including the PrimaryLanguage parameter and setting the parameter value to $Null.
  
```
Set-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com" -PrimaryLanguage $Null 
```

### EXAMPLE 3

In Example 3, all the Audio Test service contacts in use in the organization are configured to use U.S. English as their primary language. To do this, the **Get-CsAudioTestServiceApplication** cmdlet is first called without any parameters in order to return a collection of the Audio Test service contacts. This collection is then piped to the **Set-CsAudioTestServiceApplication**, which assigns U.S. English (en-Us) to the PrimaryLanguage property for each contact in the collection.
  
```
Get-CsAudioTestServiceApplication | Set-CsAudioTestServiceApplication -PrimaryLanguage "en-US"
```

## Detailed Description

The Audio Test service enables Skype for Business Server 2015 users to test their voice connections before they make a voice call. To do this, users click the Check call quality button found on the Audio Device tab of the Skype for Business Options dialog box. When a user clicks this button, a call will be made to the automated Audio Test service. The call will be answered and, after an introductory prompt is played, the caller will be asked to record a brief message (10 seconds maximum). That recording will then be replayed, enabling the caller to hear what he or she sounds like over the current connection.
  
The Audio Test service relies, in part, on Active Directory contact objects. These objects are automatically created for you when you install Audio Bot; there is no way to manually create these objects. However, administrators can use the **Get-CsAudioTestServiceApplication** cmdlet to retrieve information about the various test service contacts currently in use in the organization. Administrators can also use the **Set-CsAudioTestServiceApplication** cmdlet to modify the properties of these contacts.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |SIP address of the audio test service contact to be modified.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Active Directory display name of the contact object.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |Although a valid property, DisplayNumber is not actually used with the Audio Test service.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not the contact object has been enabled for Skype for Business Server 2015. If you set this value to False ($False), the contact will no longer be able to log on to Skype for Business Server 2015; setting this value to True ($True) re-enables the contact's logon privileges.  <br/> |
| _EnabledForFederation_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether this contact is available to users from a federated domain. If set to False, only users within your organization will have access to the contact.  <br/> |
| _EnterpriseVoiceEnabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the contact object has been enabled for Enterprise Voice, which is the Microsoft implementation of Voice over Internet Protocol (VoIP). With Enterprise Voice, users can use make telephone calls by using the Internet rather than by using the standard telephone network.  <br/> |
| _ExchangeArchivingPolicy_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ExchangeArchivingPolicyOptionsEnum  <br/> |Indicates where the contact's instant messaging sessions are archived. Allowed values are:  <br/> Uninitialized  <br/> UseLyncArchivingPolicy  <br/> ArchivingToExchange  <br/> NoArchiving  <br/> |
| _LineURI_ <br/> |Optional  <br/> |System.String  <br/> |Although a valid property, LineUri is not actually used with the Audio Test service.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user being assigned the policy. By default, the **Set-CsAudioTestServiceApplication** cmdlet does not pass objects through the pipeline. <br/> |
| _PrimaryLanguage_ <br/> |Optional  <br/> |System.String  <br/> |Primary language used for the audio test service. The language must be configured using one of the allowed language codes; for example, en-US for U.S. English; fr-FR for French; etc. To return a list of the available language codes, type the following command at the Windows PowerShell prompt:  <br/>  `Get-CsDialInConferencingLanguageList | Select-Object -ExpandProperty Languages.` <br/> |
| _SecondaryLanguages_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty  <br/> |Although a valid property, SecondaryLanguages is not actually used with the Audio Test service.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is currently disabled. You cannot change the SIP address using Set-CsAudioTestServiceApplication.  <br/> |
| _Type_ <br/> |Optional  <br/> |System.String  <br/> |Indicates the type of test contact being deployed. By default, contacts are listed as Automaton, which means they can interact with callers.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

The **Set-CsAudioTestServiceApplication** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact object.
  
## Return Types

The **Set-CsAudioTestServiceApplication** cmdlet does not return any objects or values.
  
## See also

#### 

[Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)

