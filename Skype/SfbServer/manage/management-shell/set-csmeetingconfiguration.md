---
title: "Set-CsMeetingConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 80c3529e-d009-48c5-835a-3740f02b6dd4
description: "Set-CsMeetingConfiguration enables you to modify the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings (also called conferences) that users can create, and also control how (or even if) anonymous users and dial-in conferencing users can join these meetings. Note that these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking the Meet Now option in Skype for Business. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsMeetingConfiguration
 
 **Set-CsMeetingConfiguration** enables you to modify the meeting configuration settings currently in use in your organization. Meeting configuration settings help dictate the type of meetings (also called conferences) that users can create, and also control how (or even if) anonymous users and dial-in conferencing users can join these meetings. Note that these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking the Meet Now option in Skype for Business. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsMeetingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 modifies the meeting configuration settings assigned to the Redmond site ( `-Identity site:Redmond`). In this case, the value of the DesignateAsPresenter property is set to Everyone.
  
```
Set-CsMeetingConfiguration -Identity site:Redmond -DesignateAsPresenter Everyone
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the value of the DesignateAsPresenter property is modified for all the meeting configuration settings in use in the organization. To do this, the **Get-CsMeetingConfiguration** cmdlet is called without any parameters in order to return a collection of all the meeting configuration settings currently in use. This collection is then piped to the **Set-CsMeetingConfiguration** cmdlet, which modifies the DesignateAsPresenter property for each item in the collection.
  
```
Get-CsMeetingConfiguration | Set-CsMeetingConfiguration -DesignateAsPresenter Everyone
```

### EXAMPLE 3

In Example 3, all the meeting configuration settings that do not allow the default admission of anonymous users are modified. To perform this task, the command first calls the **Get-CsMeetingConfiguration** cmdlet to return a collection of all the meeting configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the AdmitAnonymousUsersByDefault property is equal to False. In turn, this filtered collection is piped to the **Set-CsMeetingConfiguration** cmdlet, which takes each item in the collection and sets the PstnCallersBypassLobby property to True.
  
```
Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $False} | Set-CsMeetingConfiguration -PstnCallersBypassLobby $True
```

## Detailed Description

Meetings (also called conferences) are an integral part of Skype for Business Server 2015. The CsMeetingConfiguration cmdlets enable administrators to control the type of meetings that users can create and to determine how meetings deal with anonymous users and dial-in conferencing users. For example, you can configure meetings so that anyone dialing in over the public switched telephone network (PSTN) is automatically admitted to the meeting. Alternatively, you can configure meetings so that dial-in users are not automatically admitted the meeting, but are instead routed to the meeting lobby. These dial-in users remain on hold in the lobby until a presenter admits them to the meeting.
  
As noted previously, these settings only affect scheduled meetings; they do not affect ad-hoc meetings created by clicking Meet Now in Microsoft Lync. When you create a meeting by clicking Meet Now, participant access is automatically open to all everyone, and anonymous users can join the meeting without having to wait in the lobby. This will occur regardless of how you have configured your meeting settings using the CsMeetingConfiguration cmdlets.
  
The **Set-CsMeetingConfiguration** cmdlet enables you to modify any of the meeting configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AdmitAnonymousUsersByDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether meetings will, by default, allow attendance by anonymous users (that is, by unauthenticated users). Set this value to True if you would like new meetings to allow for attendance by anonymous users by default. Set this value to False if you would prefer that, by default, new meetings do not allow for attendance by anonymous users. The default value is True.  <br/> |
| _AssignedConferenceTypeByDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether new meetings will be configured, by default, as public meetings. Set this value to True to use public meetings by default; set this value to False to use private meetings by default. The default value is True.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CustomFooterText_ <br/> |Optional  <br/> |System.String  <br/> |Text to be used on custom meeting invitations.  <br/> |
| _DesignateAsPresenter_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.DesignateAsPresenter  <br/> |Indicates which users (besides the meeting organizer) are automatically designated as presenters when they join a meeting. Valid choices are: None; Company; and Everyone. By default, DesignateAsPresenter is set to Company, meaning everyone in your organization will have presenter rights the moment they join a meeting.  <br/> |
| _EnableAssignedConferenceType_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users are allowed to schedule public meetings. With a public meeting, the conference ID and the meeting link remain consistent each time the meeting is held. With a private meeting, the conference ID and meeting link change from meeting to meeting. The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HelpURL_ <br/> |Optional  <br/> |System.String  <br/> |URL to a website where users can obtain assistance on joining the meeting.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the unique identifier for the collection of meeting configuration settings you want to modify. To refer to the global settings, use this syntax:  `-Identity global`. To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"`. Settings configured at the service scope can be referenced using syntax like this:  `-Identity "service:UserServer:atl-cs-001.litwareinc.com"`.  <br/> If this parameter is not specified, then the **Set-CsMeetingConfiguration** cmdlet will modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |MeetingConfiguration object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _LegalURL_ <br/> |Optional  <br/> |System.String  <br/> |URL to a website containing legal information and meeting disclaimers.  <br/> |
| _LogoURL_ <br/> |Optional  <br/> |System.String  <br/> |URL for the image to be used on custom meeting invitations.  <br/> |
| _PstnCallersBypassLobby_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users dialing in over a public switched telephone network (PSTN) phone line should automatically be admitted to a meeting. If set to True ($True), PSTN callers will automatically be admitted to the meeting. If set to False ($False), then PSTN callers will initially be routed to the conference lobby. At that point, they will have to wait, on hold, until a conference presenter grants them access to the meeting. The default value is True.  <br/> |
| _RequireRoomSystemsAuthorization_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) all users must be authenticated before they can join a meeting using the Skype for Business Room System. The default value is False ($False).  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Office 365 tenant account whose meeting configuration settings are being modified.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration object. The Set-CsMeetingConfiguration cmdlet accepts pipelined instances of the meeting configuration object.
  
## Return Types

The **Set-CsMeetingConfiguration** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.MeetingConfiguration object.
  
## See also

#### 

[Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)
  
[New-CsMeetingConfiguration](new-csmeetingconfiguration.md)
  
[Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)

