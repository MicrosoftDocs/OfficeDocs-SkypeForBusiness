---
title: "Set-CsThirdPartyVideoSystem"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1ad9b8de-bfae-49ff-be23-8ad928266140
description: "Modifies an existing Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing device (VTC) that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities."
---

# Set-CsThirdPartyVideoSystem
 
Modifies an existing Active Directory contact object that represents a third-party video system. A third-party video system is a video teleconferencing device (VTC) that provides users with telepresence: the ability to participate in online meetings and conferences with full audio and video capabilities.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsThirdPartyVideoSystem -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-Enabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 changes the SIP address for the third-party video system with the Active Directory display name Redmond Video System. To carry out this task, the command first uses the Get-CsThirdPartyVideoSystem cmdlet and the Filter parameter to return the video system that has the Active Directory display name Redmond Video System. The contact object for that system is then piped to the Set-CsThirdPartyVideoSystem cmdlet, which changes the object's SIP address to sip:redmondvideo@litwareinc.com.
  
```
Get-CsThirdPartyVideoSystem -Filter {DisplayName -eq "Redmond Video System" | Set-CsThirdPartyVideoSystem -SipAddress "sip:redmondvideo$litwareinc.com"
```

### Example 2

In Example 2, all the third-party video systems configured for use in the organization are disabled. In order to do this, the command first uses the Get-CsThirdPartyVideoSystem cmdlet (without any parameters) to return a collection of all the available video systems. That collection is then piped to the Set-CsThirdPartyVideoSystem cmdlet, which disables each system by setting the Enabled property to False ($False).
  
```
Get-CsThirdPartyVideoSystem | Set-CsThirdPartyVideoSystem -Enabled $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

Third-party video systems are VTC devices that provide remote users with telepresence capabilities (most notably audio and video). In Skype for Business Server 2015, third-party VTC devices can be configured as Active Directory contact objects, much in the same way that analog phones and common area phones can be configured as contact objects. Associating each VTC device with a contact object makes it easy for administrators to track, and to manage, these devices. VTC contact objects can be created by using the New-CsThirdPartyVideoSystem cmdlet. If you later need to modify the property values for one of these contact objects you can do so by using the Set-CsThirdPartyVideoSystem cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the video system being modified. Video systems are identified by using the Active Directory distinguished name (DN) of the associated contact object. By default, video systems use a GUID (globally unique identifier) as their common name, which means systems will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. In turn, that means that you might find it easier to modify third-party video systems by using the Get-CsThirdPartyVideoSystem cmdlet to return the devices and then piping those objects to the Set-CsThirdPartyVideoSystem cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Configures the Active Directory display name of the video system.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) the video system can be used with Skype for Business Server 2015.  <br/> |
| _ExchangeArchivingPolicy_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ExchangeArchivingPolicyOptionsEnum  <br/> |Indicates where the contact's instant messaging sessions are archived. Allowed values are:  <br/> Uninitialized  <br/> UseLyncArchivingPolicy  <br/> NoArchiving  <br/> ArchivingToExchange  <br/> |
| _LineURI_ <br/> |Optional  <br/> |System.String  <br/> |Phone number for the analog device. The line URI should be specified by using the E.164 format, and should be prefixed by the "TEL:" prefix. For example:  <br/> -LineURI "TEL:+14255551297"  <br/> Any extension number should be added to the end of the line URI; for example:  <br/> -LineURI "TEL:+14255551297;ext=51297"  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a contact object through the pipeline that represents the third-party video system being modified. By default, the Set-CsThirdPartyVideoSystem cmdlet does not pass objects through the pipeline.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |Unique identifier that allows the video system to communicate with SIP devices such as Skype for Business. The SIP address must be prefaced by the prefix "sip:". For example:  <br/> sip:redmondvideo@litwareinc.com  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsThirdPartyVideoSystem cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object.
  
## Return Types
<a name="ReturnTypes"> </a>

By default, the Set-CsThirdPartyVideoSystem cmdlet does not return any data or objects. However, if you include the PassThru parameter the cmdlet will pass instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADThirdPartyVideoSystemContact object through the pipeline.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsThirdPartyVideoSystem](new-csthirdpartyvideosystem.md)
  
[Remove-CsThirdPartyVideoSystem](remove-csthirdpartyvideosystem.md)
  
[Set-CsThirdPartyVideoSystem](set-csthirdpartyvideosystem.md)

