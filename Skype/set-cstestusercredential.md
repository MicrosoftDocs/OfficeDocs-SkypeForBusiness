---
title: Set-CsTestUserCredential
ms.prod: SKYPEFORBUSINESS
ms.assetid: e613fad9-e91b-4bce-a67d-b1c9860ab34d
---


# Set-CsTestUserCredential
[]
Creates a new watcher node test user. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Skype for Business Server 2015 synthetic transactions to verify that Skype for Business Server 2015 components are working as expected. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsTestUserCredential -Credential <PSCredential> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 configures the user with the SIP address sip:kenmyer@litwareinc.com to be a watcher node test user. Note that you must also supply the user name (in the form domain name\\user name) and the user's password when you configure an account as a watcher node test user.
  
    
    

```

Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -UserName "litwareinc\\kenmyer" -Password "07Apples"
```


### Example 2

The commands shown in the preceding example also configure the user with the SIP address sip:kenmyer@litwareinc.com to be a watcher node test user; in this case, however, the Credential parameter is used instead of the UserName and Password parameters. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the account litwareinc\\kenmyer; that credentials object is then stored in a variable named $x. (Note that you must supply the password for the litwareinc\\kenmyer account when creating the credentials object.) The second command in the example then uses the Credential parameter and the parameter value $x to configure the test credentials.
  
    
    

```
$x = Get-Credential "litwareinc\\kenmyer"

Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -Credential $x
```


## Detailed Description
<a name="DetailedDescription"> </a>

If you are using System Center Operations Manager in conjunction with Skype for Business Server 2015, you have the option of configuring "watcher node" computers. Watcher nodes are computers that periodically (and automatically) run synthetic transactions. Synthetic transactions are cmdlets that test various features of Skype for Business Server 2015; for example, there are synthetic transactions that verify that users can register with Skype for Business Server 2015; that users can exchange instant messages and presence information using Skype for Business Server 2015; that users can conduct data collaboration and application sharing conferences; and that users can make phone calls across the public switched telephone network. As noted, these synthetic transactions run periodically and, if they fail, issue alerts notifying administrators that the system might be experiencing difficulties.
  
    
    
Many synthetic transactions require test users; for example, you cannot test the ability of two users to exchange instant messages unless you have a pair of user accounts and you attempt to exchange instant messages using those accounts. When you configure a watcher node you must assign at least two test users to that node. These test users can be any valid Active Directory user accounts that have been enabled for Skype for Business Server 2015 and have been registered as test accounts. Accounts are registered as test accounts by using the **Set-CsTestUserCredential** cmdlet. If you later decide not to use an account as a test account you can unregister the by using the [Remove-CsTestUserCredential](remove-cstestusercredential.md) cmdlet. This cmdlet simply prevents the account from being used as a watcher node test account; it does not delete, disable, or otherwise modify the account.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsTestUserCredential** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Credential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |Enables you to configure test credentials by using a Windows PowerShell credentials object rather than the Password and UserName parameters; this has the advantage of ensuring that the user password is masked when you type it onscreen.  <br/> To use the Credential parameter you must first create a PSCredential object using the **Get-Credential** cmdlet and then store the resulting object in a variable. For example: <br/> $x = Get-Credential "litwareinc\\kenmyer"  <br/> That variable is then used as the parameter value for the Credential parameter.  <br/> |
| _Password_ <br/> |Required  <br/> |System.String  <br/> |Password for the account whose test user credentials are being set. (Note that this password will be displayed onscreen in plain text.) For example:  <br/>  `-Password "p@ssw0rd"` <br/> You do not need to use the Password or the UserName parameters if you use the Credential parameter.  <br/> |
| _SipAddress_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the account whose test user credentials are being set. For example:  <br/>  `-SipAddress "sip:kenmyer@litwareinc.com"` <br/> |
| _UserName_ <br/> |Required  <br/> |System.String  <br/> |User name of the account being configured for test credentials. The user name can be the SamAccountName or Active Directory DisplayName; for example:  <br/>  `-UserName "Ken Myer"` <br/> You can also specify the UserName by using the format domain name\\user name. For example:  <br/>  `-UserName "litwareinc\\kenmyer"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Set-CsTestUserCredential** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsTestUserCredential** cmdlet modifies existing instances of the System.Management.Automation.PSCredential object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsTestUserCredential](get-cstestusercredential.md)
  
    
    
 [Remove-CsTestUserCredential](remove-cstestusercredential.md)
