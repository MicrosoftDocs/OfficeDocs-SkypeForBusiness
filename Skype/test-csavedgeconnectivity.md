---
title: Test-CsAVEdgeConnectivity
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9f3b2c70-9239-4085-a108-43e0b7a308b5
---


# Test-CsAVEdgeConnectivity
[]
Verifies connectivity through the A/V Edge server. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Test-CsAVEdgeConnectivity -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 verifies that a preconfigured test user can connect to the A/V Edge server configured for the pool atl-cs-001.litwareinc.com Note that this command will fail if you have not defined at least one health monitoring test user for atl-cs-001.litwareinc.com.
  
    
    

```

Test-CsAVEdgeConnectivity -TargetFqdn "atl-cs-001.litwareinc.com"
```


### Example 2

In Example 2, the **Test-CsAVEdgeConnectivity** cmdlet verifies that the user with the SIP address sip:kenmyer@litwareinc.com is able to connect to the AV Edge server. To do this, the first command in the example uses the Get-Credential cmdlet to retrieve a Windows PowerShell credentials object for the user litwareinc\\kenmyer; note that you supply the password for this account when obtaining this object. After the credentials object has been obtained, the second command uses the **Test-CsAVEdgeConnectivity** cmdlet to verify that the user can connect to the AV Edge server.
  
    
    

```
$cred = Get-Credential "litwareinc\\kenmyer"

Test-CsAVEdgeConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsAVEdgeConnectivity** cmdlet verifies that a user can connect to the AV Edge Server assigned to a Registrar pool.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsAVEdgeConnectivity** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credentials object for the account to be tested. The value passed to UserCredential must be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credential object for the user litwareinc\\kenmyer and stores that object in a variable named <br/>  `$x: $x = Get-Credential "litwareinc\\kenmyer"` <br/> You need to supply the user password when running this command. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/> * TrustedServer  <br/> * Negotiate  <br/> * ClientCertificate  <br/> * LiveID  <br/> |
| _AVEdgeAddress_ <br/> |Optional  <br/> |System.String  <br/> |IP address of the Edge server being tested. Specifying the IP address enables you to test the internal side of the Edge server; in turn, this allows you to verify the connection between the test client and the internal Edge server. Note that the internal side often has multiple IP addresses.  <br/> |
| _AVEdgeTCPPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Transmission Control Protocol (TCP) of the Edge server being tested.  <br/> The default value is 443.  <br/> |
| _AVEdgeUDPPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |User Datagram Protocol (UDP) port of the Edge server being tested.  <br/> The default value is 3478.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not use prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for user account to be tested; for example:  `-UserSipAddress "sip:kenmyer@litwareinc.com"`. The UserSipAddress parameter must reference the same user account as UserCredential. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _HybridOnlineUserCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsAVEdgeConnectivity** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsAVEdgeConnectivity** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
