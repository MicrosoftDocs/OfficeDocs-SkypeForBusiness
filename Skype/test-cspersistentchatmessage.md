---
title: Test-CsPersistentChatMessage
ms.prod: SKYPEFORBUSINESS
ms.assetid: 08c6db0b-23e2-4fbe-8276-181275a40daf
---


# Test-CsPersistentChatMessage
[]
Verifies whether or not a pair of users can exchange messages using the Persistent Chat service (formerly known as the Group Chat service). This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Test-CsPersistentChatMessage -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The commands shown in Example 2 test the ability of a pair of users (litwareinc\\pilar and litwareinc\\kenmyer) to log on to Skype for Business Server 2015 and then exchange messages using the Persistent Chat service. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\\pilar, has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
    
    
With the credential objects in hand, the third command determines whether or not these two users can log on to Skype for Business Server 2015 and exchange messages using Persistent Chat. To carry out this task, the **Test-CsPersistentChatMessage** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SenderSipAddress (the SIP address for the first test user); SenderCredential (the Windows PowerShell object containing the credentials for this same user); ReceiverSipAddress (the SIP address for the other test user); and ReceiverCredential (the Windows PowerShell object containing the credentials for the other test user).
  
    
    



```

$cred1 = Get-Credential "litwareinc\\pilar"
$cred2 = Get-Credential "litwareinc\\kenmyer"

Test-CsPersistentChatMessage -TargetFqdn atl-persistentchat-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2
```


## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsPersistentChatMessage** cmdlet verifies that a pair of test users is able to exchange messages using the Persistent Chat service. To do this, the cmdlet logs the two users on to Skype for Business Server 2015, connects the users to a persistent Chat room, exchanges a pair of messages, then exits the chat room and logs off the two users. Note that calls to this cmdlet will fail if you have not created any chat rooms or if the two test user accounts have not been assigned a Persistent Chat policy that gives them access to the Persistent Chat service.
  
    
    
 **Skype for Business Server Control Panel **: The functions carried out by the **Test-CsPersistentChatMessage** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ReceiverCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the first of the two user accounts to be tested. The value passed to ReceiverCredential should be an object reference obtained by using the Get-Credential cmdlet. For example, this code returns a credentials object for the user litwareinc\\pilar and stores that object in a variable named $y:  <br/>  `$y = Get-Credential "litwareinc\\pilar"` <br/> You need to supply the user password when running this command.  <br/> The receiver credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _SenderCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to SenderCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> TrustedServer  <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _ChatRoomUri_ <br/> |Optional  <br/> |System.String  <br/> |Chat room location, consisting of the fully qualified domain name of the Persistent Chat Server and the name of the chat room. For example:  <br/>  `-ChatRoomIdentity "atl-persistentchat-001.litwareinc.com\\ITChatRoom"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput. ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput. ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ReceiverSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/>  `-ReceiverSipAddress "sip:pilar@litwareinc.com"` <br/> The ReceiverSIPAddress parameter must reference the same user account as ReceiverCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SenderSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  <br/>  `-SenderSipAddress "sip:kenmyer@litwareinc.com"` <br/> The SenderSipAddress parameter must reference the same user account as SenderCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _Setup_ <br/> |Optional  <br/> |System.Boolean  <br/> |Enables the cmdlet to be run on a watcher node computer that does not have access to the Skype for Business Server 2015 topology. To allow for this, first run the **Test-CsPersistentChatMessage** along with the Setup parameter from a computer which does have access to the topology. After that, you will be able to run the cmdlet on your watcher node computers. <br/> If you use the Setup parameter you must also use the TestUser1SipAddress and TestUser2SipAddress parameters.  <br/> |
| _TestUser1SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address of the first test user used in conjunction with the Setup parameter.  <br/> |
| _TestUser2SipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address of the second test user used in conjunction with the Setup parameter.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsPersistentChatMessage** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsPersistentChatMessage** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)
  
    
    
 [New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)
  
    
    
 [Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)
