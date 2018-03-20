---
title: "Set-CsMobilityPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 660fcd74-24fc-496e-8aa0-1aadd9334ad3
description: "Modifies an existing mobility policy. Mobility policies determine whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Set-CsMobilityPolicy
 
Modifies an existing mobility policy. Mobility policies determine whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Set-CsMobilityPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1, Call via Work is disabled in the mobility policy assigned to the Redmond site. This is done by setting the EnableOutsideVoice property to False.
  
```
Set-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False

```

### EXAMPLE 2

The command shown in Example 2 disables Call via Work for all the mobility policies configured at the per-user scope. To carry out this task, the command first calls the **Get-CsMobilityPolicy** cmdlet along with the Filter parameter; the filter value "tag:*" limits the returned data to policies that have an Identity that begins with the string value "tag:". That filtered collection of policies is then piped to the **Set-CsMobilityPolicy** cmdlet, which takes each policy in the collection and sets the EnableOutsideVoice property to False.
  
```
Get-CsMobilityPolicy -Filter "tag:*" | Set-CsMobilityPolicy -EnableOutsideVoice $False

```

### EXAMPLE 3

In Example 3, a new description is added to any mobility policy property that does not currently have a description. To do this, the first uses the **Get-CsMobilityPolicy** cmdlet to return a collection of all the mobility policies currently in use in the organization. This collection is then piped to the Where-Object cmdlet, which selects only those policies where the Description property is equal to (-eq) a null value. That filtered collection is then piped to the **Set-CsMobilityPolicy** cmdlet, which sets the Description property for each policy to the string value "Policy owner: kenmyer@litwareinc.com".
  
```
Get-CsMobilityPolicy | Where-Object {$_.Description -eq $Null} | Set-CsMobilityPolicy -Description "Policy owner: kenmyer@litwareinc.com"

```

## Detailed Description

Skype for Business Mobile is a client application that enables users to run Skype for Business on their mobile phones. Call via Work provides a way for users to make calls on their mobile phone and yet have it appear as though the call originated from their work phone number instead of their mobile phone number. Users who have been enabled for Call via Work can achieve this either by dialing directly from their mobile phone or by using the dial-out conferencing option. With dial-out conferencing, a user effectively asks the Skype for Business Server 2015 Mobility Service server to make a call for them. The server will set up the call, and then call the user back on their mobile phone. After the user has answered, the server will then dial the party being called. Both of these capabilities can be managed by using mobility policies.
  
With Skype for Business Server 2015 mobile devices can make or receive phone calls by using either the standard cellular phone network. or by using Wi-Fi connections. Mobility policies can be used to require Wi-Fi connections and to prevent calls over the cellular network.
  
These policies can be modified at any time by using the **Set-CsMobilityPolicy** cmdlet.
  
Note that two different properties must be configured in order to enable Call via Work. The first property, EnableOutsideVoice, determines whether or not Call via Work is enabled; the second, EnableMobility, determines whether or not users are allowed to use Skype for Business Mobile. Both of these properties must be set to true before a user can take advantage of Call via Work. If EnableMobility is set to True and EnableOutsideVoice is set to False, the user can run Skype for Business Server 2015 Mobile but will not be able to use Call via Work. If EnableMobility is set to False and EnableOutsideVoice is set to True the user will not be able to run Skype for Business Mobile. In turn, that means that the user will not be able to use Call via Work, regardless of the value of the EnableOutsideVoice property.
  
To use Call via Work, users must be managed by a voice policy that allows simultaneous ringing.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowCustomerExperienceImprovementProgram_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) mobile users will be allowed to participate in the Microsoft Customer Experience Improvement Program.  <br/> |
| _AllowDeviceContactsSync_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _AllowExchangeConnectivity_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to connect to Exchange by using their mobile device.  <br/> |
| _AllowSaveCallLogs_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save a call log of calls made from or received by their mobile device.  <br/> Note that this setting does not apply to Android devices.  <br/> |
| _AllowSaveCredentials_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save credentials information (such as passwords) on their mobile device. This information can then be applied to auto-logon scenarios.  <br/> |
| _AllowSaveIMHistory_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save transcripts of IM and conferencing sessions on their mobile devices.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text to accompany a mobility policy. For example, the Description might include information about the users the policy should be assigned to.  <br/> |
| _EnableIPAudioVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False, prohibits the user from making voice over IP (VoIP) calls using the mobile device. The default value is True, meaning that VoIP calls are allowed.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _EnableMobility_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users are allowed to use Skype for Business Mobile.  <br/> |
| _EnableOutsideVoice_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, enables users to take advantage of Call via Work. When set to False, users cannot use Call via Work.  <br/> The default value is True.  <br/> |
| _EnablePushNotifications_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EncryptAppData_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier assigned to the policy when it was created. Mobility policies can be assigned at the global, site, or per-user scope. To refer to the global instance, use this syntax:  <br/>  `-Identity global` <br/> To refer to a policy at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To refer to a per-user policy, use syntax similar to this:  <br/>  `-Identity RedmondMobilityPolicy` <br/> If you do not specify an Identity, then the Set-CsMobilityPolicy cmdlet will modify the global policy.  <br/> |
| _Instance_ <br/> |Optional  <br/> |Mobility object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _RequireIntune_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _RequireWIFIForIPAudio_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the user can use IP audio in calls made when his or her mobile device is connected to a WiFi network. That means that the user will only be allowed to make audio calls using Wi-Fi, and will not be able to use the standard cellular phone network. The default value is False.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _RequireWIFIForIPVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the user can use IP video only in calls made when mobile device is connected to a Wi-Fi network. If mobile device goes outside of Wi-Fi range, then video calls will be received as audio calls only. If this property is set to False (the default value) then the user can make or receive IP video calls in using either a Wi-Fi or a cellular data connection.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _RequireWiFiForSharing_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, mobile users must use a WiFi connection in order to participate in an application sharing session. When set to False (the default value) mobile users can participate in application sharing by using either a WiFi connection or a cellular (3G/4G) connection.  <br/> If this value is set to True, then users then users will not be able to change their sharing configuration settings. If this value is set to False users can use the Options page to modify their sharing configuration settings.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the mobility policy is being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _AllowAutomaticPstnFallback_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _VoiceSettings_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility. The **Set-CsMobilityPolicy** cmdlet accepts pipelined instances of the Mobility object.
  
## Return Types

None. Instead, the **Set-CsMobilityPolicy** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility object.
  

