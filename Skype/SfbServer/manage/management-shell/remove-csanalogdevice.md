---
title: "Remove-CsAnalogDevice"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61250894-fde6-476d-aaa2-ec5692af02b3
description: "Removes an existing device from the collection of analog devices that can be managed by using Skype for Business Server 2015. An analog device is a telephone or other device that is connected to the public switched telephone network (PSTN). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsAnalogDevice
 
Removes an existing device from the collection of analog devices that can be managed by using Skype for Business Server 2015. An analog device is a telephone or other device that is connected to the public switched telephone network (PSTN). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsAnalogDevice -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 deletes the analog device that has the Identity CN={e5e7daba-394e-46ec-95a1-1f2a9947aad2},CN=Users,DC=litwareinc,DC=com.
  
```
Remove-CsAnalogDevice -Identity "CN={e5e7daba-394e-46ec-95a1-1f2a9947aad2},CN=Users,DC=litwareinc,DC=com"
```

### EXAMPLE 2

The command shown in Example 2 deletes any analog devices that have been assigned the display name "Building 14 Receptionist". To carry out this task, the command first calls the **Get-CsAnalogDevice** cmdlet along with the Filter parameter; the filter value {DisplayName -eq "Building 14 Receptionist"} limits the returned objects to analog devices where the DisplayName property is equal to "Building 14 Receptionist". The returned items are then piped to, and removed by, the **Remove-CsAnalogDevice** cmdlet.
  
```
Get-CsAnalogDevice -Filter {DisplayName -eq "Building 14 Receptionist"} | Remove-CsAnalogDevice
```

### EXAMPLE 3

Example 3 deletes all of the analog devices that have been assigned the voice policy RedmondVoicePolicy. To do this, the **Get-CsAnalogDevice** cmdlet and the Filter parameter are used to retrieve all of the analog devices where the VoicePolicy property is equal to RedmondVoicePolicy. The filtered collection is then piped to the **Remove-CsAnalogDevice** cmdlet, which deletes each item in that collection.
  
```
Get-CsAnalogDevice -Filter {VoicePolicy -eq "RedmondVoicePolicy"} | Remove-CsAnalogDevice
```

### EXAMPLE 4

The command shown in Example 4 removes all the analog fax machines currently in use in the organization. To carry out this task, the **Get-CsAnalogDevice** cmdlet is called first along with the Filter parameter; the filter value {AnalogFax -eq $True} picks out only those devices where the AnalogFax property is equal to True. In turn, this filtered collection is piped to the **Remove-CsAnalogDevice** cmdlet, which removes each item in the collection.
  
```
Get-CsAnalogDevice -Filter {AnalogFax -eq $True} | Remove-CsAnalogDevice
```

## Detailed Description

Analog devices include telephones, fax machines, modems, and teletype/telecommunication device for the deaf (TTY/TDD) devices connected to the public switched telephone network (PSTN). Unlike devices that take advantage of Enterprise Voice (the Voice over Internet Protocol (VoIP) solution offered by Microsoft), analog devices do not transmit information by using digital packets. Instead, information is transmitted by using a continuous signal. This signal is commonly referred to as an analog signal; hence the term "analog devices."
  
In order to enable administrators to manage analog devices for organizations, Skype for Business Server 2015 lets you associate analog devices with Active Directory contact objects. After a device has been associated with a contact object, you can then manage the analog device by assigning policies and dial plans to the contact. 
  
Over time, you might need to delete a contact object associated with an analog device. For example, if you phase out all of your fax machines, you will no longer need to have analog devices (and contact objects) associated with those machines. The **Remove-CsAnalogDevice** cmdlet provides a way for you to delete analog devices. When you run this cmdlet, the device will be deleted from the list of analog devices returned by the **Get-CsAnalogDevice** cmdlet. Additionally, the contact object associated with that device will be deleted from Active Directory Domain Services.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the analog device to be removed. Analog devices are identified by using the Active Directory distinguished name (DN) of the associated contact object. By default, these devices, use a globally unique identifier (GUID) as their common name; that means analog devices will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Because of that you might find it easier to retrieve analog devices by using the **Get-CsAnalogDevice** cmdlet, and then piping the returned objects to the **Remove-CsAnalogDevice** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object. The **Remove-CsAnalogDevice** cmdlet accepts pipelined instances of the analog device object.
  
## Return Types

The **Remove-CsAnalogDevice** cmdlet deletes existing instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object.
  
## See also

#### 

[Get-CsAnalogDevice](get-csanalogdevice.md)
  
[Move-CsAnalogDevice](move-csanalogdevice.md)
  
[New-CsAnalogDevice](new-csanalogdevice.md)
  
[Set-CsAnalogDevice](set-csanalogdevice.md)

