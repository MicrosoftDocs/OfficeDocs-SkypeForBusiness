---
title: Move-CsMeetingRoom
ms.prod: SKYPEFORBUSINESS
ms.assetid: 4ea6b8bd-b134-4453-9ae4-6118330a62ea
---


# Move-CsMeetingRoom
[]
Moves a Skype for Business Server 2015 meeting room object from one Registrar pool to another. A meeting room is a conferencing device designed to address video conferencing and collaboration scenarios in small conference rooms. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Move-CsMeetingRoom -Identity <UserIdParameter> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 moves the meeting room with the display name "Room 14" to the pool atl-cs-001.litwareinc.com.
  
    
    

```

Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com" -Identity "Room 14"
```


### Example 2

Example 2 moves all the meeting rooms in the organization to the pool atl-cs-001.litwareinc.com. To do this, the command first calls the **Get-CsMeetingRoom** cmdlet without any parameters; that returns a collection of all the meeting rooms configured for use in the organization. That collection is then piped to the **Move-CsMeetingRoom** cmdlet, which moves each meeting room in the collection to the new pool.
  
    
    

```
Get-CsMeetingRoom | Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities such as:
  
    
    

- One touch meeting join experience
    
  
- Multi-view video gallery
    
  
- Touch-enabled white-boarding on the front of room screen
    
  
- Calendar integration to provide access to scheduled meetings
    
  
- Content sharing and switching
    
  
In order to manage these new endpoint devices you must, among other things, create and enable a Exchange resource mailbox account for the device, then enable that resource account for Skype for Business Server 2015. Note that, for Skype for Business Server 2015, there are no cmdlets for creating or removing meeting rooms. Instead, you use the  [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet to enable meeting rooms and the [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet to disable meeting rooms. The resource account must already exist in order for you to enable the meeting room, and disabling a meeting room only removes that room from your collection of meeting rooms; it does not delete the resource mailbox account.
  
    
    
Skype for Business Server Control Panel: The functions carried out by the **Move-CsMeetingRoom** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the meeting room to be moved. Meeting rooms can be specified using one of four formats: 1) the room's SIP address; 2) the room's user principal name (UPN); 3) the room's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the room's Active Directory display name (for example, Main Conference Room). User Identities can also be referenced by using the room's Active Directory distinguished name.  <br/> |
| _Target_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The FQDN (for example, atl-cs-001.litwareinc.com) of the Registrar pool where the meeting room should be moved.  <br/> |
| _UserList_ <br/> |Required  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ConcurrentMovesPerFE_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to run the Move-CsMeetingRoom cmdlet under alternate credentials. This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with user objects. To use the Credential parameter you must first create a PSCredential object using the Get-Credential cmdlet. For details, see the  [Get-Credential](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.security/get-credential) cmdlet help topic. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to move a meeting room. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-dc-001) or its fully qualified domain name (FQDN) (for example, atl-dc-001.litwareinc.com).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the **Move-CsMeetingRoom** cmdlet to ignore all errors that might occur when carrying out the move operation. As a general rule, you should avoid using the Force parameter unless absolutely necessary. <br/> |
| _HostedMigrationOverrideUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the hosted migration service used when moving a meeting room to Skype for Business Online.  <br/> |
| _IgnoreBackendStoreException_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to the move meeting room despite those errors.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a meeting room object through the pipeline that represents the meeting room being moved. By default, the **Move-CsMeetingRoom** cmdlet does not pass objects through the pipeline. <br/> |
| _ProxyPool_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |This parameter is not used with the on-premises version of Skype for Business Online.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The Move-CsMeetingRoom cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Disable-CsMeetingRoom](disable-csmeetingroom.md)
  
    
    
 [Enable-CsMeetingRoom](enable-csmeetingroom.md)
  
    
    
 [Get-CsMeetingRoom](get-csmeetingroom.md)
  
    
    
 [Set-CsMeetingRoom](set-csmeetingroom.md)
