---
title: Test-CsXmppIM
ms.prod: SKYPEFORBUSINESS
ms.assetid: ffeb05a7-141d-46dc-936f-1f7218521ff8
---


# Test-CsXmppIM
[]
Verifies whether or not an instant message can be sent across an XMPP gateway. XMPP gateways enable Skype for Business Server 2015 users to exchange instant message and presence information with users belonging to IM and presence providers that employ the extensible Messaging and Presence Protocol (XMPP). This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Test-CsXmppIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The preceding example verifies the XMPP instant messaging capabilities for the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to send an XMPP instant message to a user with the SIP address adelaney@contoso.com. 
  
    
    
If test users have not been defined, then the command will fail because it will not know which user to log on as. If you have not defined test users for a pool, then you must include the UserSipAddress parameter and the credentials of the user that the command should use when trying to log on.
  
    
    



```

Test-CsXmppIM -TargetFqdn "atl-cs-001.litwareinc.com" -Receiver "adelany@contoso.com"
```


### Example 2

The commands shown in Example 2 test the ability of a specific user (litwareinc\\pilar) to log on to send an XMPP instant message to the user adelaney@contoso.com. To do this, the first command in the example uses the Get-Credential cmdlet to create a Windows PowerShell command-line interface credential object containing the name and password of the user Pilar Ackerman. (Because the logon name litwareinc\\pilar has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credential object is then stored in a variable named $cred1.
  
    
    
The second command then checks to see if this user can log on to the pool atl-cs-001.litwareinc.com and send the XMPP instant message. To carry out this task, the **Test-CsXmppIm** cmdlet is called, along with four parameters: TargetFqdn (the FQDN of the Registrar pool); Receiver (the SIP address of the user the message is being addressed to); UserCredential (the Windows PowerShell object containing Pilar Ackerman's user credentials); and UserSipAddress (the SIP address corresponding to the supplied user credentials).
  
    
    



```
$credential = Get-Credential "litwareinc\\kenmyer"

Test-CsXmppIM -TargetFqdn "atl-cs-001.litwareinc.com" -Receiver "adelany@contoso.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat. The **Test-CsXmppIM** cmdlet verifies that a user can exchange instant messages with a user on an XMPP network. Note that, for this test to succeed, you must have a valid SIP address for the XMPP user, and that SIP address must be on a network that has been configured as an allowed XMPP partner.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsXmppIM** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Receiver_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the user who the test message is addressed to.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the pool being tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account to be tested. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\kenmyer and stores that object in a variable named $x:$x = Get-Credential "litwareinc\\kenmyer" <br/> You need to supply the user password when running this command.  <br/> This parameter is not required if you are conducting the test using the health monitoring configuration settings.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |User credential object for the account to be tested. The value passed to UserCredential must be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credential object for the user litwareinc\\kenmyer and stores that object in a variable named <br/>  `$x = Get-Credential "litwareinc\\kenmyer"` <br/> You need to supply the user password when running this command. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for user account to be tested; for example:  <br/>  `-UserSipAddress "sip:kenmyer@litwareinc.com"` <br/> The UserSipAddress parameter must reference the same user account as UserCredential. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _HybridOnlineUserCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsXmppIM** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsXmppIM** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)
