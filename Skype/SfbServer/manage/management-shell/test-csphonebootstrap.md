---
title: "Test-CsPhoneBootstrap"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b132446b-f264-405e-8e3a-971ab1c37694
description: "Verifies that a user can log on to Skype for Business Server 2015 using a Phone Edition-compatible device. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsPhoneBootstrap
 
Verifies that a user can log on to Skype for Business Server 2015 using a Phone Edition-compatible device. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsPhoneBootstrap -PhoneOrExtension <String> -PIN <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetUri <String>] [-UserSipAddress <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 verifies that the user with the specified phone number and PIN can connect to Skype for Business Server 2015 using a Phone Edition-compatible device. In order to run the test, the user's phone number (+14255551219) and the user's PIN (0712) must be supplied.
  
```
Test-CsPhoneBootstrap -PhoneOrExtension "+14255551219" -Pin "0712"
```

### EXAMPLE 2

Example 2 verifies whether or not the user with the specified phone number and PIN can connect to Skype for Business Server 2015 using a Phone Edition-compatible device. In this example, the UserSipAddress parameter is included as an additional check: the test will fail if the user with the SIP address is not the same as the user with the specified phone number and PIN.
  
```
Test-CsPhoneBootstrap -PhoneOrExtension "+14255551219" -Pin "0712" -UserSipAddress "sip:kenmyer@litwareinc.com"
```

## Detailed Description

In order to connect to Skype for Business Server 2015, Phone Edition-compatible devices need to use Dynamic Host Configuration Protocol (DHCP) to retrieve the address of a Skype for Business Server 2015 Registrar; these devices must also provide a valid phone number and associated personal identification number (PIN) in order to be authenticated by the system. (This process is known as "bootstrapping".) The **Test-CsPhoneBootstrap** cmdlet enables administrators to verify that a given user -- using the phone number and PIN assigned to him or her -- is able to log on to the system from a Phone Edition-compatible device. (No device is actually needed in order to run the test.)
  
In order for the **Test-CsPhoneBootstrap** cmdlet to make its check, the Registrar pool that hosts the user account being tested must be discoverable using DHCP. To determine whether a Registrar is discoverable in this manner, use the[Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md) cmdlet and check the value of the EnableDHCPServer property. If this property is set to False, you will need to use the[Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md) cmdlet to set the property value to True and make the Registrar discoverable using DHCP. This can also be done by using Enterprise DHCP Server and configuring the Skype for Business Server 2015-specific options.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PhoneOrExtension_ <br/> |Required  <br/> |System.String  <br/> |Telephone number or extension of the user account being tested. For example: -PhoneOrExt "+14255551219".  <br/> |
| _PIN_ <br/> |Required  <br/> |System.String  <br/> |PIN of the user account being tested.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _TargetFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool that hosts the user account to be tested. If not specified, then DHCP discovery will be used to locate the Registrar pool.  <br/> |
| _TargetUri_ <br/> |Optional  <br/> |System.String  <br/> |URL of the certificate provisioning service. If this parameter is not included, then the DHCP discovery will be used to locate the target URI.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the user account used in the text; for example:  <br/>  `-UserSipAddress "sip:kenmyer@litwareinc.com"` <br/> The UserSipAddress parameter must reference the supplied phone number and PIN; the test will fail if the included phone number and PIN do not belong to the user specified by the UserSipAddress parameter. Note that the SIP address must include the "sip:" prefix.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsPhoneBootstrap** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsPhoneBootstrap** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Test-CsRegistration](test-csregistration.md)

