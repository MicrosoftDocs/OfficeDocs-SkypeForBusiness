---
title: "Set-CsMeetingRoom"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3dd02280-6407-4e17-929c-7070f8d1c3cf
description: "Modifies the property values of an existing Skype for Business Server 2015 meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsMeetingRoom
 
Modifies the property values of an existing Skype for Business Server 2015 meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsMeetingRoom -Identity <UserIdParameter> [-AcpInfo <MultiValuedProperty>] [-AudioVideoDisabled <$true | $false>] [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-HostedVoiceMail <$true | $false>] [-LineServerURI <String>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrivateLine <String>] [-RemoteCallControlTelephonyEnabled <$true | $false>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command show in Example 1 updates the LineUri assigned to the meeting room RedmondMeetingRoom.
  
```
Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -LineUri "tel:+12065551219"
```

### Example 2

In Example 2, the meeting room RedmondMeetingRoom is temporarily disabled; this is done by setting the Enabled property to False ($False): 
  
```
Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -Enabled $False
```

To re-enable the room, simply set the Enabled property to True ($True):
  
```
Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -Enabled $True
```

### Example 3

Example 3 temporarily disables all the meeting rooms in the organization. To do this, the command first calls the **Get-CsMeetingRoom** cmdlet without any parameters; that returns a collection of all the available meeting rooms. That collection is then piped to the **Set-CsMeetingRoom** cmdlet, which temporarily disables each room in the collection.
  
```
Get-CsMeetingRoom | Set-CsMeetingRoom -Enabled $False
```

### Example 4

In Example 4, all the meeting rooms in the organization are configured to use Skype for Business Server 2015 archiving rather than Exchange archiving. To carry out this task, the command first uses the **Get-CsMeetingRoom** cmdlet to return a collection of all the available meeting rooms. That collection is then piped to the **Set-CsMeetingRoom** cmdlet, which uses the ExchangeArchivingPolicy cmdlet to configure each room in the collection to use Skype for Business Server 2015 archiving.
  
```
Get-CsMeetingRoom | Set-CsMeetingRoom -ExchangeArchivingPolicy "UseLyncArchivingPolicy"
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities such as:
  
- One touch meeting join experience
    
- Multi-view video gallery
    
- Touch-enabled white-boarding on the front of room screen
    
- Calendar integration to provide access to scheduled meetings
    
- Content sharing and switching
    
In order to manage these new endpoint devices you must, among other things, create and enable an Exchange resource mailbox account for the device, then enable that resource account for Skype for Business Server 2015. Note that, for Skype for Business Server 2015, there are no cmdlets for creating or removing meeting rooms. Instead, you use the [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet to enable meeting rooms and the [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet to disable meeting rooms. The resource account must already exist in order for you to enable the meeting room, and disabling a meeting room only removes that room from your collection of meeting rooms; it does not delete the resource mailbox account.
  
Skype for Business Server Control Panel: The functions carried out by the **Set-CsMeetingRoom** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |UserIdParameter  <br/> |Indicates the Identity of the meeting room to be modified. Meeting room Identities are typically specified using one of four formats: 1) the room's SIP address; 2) the room's user principal name (UPN); 3) the room's domain name and logon name, in the form domain\logon (for example, litwareinc\room14); and, 4) the room's Active Directory display name (for example, Room 14). You can also reference a room account by using the room's Active Directory distinguished name.  <br/> |
| _AcpInfo_ <br/> |Optional  <br/> |MultiValuedProperty  <br/> |Enables you to assign one or more third-party audio conferencing providers to a meeting room. However, it is recommended that you use the **Set-CsUserAcp** cmdlet to assign Audio conferencing providers. <br/> |
| _AudioVideoDisabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether the room is allowed to make audio/video (A/V) calls by using Skype for Business. If set to True, the room will largely be restricted to sending and receiving instant messages.  <br/> You cannot disable A/V communications if a room is currently enabled for remote call control, Enterprise Voice, and/or Internet Protocol private branch exchange (IP-PBX) soft phone routing.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Fqdn  <br/> |Enables you to connect to the specified domain controller in order to retrieve meeting room information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether or not the room has been enabled for Skype for Business Server 2015. If you set this value to False, the room will no longer be able to log on to Skype for Business Server 2015; setting this value to True re-enables the meeting room's logon privileges.  <br/> If you disable an account by using the Enabled parameter, the information associated with that account (including assigned policies and whether or not the room is enabled for Enterprise Voice and/or remote call control) is retained. If you later re-enable the account by using the Enabled parameter, the associated account information will be restored. This differs from using the **Disable-CsMeetingRoom** cmdlet to disable a meeting room account. When you run Disable-CsMeetingRoom, all the Skype for Business Server 2015 data associated with that account is deleted. <br/> |
| _EnterpriseVoiceEnabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether the room has been enabled for Enterprise Voice, which is the Microsoft implementation of Voice over Internet Protocol (VoIP). With Enterprise Voice, rooms can make telephone calls using the Internet rather than using the standard telephone network.  <br/> |
| _ExchangeArchivingPolicy_ <br/> |Optional  <br/> |ExchangeArchivingPolicyOptionsEnum  <br/> |Indicates how (and where) the room's instant messaging and conferencing sessions will be archived. Allowed values are:  <br/> Uninitialized  <br/> UseLyncArchivingPolicy  <br/> NoArchiving  <br/> ArchivingToExchange  <br/> |
| _HostedVoiceMail_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, enables a room's voice mail calls to be routed to a hosted version of Exchange. In addition, setting this option to True enables rooms to directly place a call to another user's voice mail.  <br/> |
| _LineServerURI_ <br/> |Optional  <br/> |String  <br/> |The URI of the remote call control telephone gateway assigned to the room. The LineServerUri is the gateway URI, prefaced by "sip:". For example:  <br/>  `-LineServerUri "sip:rccgateway@litwareinc.com"` <br/> |
| _LineURI_ <br/> |Optional  <br/> |String  <br/> |Phone number assigned to the room. The line Uniform Resource Identifier (URI) must be specified using the E.164 format and use the "TEL:" prefix. For example:  <br/>  `-LineUri "TEL:+14255551297"` <br/> Any extension number should be added to the end of the line URI, for example:  <br/>  `-LineUri "TEL:+14255551297;ext=51297"` <br/> |
| _PassThru_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Enables you to pass a meeting room object through the pipeline that represents the meeting room being modified. By default, the **Set-CsMeetingRoom** cmdlet does not pass objects through the pipeline. <br/> |
| _PrivateLine_ <br/> |Optional  <br/> |String  <br/> |Phone number for the room private telephone line. A private line is a phone number that is not published in Active Directory Domain Services (AD DS) and, as a result, is not readily available to other people. In addition, this private line bypasses most in-bound call routing rules; for example, a call to a private line will not be forwarded to a room's delegates. Private lines are often used for personal phone calls or for business calls that should be kept separate from other team members.  <br/> The private line value should be specified using the E.164 format, and be prefixed by the "TEL:" prefix. For example:  <br/>  `-PrivateLine "TEL:+14255551297"` <br/> |
| _RemoteCallControlTelephonyEnabled_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether the room has been enabled for remote call control telephony. When enabled for remote call control, a room can employ Skype for Business Server 2015 to answer phone calls made to his or her desk phone. Phone calls can also be made using Skype for Business. These calls all rely on the standard telephone network, also known as the public switched telephone network (PSTN). To make and receive phone calls over the Internet, the room must be enabled for Enterprise Voice. For details, see the parameter EnterpriseVoiceEnabled.  <br/> To be enabled for remote call control, a room must also have both a LineUri and a LineServerUri.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |String  <br/> |Unique identifier (similar to an email address) that allows the room to communicate using SIP devices such as Skype for Business. The SIP address must use the sip: prefix as well as a valid SIP domain; for example:  <br/>  `-SipAddress "sip:room14@litwareinc.com"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsMeetingRoom** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsMeetingRoom** cmdlet modifies existing instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Disable-CsMeetingRoom](disable-csmeetingroom.md)
  
[Enable-CsMeetingRoom](enable-csmeetingroom.md)
  
[Get-CsMeetingRoom](get-csmeetingroom.md)
  
[Move-CsMeetingRoom](move-csmeetingroom.md)

