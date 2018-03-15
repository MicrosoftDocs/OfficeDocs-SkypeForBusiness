---
title: "Get-CsAudioConferencingProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4632e9d0-aa87-459f-ad7e-27125c11da5b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAudioConferencingProvider
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about the audio conferencing providers authorized for use in the organization. Audio conferencing providers are a third-party companies that provide organizations with conferencing services. 
  
The **Get-CsAudioConferencingProvider** cmdlet can only be used with Skype for Business Online. 
  
```
Get-CsAudioConferencingProvider [[-Identity] <XdsGlobalRelativeIdentity>] [-LocalStore][<CommonParameters>]Get-CsAudioConferencingProvider [-Filter <string>] [-LocalStore] [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the audio conferencing providers available for use in your organization.
  
```
Get-CsAudioConferencingProvider
```

### Example 2

In Example 2, information is returned for a single audio conferencing provider: the provider with the Identity Fabrikam Telecom.
  
```
Get-CsAudioConferencingProvider -Identity "Fabrikam Telecom"
```

### Example 3

Example 3 demonstrates how wildcard values (and the Filter parameter) can be used to return information about audio conferencing providers. In this example, the filter value "\*Fabrikam\*" returns all audio conferencing providers that have the string value "Fabrikam" anywhere in their Identity.
  
```
Get-CsAudioConferencingProvider -Filter "*Fabrikam*"
```

## Detailed Description
<a name="DetailedDescription"> </a>

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers provide a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.
  
After organizations have contracted with an audio conferencing provider, users can be assigned to the provider by using the **Set-CsUserAcp** cmdlet. Administrators can retrieve information about the audio conferencing providers available to them by using the **Get-CsAudioConferencingProvider** cmdlet. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when indicating the audio conferencing provider (or providers) to be returned. For example, this syntax returns information about all the audio conferencing providers that have the string value "fabrikam" somewhere in their Identity:  <br/> -Filter "\*fabrikam\*"  <br/> Note that you cannot use the Filter parameter and the Identity parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the audio conferencing provider to be returned. For example:  <br/> -Identity "Fabrikam Telecom"  <br/> If neither the Identity parameter nor the Filter parameter are included in a command then the **Get-CsAudioConferencingProvider** cmdlet returns information for all the available providers.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the audio conferencing provider data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsAudioConferencingProvider** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsAudioConferencingProvider** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AudioConferencingProvider.AudioConferencingProvider#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsUserAcp](get-csuseracp.md)
  
[Remove-CsUserAcp](remove-csuseracp.md)
  
[Set-CsUserAcp](set-csuseracp.md)

