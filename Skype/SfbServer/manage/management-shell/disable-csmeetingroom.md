---
title: "Disable-CsMeetingRoom"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bce6b58-484f-4e59-a259-aa315d37d9b0
description: "Disables a Skype for Business Server 2015 meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. When you disable a meeting room object you remove all the Skype for Business Server 2015-specific Active Directory attributes assigned to the user account that represents the meeting room. However, the Active Directory user account itself is not deleted. This cmdlet was introduced in Lync Server 2013."
---

# Disable-CsMeetingRoom
 
Disables a Skype for Business Server 2015 meeting room. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. When you disable a meeting room object you remove all the Skype for Business Server 2015-specific Active Directory attributes assigned to the user account that represents the meeting room. However, the Active Directory user account itself is not deleted. This cmdlet was introduced in Lync Server 2013.
  
```
Disable-CsMeetingRoom -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 disables the meeting room sip:RedmondMeetingRoom@litwareinc.com.
  
```
Disable-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"
```

### Example 2

In Example 2, all the meeting rooms currently in use in the organization are disabled. To do this, the **Get-CsMeetingRoom** cmdlet is first used to retrieve a collection of all the meeting rooms. That collection is then piped to the **Disable-CsMeetingRoom** cmdlet, which disables each meeting room in the collection.
  
```
Get-CsMeetingRoom | Disable-CsMeetingRoom
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities such as:
  
- One touch meeting join experience
    
- Multi-view video gallery
    
- Touch-enabled white-boarding on the front of room screen
    
- Calendar integration to provide access to scheduled meetings
    
- Content sharing and switching
    
In order to manage these new endpoint devices you must, among other things, create and enable an Exchange resource mailbox account for the device, then enable that resource account for Skype for Business Server 2015. Note that, for Skype for Business Server 2015, there are no cmdlets for creating or removing meeting rooms. Instead, you use the [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet to enable meeting rooms and the **Disable-CsMeetingRoom** cmdlet to disable meeting rooms. The resource account must already exist in order for you to enable the meeting room, and disabling a meeting room only removes that room from your collection of meeting rooms; it does not delete the resource mailbox account.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Disable-CsMeetingRoom** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account to be configured as a meeting room. Identities are typically specified by using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).  <br/> You can also reference a user account by using the user's Active Directory distinguished name.  <br/> You can use the asterisk (\*) wildcard character when using the Display Name as the user Identity. For example, the Identity "\* Smith" returns all the user who have a display name that ends with the string value " Smith".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to disable a meeting room. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a meeting room object through the pipeline that represents the meeting room being disabled. By default, the **Disable-CsMeetingRoom** cmdlet does not pass objects through the pipeline. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Disable-CsMeetingRoom** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Disable-CsMeetingRoom** cmdlet deletes instance of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Enable-CsMeetingRoom](enable-csmeetingroom.md)
  
[Get-CsMeetingRoom](get-csmeetingroom.md)
  
[Move-CsMeetingRoom](move-csmeetingroom.md)
  
[Set-CsMeetingRoom](set-csmeetingroom.md)

