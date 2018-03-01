---
title: "Set-CsLocationPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: efa2840c-2e21-408e-b9fe-6f9998c81db2
description: "Modifies an existing location policy. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsLocationPolicy
 
Modifies an existing location policy. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsLocationPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This command uses the **Set-CsLocationPolicy** cmdlet to modify the location policy with the Identity site:Redmond. (In other words, it modifies the location policy applied to the Redmond site.) In this case, the command sets the value of the EnhancedEmergencyServicesEnabled property to True, which will enable E9-1-1 functionality for all users connected to (in this case) the Redmond site.
  
```
Set-CsLocationPolicy -Identity site:Redmond -EnhancedEmergencyServicesEnabled $True
```

### EXAMPLE 2

Example 2 modifies all the location policies in use in the organization that have defined a conferencing URI to have a conferencing mode of two-way. To carry out this task, the command first uses the **Get-CsLocationPolicy** cmdlet to return a collection of all the location policies currently defined. This collection is then piped to the **Where-Object** cmdlet to narrow the collection down to only those location policies that have a ConferenceUri property that is not empty (not equal to Null). This results in a collection of location policies that have ConferenceUri values. This collection is then piped to the **Set-CsLocationPolicy** cmdlet, which then modifies the value of the ConferenceMode property for each policy in the collection by setting the value to twoway.
  
```
Get-CsLocationPolicy | Where-Object {$_.ConferenceUri -ne $null} | Set-CsLocationPolicy -ConferenceMode twoway
```

## Detailed Description

The location policy is used to apply settings that relate to Enhanced 9-1-1 (E9-1-1) functionality and client location. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. This cmdlet modifies an existing location policy.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ConferenceMode_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Location.ConferenceModeEnum  <br/> |If a value is specified for the ConferenceUri parameter, the ConferenceMode parameter determines whether a third party can participate in the call or can only listen in. Available values are:  <br/> Oneway: Third party can only listen to the conversation between the caller and the Public Safety Answering Point (PSAP) operator.  <br/> Twoway: Third party can listen in and participate in the call between the caller and the PSAP operator.  <br/> |
| _ConferenceUri_ <br/> |Optional  <br/> |System.String  <br/> |The SIP Uniform Resource Identifier (URI), in this case the telephone number, of a third party that will be conferenced in to any emergency calls that are made. For example, the company security office could receive a call when an emergency call is made and listen in or participate in that call (depending on the value of the ConferenceMode property).  <br/> The string must be from 1 to 256 characters in length and must begin with the prefix sip:.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A detailed description of this location. For example, "Building 30, 3rd Floor, Northeast corner".  <br/> |
| _EmergencyDialMask_ <br/> |Optional  <br/> |System.String  <br/> |A number that is dialed that will be translated into the value of the EmergencyDialString property. For example, if EmergencyDialMask has a value of "212" and EmergencyDialString has a value of "911", if a user dials 212 the call will be made to 911. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services (for example, if someone from a country/region with a different emergency number attempts to dial that country/region's number rather than the number for the country/region they're currently in). You can define multiple emergency dial masks by separating the values with semicolons. For example,  `-EmergencyDialMask "212;414"`.  <br/> IMPORTANT. Ensure that the specified dial mask value is not the same as a number in a call park orbit range. Call park routing will take precedence over emergency dial string conversion. To see the existing call park orbit ranges, call the **Get-CsCallParkOrbit** cmdlet. <br/> Maximum length of the string is 100 characters. Each character must be a digit 0 through 9.  <br/> |
| _EmergencyDialString_ <br/> |Optional  <br/> |System.String  <br/> |The number that is dialed to reach emergency services. In the United States this value is "911".  <br/> The string must be made of the digits 0 through 9 and can be from 1 to 10 characters in length.  <br/> |
| _EmergencyNumbers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |PARAMVALUE: PSListModifier  <br/> |
| _EnhancedEmergencyServiceDisclaimer_ <br/> |Optional  <br/> |System.String  <br/> |Text value containing information that will be displayed to users who are connected from locations that cannot be resolved by the location mapping (wiremap) who choose not to enter their location manually. To remove a service disclaimer from a location policy set this property to a null value:  <br/>  `-EnhancedEmergencyServiceDisclaimer $Null` <br/> Location policies, and the EnhancedEmergencyServiceDisclaimer property, should be used in Skype for Business Server 2015 to set disclaimers for the E9-1-1 service. By using location policies to set these disclaimers, you can create different disclaimers for different locales or different sets of users.  <br/> |
| _EnhancedEmergencyServicesEnabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether the users associated with this policy are enabled for E9-1-1. Set the value to True to enable E9-1-1, so Skype for Business Server 2015 clients will retrieve location information on registration and include that information when an emergency call is made.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the location policy you want to modify. To modify the global location policy, use a value of Global. For a policy created at the site scope, this value will be in the form site:\<site name\>, where site name is the name of a site defined in the Skype for Business Server 2015 deployment (for example, site:Redmond). For a policy created at the per-user scope, this value will simply be the name of the policy, such as Reno.  <br/> |
| _Instance_ <br/> |Optional  <br/> |LocationPolicy  <br/> |A reference to a location policy object. This object must be of type Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy, which can be retrieved by calling the **Get-CsLocationPolicy** cmdlet. Retrieve this object, change the properties in memory, and then pass the object reference as a value to this parameter to update that location policy. <br/> |
| _LocationRefreshInterval_ <br/> |Optional  <br/> |System.Int64  <br/> |Specifies the amount of time (in hours) between client requests for Location Information service location update. The LocationRefreshInterval can be set to any value between 1 and 12; the default value is 4.  <br/> |
| _LocationRequired_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationRequiredEnum  <br/> |If the client was unable to retrieve a location from the location configuration database, the user can be prompted to manually enter a location. This parameter accepts the following values:  <br/> - no: The user will not be prompted for a location. When a call is made with no location information, the Emergency Service Provider will answer the call and ask for a location.  <br/> - yes: The user will be prompted to input location information when the client registers at a new location. The user can dismiss the prompt without entering any information. If information is entered, a call made to 911 will first be answered by the Emergency Service Provider to verify the location before being routed to the PSAP (that is, the 911 operator).  <br/> - disclaimer: This option is the same as yes except that if the user dismisses the prompt disclaimer text will be displayed that can alert the user to the consequences of declining to enter location information. (The disclaimer text must be set by calling the **Set-CsEnhancedEmergencyServiceDisclaimer** cmdlet.) <br/> This value is ignored if EnhancedEmergencyServicesEnabled is set to False (the default). Users will not be prompted for location information.  <br/> |
| _NotificationUri_ <br/> |Optional  <br/> |System.String  <br/> |One or more SIP Uniform Resource Identifiers (URIs) to be notified when an emergency call is made. For example, the company security office could be notified through an instant message whenever an emergency call is made. If the caller's location is available that location will be included in the notification.  <br/> Multiple SIP URIs can be included as a comma-separated list. For example,  `-NotificationUri sip:security@litwareinc.com,sip:kmyer@litwareinc.com`. Note that, with the release of Skype for Business Server 2015 distribution lists can now be configured as a notification URI.  <br/> The string must be from 1 to 256 characters in length and must begin with the prefix sip:.  <br/> |
| _PstnUsage_ <br/> |Optional  <br/> |System.String  <br/> |The public switched telephone network (PSTN) usage that will be used to determine which voice route will be used to route 911 calls from clients using this profile. The route associated with this usage should point to a SIP trunk dedicated to emergency calls.  <br/> The usage must already exist in the global list of PSTN usages. Call the **Get-CsPstnUsage** cmdlet to retrieve a list of usages. To create a new usage, call the **Set-CsPstnUsage** cmdlet. <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for whom the location policy is being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _UseLocationForE911Only_ <br/> |Optional  <br/> |System.Boolean  <br/> |Location information can be used by the Skype for Business Server 2015 client for various reasons (such as notifying teammates of current location). Set this value to True to ensure location information is available only for use with an emergency call.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object. Accepts pipelined input of location policy objects.
  
## Return Types

This cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy object.
  
## See also

#### 

[New-CsLocationPolicy](new-cslocationpolicy.md)
  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)
  
[Test-CsLocationPolicy](test-cslocationpolicy.md)
  
[Get-CsPstnUsage](get-cspstnusage.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)

