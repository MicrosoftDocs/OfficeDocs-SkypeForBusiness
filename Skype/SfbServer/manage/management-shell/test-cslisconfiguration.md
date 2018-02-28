---
title: "Test-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6983d42e-6b93-4365-b0f1-81031d6e251b
description: "Tests the Location Information Server (LIS) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsLisConfiguration
[]
Tests the Location Information Server (LIS) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsLisConfiguration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example tests the LIS configuration at the FQDN atl-cs-001.litwareinc.com. The test will be successful if a connection can be made with the current user credentials to the LIS web service at that FQDN. If a location can be found that maps to the subnet IP address 192.168.0.0, then that location address will be returned.
  
For this command to succeed, a health monitoring configuration containing synthetic transaction users must exist. To see if a health monitoring configuration exists, run the **Get-CsHealthMonitoringConfiguration** cmdlet. To create a new health monitoring configuration, run the **New-CsHealthMonitoringConfiguration** cmdlet.
  
```
Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0
```

### EXAMPLE 2

This example is identical to Example 1 but with the addition of the UserSipAddress parameter. Use this command when no synthetic transaction users have been set up, but where the computer on which the command is running has a server certificate.
  
```
Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com
```

### EXAMPLE 3

The first line of this example calls a Windows PowerShell cmdlet, the **Get-Credential** cmdlet, which prompts the user for a user ID and password. This information is stored in an encrypted fashion in the variable $cred.
  
The second line is identical to the command in Example 2 but with the addition of the UserSipAddress parameter. Use this command when no synthetic transaction users have been set up, and where the computer on which the command is running does not have a server certificate.
  
```
$cred = Get-Credential
Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com -UserCredential $cred
```

### EXAMPLE 4

The first line of this example calls the **Get-Credential** cmdlet, which prompts the user for a user ID and password. This information is stored in an encrypted fashion in the variable $cred.
  
Line 2 tests the LIS configuration by making a call to the web service URI (https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc) based on the SIP address of the remote user (sip:kmyer@litwareinc.com), and using the credentials we obtained in line 1 by passing them to the WebCredential parameter. The test will be successful if a connection can be made with the given user credentials to the LIS web service at that URI. If a location can be found that maps to the subnet IP address 192.168.0.0, the MAC address 0A-23-00-00-00-AA or the Port ID 4500 and ChassisId 0A-23-00-00-00-AA, that location address will be returned.
  
Use this command when the computer on which the command is running does not have a server certificate.
  
```
$cred = Get-Credential
Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -WebCredential $cred -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA
```

### EXAMPLE 5

This example is identical to Example 4, except that the command does not use the WebCredential parameter (and therefore also does not call the **Get-Credential** cmdlet). Use this command when the computer on which the command is running has a server certificate.
  
```
Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA
```

## Detailed Description

This cmdlet determines whether the Location Information Server (LIS) web service can be contacted based on the information in the supplied parameters. If the web service can be contacted and a location is found that corresponds to any of the supplied parameters, the test is considered to have passed and the location will be displayed. Even if the location is not found, if the web service can be contacted the test will return a pass, but with no location information. In addition, if you call this cmdlet without supplying any of the optional parameters, the test will still pass as long as the web service can be contacted; however, again, no location information will be returned.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |The fully qualified domain name (FQDN) (in the form server.litwareinc.com) of the server against which you want to run the test.  <br/> This parameter is required unless you specify the TargetUri parameter, in which case you cannot specify a TargetFqdn.  <br/> |
| _TargetUri_ <br/> |Required  <br/> |System.String  <br/> |The Uniform Resource Identifier (URI) of the Location Information service. You can retrieve the URI of the Location Information service by running the following command:  `Get-CsService -WebServer | Select-Object LisServiceInternalUri` <br/> If you specify a value for this parameter, the UserSipAddress parameter is also required. If the computer you are running the command on does not have a server certificate, you must also specify a value for the WebCredential parameter.  <br/> This parameter is required unless you specify the TargetFqdn parameter.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the **Get-Credential** cmdlet and supplying the appropriate credentials. <br/> This parameter is required if the TargetFqdn and UserSipAddress parameters are specified, and if the computer from which you're running the cmdlet does not have a server certificate.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/>  TrustedServer <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _BssId_ <br/> |Optional  <br/> |System.String  <br/> |The Basic Service Set Identifier (BSSID) of a wireless access point. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.  <br/> |
| _ChassisId_ <br/> |Optional  <br/> |System.String  <br/> |The Media Access Control (MAC) address of a network switch. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab, or an IP address.  <br/> |
| _External_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |This parameter is not supported for Location Information Server.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Mac_ <br/> |Optional  <br/> |System.String  <br/> |The MAC address of the port switch. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _PortId_ <br/> |Optional  <br/> |System.String  <br/> |The ID of the port associated with the location to test. This can also contain a MAC address or IP address.  <br/> |
| _PortIdSubType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.PortIDSubType  <br/> |The subtype of the port. This value can be entered as a numeric value or a string, but it must be a valid subtype. Valid subtypes are:  <br/> 1: InterfaceAlias  <br/> 5: InterfaceName  <br/> 7: LocallyAssigned  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |The port number of the Registrar service.  <br/> |
| _Subnet_ <br/> |Optional  <br/> |System.String  <br/> |The IP address of a subnet. This value should be entered as an IPv4 address (digits separated by periods, such as 192.0.2.0).  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |The SIP address of a remote user.  <br/> If you specify a value for this parameter, the TargetFqdn or TargetUri parameter is also required.  <br/> This parameter is required when you specify the TargetFqdn parameter only if you have not set up synthetic transactions users. To see if synthetic transaction users have been set up, run the **Get-CsHealthMonitoringConfiguration** cmdlet. <br/> |
| _WebCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the **Get-Credential** cmdlet and supplying the appropriate credentials. <br/> This parameter is required if the TargetUri and UserSipAddress parameters are specified, and the computer on which the command is run does not have a server certificate.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None.
  
## Return Types

The **Test-CsLisConfiguration** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)
  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)
  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Export-CsLisConfiguration](export-cslisconfiguration.md)

