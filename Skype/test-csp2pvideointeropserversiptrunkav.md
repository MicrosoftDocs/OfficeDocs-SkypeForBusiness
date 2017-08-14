---
title: Test-CsP2PVideoInteropServerSipTrunkAV
ms.prod: SKYPEFORBUSINESS
ms.assetid: bf755ca0-649a-43f3-80b3-8739a92fbad5
---


# Test-CsP2PVideoInteropServerSipTrunkAV
[]
Use the **Test-CsP2PVideoInteropServerSipTrunkAV** cmdlet to test the ability of a video gateway to conduct a peer-to-peer audio/video (A/V) call to a Skype for Business user via a Video Interop Server (VIS) pool.
  
    
    


> [!NOTE]
> There are several pre-requisites required to run **Test-CsP2PVideoInteropServerSipTrunkAV**. See the [Detailed Description](test-csp2pvideointeropserversiptrunkav.md#DetailedDescription) in this topic for more information.
  
    
    


```

Test-CsP2PVideoInteropServerSipTrunkAV -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example creates a credential variable and passes the credential and SIP address of a specific user for testing against the "atl-cs-001.contoso.com" VIS pool.
  
    
    

```

$cred1 = Get-Credential "contoso\\user1"
Test-CsP2PVideoInteropServerSipTrunkAV -UserSipAddress "sip:user1@contoso.com" -UserCredential $cred1 -TargetFqdn "atl-cs-001.contoso.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsP2PVideoInteropServerSipTrunkAV** cmdlet is an example of a Skype for Business Server "synthetic transaction." Synthetic transactions are used in Skype for Business Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as System Center Operations Manager.
  
    
    
Synthetic transactions can be run against a pool, or specific users.
  
    
    

- Administrators will generally use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. The test users are pre-configured for use with synthetic transactions. With test users configured for a pool, administrators can run a synthetic transaction against that pool without having to provide specific users and credentials.
    
  
- Administrators can also run a synthetic transaction using actual Skype for Business user accounts. For example, if one user is reporting audio or video issues, you could use the **Test-CsP2PVideoInteropServerSipTrunkAV** cmdlet to test that user's connection to the VIS pool and that connection's support of audio and video streams. The cmdlet accepts one actual user per run. If you test VIS using actual user accounts you need to supply the logon names and passwords for each user via a credential object created by the **Get-Credential** cmdlet. See Example 1 for more information.
    
  

> [!IMPORTANT]
> **Cmdlet pre-requisites**> The following are pre-requisites for running the **Test-CsP2PVideoInteropServerSipTrunkAV** cmdlet.
  
    
    

When you call **Test-CsCsP2PVideoInteropServerSipTrunkAV** the cmdlet will first attempt to log the synthetic or actual user on to Skype for Business Server. Assuming that the logon succeeds, the cmdlet will simulate a video gateway and attempt to call the test user over the Video Trunk setup with the VIS Pool specified in the configuration file. The **Test-CsP2PVideoInteropServerSipTrunkAV** cmdlet verifies the connection by making an audio-video call to the test user via the target VIS pool. That call also transmits audio-video streams across the network to determine whether media can be sent over the connection. The call is answered by the cmdlet itself, and no manual termination of the call is necessary (no one needs to answer or hang up the call.)
  
    
    
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    



```

Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credentials object for the account to be tested. The value passed to  _UserCredential_ must be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credential object for the user litwareinc\\kenmyer and stores that object in a variable named named $x: `$x = Get-Credential "litwareinc\\kenmyer"`. You need to supply the user password when running **Get-Credential**. <br/> This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> | Type of authentication used in the test. Allowed values are: <br/>  TrustedServer <br/>  Negotiate <br/>  ClientCertificate <br/>  LiveID <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, the transaction log for the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for user account to be tested; for example:  `-UserSipAddress "sip:kenmyer@contoso.com"`.  <br/> The  _UserSipAddress_ parameter must reference the same user account as _UserCredential_. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _HybridOnlineUserCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsVideoInteropServerSyntheticTransactionConfiguration](get-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [Set-CsVideoInteropServerSyntheticTransactionConfiguration](set-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [New-CsVideoInteropServerSyntheticTransactionConfiguration](new-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [Remove-CsVideoInteropServerSyntheticTransactionConfiguration](remove-csvideointeropserversynthetictransactionconfiguration.md)
