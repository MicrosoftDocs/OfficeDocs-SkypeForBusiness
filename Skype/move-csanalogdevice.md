---
title: Move-CsAnalogDevice
ms.prod: SKYPEFORBUSINESS
ms.assetid: c629c5f8-93e7-4fe4-ad51-52bc0ae99a46
---


# Move-CsAnalogDevice
[]
Moves one or more analog devices to a new Registrar pool. An analog device is a telephone or other device that is connected to the public switched telephone network (PSTN). This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Move-CsAnalogDevice -Identity <UserIdParameter> <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 moves the analog device with the Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com to the Registrar pool atl-cs-001.litwareinc.com.
  
    
    

```

Move-CsAnalogDevice -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target atl-cs-001.litwareinc.com
```


### EXAMPLE 2

In Example 2, the analog device that has the Active Directory display name, "Building 14, Room 142", is moved to the Registrar pool atl-cs-001.litwareinc.com. To do this, the **Get-CsAnalogDevice** cmdlet is first called without any parameters in order to return a collection of all the analog devices currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out all the devices that have the display name "Building 14, Room 142". That filtered collection is then piped to the **Move-CsAnalogDevice** cmdlet, which moves all of the devices in the collection to the Registrar pool atl-cs-001.litwareinc.com.
  
    
    

```
Get-CsAnalogDevice | Where-Object {$_.DisplayName -eq "Building 14, Room 142"} | Move-CsAnalogDevice -Target atl-cs-001.litwareinc.com
```


### EXAMPLE 3

The command shown in Example 3 moves all of the analog devices that have a display name that begins with the string value "Building 14". To carry out this task, the command first calls the **Get-CsAnalogDevice** cmdlet to return a collection of all the analog devices currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects all the devices that have a display name that begins with the string value "Building 14". The filtered collection is then piped to the **Move-CsAnalogDevice** cmdlet, which moves each device in the collection to the Registrar pool atl-cs-001.litwareinc.com.
  
    
    

```
Get-CsAnalogDevice | Where-Object {$_.DisplayName -like "Building 14*"} | Move-CsAnalogDevice -Target atl-cs-001.litwareinc.com
```


## Detailed Description

Analog devices include telephones, fax machines, modems, and teletype/telecommunication device for the deaf (TTY/TDD) devices that are connected to the public switched telephone network (PSTN). Unlike devices that take advantage of Enterprise Voice (the Voice over Internet Protocol (VoIP) solution offered by Microsoft), analog devices do not transmit information by using digital packets. Instead, information is transmitted by using a continuous signal. This signal is commonly referred to as an analog signal; hence the term "analog devices."
  
    
    
In order to enable administrators to manage analog devices, Skype for Business Server 2015 lets you associate analog devices with Active Directory contact objects. After a device has been associated with a contact object, you can then manage the analog device by assigning policies and dial plans to the contact. 
  
    
    
The **Move-CsAnalogDevice** cmdlet provides a way for you to move an existing analog device to a new Registrar pool.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the analog device. Analog devices are identified by using the Active Directory distinguished name of the associated contact object. By default, analog devices use a GUID (globally unique identifier) as their common name, which means devices will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.  <br/> |
| _Target_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) (for example, atl-cs-001.litwareinc.com) of the Registrar pool where the analog device should be moved. In addition to a Registrar pool, the Target can also be the FQDN of a hosting provider.  <br/> |
| _UserList_ <br/> |Required  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ConcurrentMovesPerFE_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to connect to the specified domain controller in order to move the analog device. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-cs-001) or its FQDN (for example, atl-cs-001.litwareinc.com).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, moves the analog device but deletes any associated data (such as policies that were assigned to the device). If not present, the device is moved along with any associated data.  <br/> |
| _IgnoreBackendStoreException_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, instructs the computer to ignore any errors that might occur with the backend database and attempt to move the common area phone despite those errors.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a user object through the pipeline that represents the user account being moved. By default, the **Move-CsAnalogDevice** cmdlet does not pass objects through the pipeline. <br/> |
| _ProxyPool_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |This parameter is used only for Skype for Business Online. It should not be used with an on-premises implementation of Skype for Business Server 2015.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types

String. The **Move-CsAnalogDevice** cmdlet accepts a pipelined string value that represents the Identity of the analog device.
  
    
    

## Return Types

By default, the **Move-CsAnalogDevice** cmdlet does not return any objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsAnalogDevice](get-csanalogdevice.md)
  
    
    
 [New-CsAnalogDevice](new-csanalogdevice.md)
  
    
    
 [Remove-CsAnalogDevice](remove-csanalogdevice.md)
  
    
    
 [Set-CsAnalogDevice](set-csanalogdevice.md)
