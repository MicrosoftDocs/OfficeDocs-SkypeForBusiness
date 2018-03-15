---
title: "New-CsAnalogDevice"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c02755d6-b651-4385-91a0-5b594dc67751
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsAnalogDevice
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new analog device that can be managed by using Lync Server. An analog device is a telephone or other device that is connected to the public switched telephone network (PSTN). This cmdlet was introduced in Lync Server 2010.
  
```
New-CsAnalogDevice -DN <ADObjectId> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new analog device with the phone number (LineUri) 1-425-555-6001. (Note that the phone number must be specified using the E.164 format.) In addition to the LineUri parameter, the other parameters used in this command are DisplayName (to set the Active Directory display name of the device); RegistrarPool (to specify the Registrar pool); AnalogFax (set to $False, to indicate that this is a phone and not a fax machine); Gateway (set to the IP address of the gateway); and OU (the distinguished name of the Active Directory OU where the device's contact object should be created). 
  
```
New-CsAnalogDevice -LineUri tel:+14255556001 -DisplayName "Building 14 Receptionist" -RegistrarPool redmond-Cs-001.litwareinc.com -AnalogFax $False -Gateway 192.168.0.240 -OU "ou=Telecommunications,dc=litwareinc,dc=com"
```

## Detailed Description
<a name="sectionSection1"> </a>

Analog devices include telephones, fax machines, modems, and teletype/telecommunication device for the deaf (TTY/TDD) devices that are connected to the public switched telephone network (PSTN). Unlike devices that take advantage of Enterprise Voice (the Voice over Internet Protocol (VoIP) solution offered by Microsoft), analog devices do not transmit information by using digital packets. Instead, information is transmitted by using a continuous signal. This signal is commonly referred to as an analog signal; hence the term "analog devices." 
  
In order to enable administrators to manage analog devices, Lync Server lets you associate analog devices with Active Directory contact objects. After a device has been associated with a contact object, you can then manage the analog device by assigning policies and dial plans to the contact. 
  
New analog devices are created by using the **New-CsAnalogDevice** cmdlet. This cmdlet can either create new contact objects for use with analog devices or it can associate existing contact objects with a new device. For details, see the OU and the DN parameter descriptions in this topic. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsAnalogDevice** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational units (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsAnalogDevice"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AnalogFax_ <br/> |Required  <br/> |System.Boolean  <br/> |Set to True ($True) if the analog device is a fax machine. Set to False ($False) if the device is not a fax machine.  <br/> |
| _DN_ <br/> |Required  <br/> |Microsoft.Rtc.Management.ADConnect.Core.ADObjectId  <br/> |Enables you to associate an existing Active Directory contact object with the analog device. If you have a contact object you want to associate with an analog device, use the DN parameter followed by the distinguished name of that contact. For example: -DN "cn=Building 14 Lobby,dc=litwareinc,dc=com". Note that the command will fail if the specified contact does not exist.  <br/> You cannot use the OU and the DN parameters in the same command.  <br/> |
| _Gateway_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |IP address of the PSTN gateway to be used by the analog device.  <br/> |
| _LineUri_ <br/> |Required  <br/> |System.String  <br/> |Phone number for the analog device. The line Uniform Resource Identifier (URI) should be specified by using the E.164 format, and be prefixed by the "TEL:" prefix. For example: TEL:+14255551297. Any extension number should be added to the end of the line URI, for example: "TEL:+14255551297;ext=51297".  <br/> |
| _OU_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |Distinguished name of the Active Directory organizational unit (OU) where the contact object should be located. For example: -OU "ou=Redmond,dc=litwareinc,dc=com".  <br/> If you include the OU parameter, a new contact will be created in the specified OU, and the contact will automatically be assigned a GUID (globally unique identifier) as its common name. As a result, the contact object will have a name similar to this: {ce84964a-c4da-4622-ad34-c54ff3ed361f}.  <br/> |
| _RegistrarPool_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where the contact object should be homed. For example: -RegistrarPool "atl-cs-001.litwareinc.com".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Configures the Active Directory display name of the analog device.  <br/> |
| _DisplayNumber_ <br/> |Optional  <br/> |System.String  <br/> |Phone number as displayed in Lync. The DisplayNumber property can be formatted any way you prefer; for example 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; etc.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns an object representing the common area phone.  <br/> |
| _SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |Unique identifier (similar to an e-mail address) that allows the analog device to communicate with SIP devices such as Lync. The SIP address must be prefaced by the prefix "sip:". For example: sip:bldg14lobby@litwareinc.com.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsAnalogDevice** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsAnalogDevice** cmdlet creates new instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAnalogDevice](get-csanalogdevice.md)
  
[Move-CsAnalogDevice](move-csanalogdevice.md)
  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)
  
[Set-CsAnalogDevice](set-csanalogdevice.md)

