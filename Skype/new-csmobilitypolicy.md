---
title: New-CsMobilityPolicy
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1fba8c3e-087d-4ba4-918b-371f8757df7c
---


# New-CsMobilityPolicy
[]
Creates a new mobility policy at the site or the per-user scope. Mobility policies determine whether or not a user can use Skype for Business Mobile. These policies also manage a user's ability to employ Call via Work, a feature that enables users to make and receive phone calls on their mobile phone by using their work phone number instead of their mobile phone number. Mobility policies can also be used to require Wi-Fi connections when making or receiving calls. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
    
    


```

New-CsMobilityPolicy -Identity <XdsIdentity> [-AllowCustomerExperienceImprovementProgram <$true | $false>] [-AllowDeviceContactsSync <$true | $false>] [-AllowExchangeConnectivity <$true | $false>] [-AllowSaveCallLogs <$true | $false>] [-AllowSaveCredentials <$true | $false>] [-AllowSaveIMHistory <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableIPAudioVideo <$true | $false>] [-EnableMobility <$true | $false>] [-EnableOutsideVoice <$true | $false>] [-EnablePushNotifications <$true | $false>] [-EncryptAppData <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-RequireIntune <$true | $false>] [-RequireWIFIForIPAudio <$true | $false>] [-RequireWIFIForIPVideo <$true | $false>] [-RequireWiFiForSharing <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 creates a new mobility policy for the Redmond site, and disables the use of Call via Work for any users affected by the policy. This is done by setting the EnableOutsideVoice parameter to False.
  
    
    

```

New-CsMobilityPolicy -Identity site:Redmond -EnableOutsideVoice $False

```


### EXAMPLE 2

Example 2 demonstrates how you can create a new mobility policy in memory, modify a property value for that policy, and then use the **Set-CsMobilityPolicy** cmdlet to turn the virtual policy into an actual Lync Server mobility policy. To do this, the command first uses the **New-CsMobilityPolicy** cmdlet and the InMemory parameter to create a new policy for the Redmond site. Because the InMemory parameter causes this policy to exists in memory only, the resulting object must be stored in variable ($x).
  
    
    
In command 2, the EnableOutsideVoice property for the virtual policy is set to False. After that, command 3 uses the **Set-CsMobilityPolicy** cmdlet and the Instance parameter to write the changes to Lync Server and create a mobility policy for the Redmond site. If you do not call the **Set-CsMobilityPolicy** cmdlet, the policy will not be created, and, in fact, will disappear as soon as you end your Windows PowerShell command-line interface session or delete the variable $x.
  
    
    



```

$x = New-CsMobilityPolicy -Identity site:Redmond -InMemory
$x.EnableOutsideVoice = $False
Set-CsMobilityPolicy -Instance $x

```


## Detailed Description

Skype for Business Mobile is a client application that enables users to run Skype for Business on their mobile phones. Call via Work provides a way for users to make calls on their mobile phone and yet have it appear as though the call originated from their work phone number instead of their mobile phone number. Users who have been enabled for Call via Work can achieve this either by dialing directly from their mobile phone or by using the dial-out conferencing option. With dial-out conferencing, a user effectively asks the Skype for Business Server 2015 Mobility Service server to make a call for them. The server will set up the call, and then call the user back on their mobile phone. After the user has answered, the server will then dial the party being called. Both of these capabilities can be managed by using mobility policies.
  
    
    
With Skype for Business Server 2015, mobile devices can make or receive phone calls by using either the standard cellular phone network. or by using Wi-Fi connections. Mobility policies can be used to require Wi-Fi connections and to prevent calls over the cellular network.
  
    
    
When you install Skype for Business Server 2015, you will have a single, global mobility policy that applies to all your users. However, administrators can use the **New-CsMobilityPolicy** cmdlet to create custom policies at either the site or the per-user scope.
  
    
    
Note that two different properties must be configured in order to enable Call via Work. The first property, EnableOutsideVoice, determines whether or not Call via Work is enabled; the second, EnableMobility, determines whether or not users are allowed to use Skype for Business Mobile. Both of these properties must be set to true before a user can take advantage of Call via Work. If EnableMobility is set to True and EnableOutsideVoice is set to False, the user can run Skype for Business Server 2015 Mobile but will not be able to use Call via Work. If EnableMobility is set to False and EnableOutsideVoice is set to True the user will not be able to run Skype for Business Mobile. In turn, that means that the user will not be able to use Call via Work, regardless of the value of the EnableOutsideVoice property.
  
    
    
To use Call via Work, users must be managed by a voice policy that allows simultaneous ringing.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity to be assigned to the policy. New mobility policies can be created at the site or per-user scope. To create a new site policy, use the prefix "site:" and the name of the site as your Identity. For example, use this syntax to create a new policy for the Redmond site:  <br/>  `-Identity site:Redmond` <br/> To create a new per-user policy, use an Identity similar to this:  <br/>  `-Identity SalesDepartmentPolicy` <br/> Note that you cannot create a new global policy; if you want to make changes to the global policy, use the **Set-CsMobilityPolicy** cmdlet instead. Likewise, you cannot create a new site or per-user policy if a policy with that Identity already exists. If you need to make changes to an existing policy, use the **Set-CsMobilityPolicy** cmdlet. <br/> |
| _AllowCustomerExperienceImprovementProgram_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) mobile users will be allowed to participate in the Microsoft Customer Experience Improvement Program.  <br/> |
| _AllowDeviceContactsSync_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _AllowExchangeConnectivity_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to connect to Exchange by using their mobile device.  <br/> |
| _AllowSaveCallLogs_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save a call log of calls made from or received by their mobile device.  <br/> Note that this setting does not apply to Android devices.  <br/> |
| _AllowSaveCredentials_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save credentials information (such as passwords) on their mobile device. This information can then be applied to auto-logon scenarios.  <br/> |
| _AllowSaveIMHistory_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value) users will be allowed to save transcripts of IM and conferencing sessions on their mobile devices.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text to accompany the policy. For example, the Description might include information about the users that the policy should be assigned to.  <br/> |
| _EnableIPAudioVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False, prohibits the user from making voice over IP (VoIP) calls using the mobile device. The default value is True, meaning that VoIP calls are allowed.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _EnableMobility_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, users are allowed to use Skype for Business Mobile.  <br/> |
| _EnableOutsideVoice_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, enables users to take advantage of Call via Work. When set to False, users cannot use Call via Work.  <br/> The default value is True.  <br/> |
| _EnablePushNotifications_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EncryptAppData_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of a command called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _RequireIntune_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _RequireWIFIForIPAudio_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the user can use IP audio in calls made when his or her mobile device is connected to a WiFi network. That means that the user will only be allowed to make audio calls using Wi-Fi, and will not be able to use the standard cellular phone network. The default value is False.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _RequireWIFIForIPVideo_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, the user can use IP video only in calls made when mobile device is connected to a Wi-Fi network. If mobile device goes outside of Wi-Fi range, then video calls will be received as audio calls only. If this property is set to False (the default value) then the user can make or receive IP video calls in using either a Wi-Fi or a cellular data connection.  <br/> This parameter was introduced in Lync Server 2013.  <br/> |
| _RequireWiFiForSharing_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, mobile users must use a WiFi connection in order to participate in an application sharing session. When set to False (the default value) mobile users can participate in application sharing by using either a WiFi connection or a cellular (3G/4G) connection.  <br/> If this value is set to True, then users then users will not be able to change their sharing configuration settings. If this value is set to False users can use the Options page to modify their sharing configuration settings.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the new mobility policy is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _AllowAutomaticPstnFallback_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _VoiceSettings_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
   

## Input Types

None. The **New-CsMobilityPolicy** cmdlet does not accept pipelined input.
  
    
    

## Return Types

Creates new instances of the Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility object.
  
    
    

