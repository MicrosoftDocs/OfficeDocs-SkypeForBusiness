---
title: Revoke-CsClientCertificate
ms.prod: SKYPEFORBUSINESS
ms.assetid: 27d6d4d9-f8ed-4942-b7cf-dd308dafb5bc
---


# Revoke-CsClientCertificate
[]
Client certificates provide a way for users to be authenticated when logging on to Skype for Business Server 2015. Certificates are particularly useful for telephones and other devices running Skype for Business where it is difficult to enter a user name and/or password. The **Revoke-CsClientCertificate** cmdlet provides a way for administrators to revoke client certificates that have been issued to a user. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Revoke-CsClientCertificate -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 revokes all the client certificates currently assigned to Ken Myer; this is done by calling the **Revoke-CsClientCertificate** cmdlet followed by the Identity of the user whose certificates are to be revoked.
  
    
    

```

Revoke-CsClientCertificate -Identity "Ken Myer"
```


### EXAMPLE 2

Example 2 revokes all the client certificates that have been issued in your organization. To do this, the **Get-CsUser** cmdlet is first called in order to return a collection of all the users in your organization who have been enabled for Skype for Business Server 2015. This collection is then piped to the **Revoke-CsClientCertificate** cmdlet, which deletes the certificates for each user in the collection.
  
    
    

```
Get-CsUser | Revoke-CsClientCertificate
```


## Detailed Description

Client certificates provide an alternate way for users to be authenticated by Skype for Business Server 2015. Instead of providing a user name and password, users present the system with an X.509 certificate. (This certificate must have a subject name or subject alternative name that identifies the user.) To be authenticated, users only need to type in a personal identification number (PIN); it's typically easier for a mobile phone user to type in a PIN than to type in an alphanumeric user name and/or password.
  
    
    
At any time administrators can revoke the client certificates that have been issued to a user by using the **Revoke-CsClientCertificate** cmdlet. The **Revoke-CsClientCertificate** cmdlet revokes all the client certificates issued to the user in question from the server.
  
    
    
The **Revoke-CsClientCertificate** cmdlet does not delete certificates from the client device itself; certificates are only deleted from the server. However, this is sufficient to prevent a client from using certificates for authentication purposes: if a certificate cannot be found on the server than the authentication request will be denied.
  
    
    
Note that, by default, the firewall exceptions for SQL Server Express are not enabled when you install the Standard Edition of Skype for Business Server 2015. In turn, that means that you will not be able to run the **Revoke-CsClientCertificate** cmdlet from a remote instance of Windows PowerShell; that's because your command will not be able to traverse the firewall and access the SQL Server Express database. (However, you can still run the cmdlet locally; that is, on the Standard Edition server itself.) If you are using Standard Edition and need to run the **Revoke-CsClientCertificate** cmdlet remotely you must manually enable the firewall exceptions for SQL Server Express.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the Identity of the user account for which certificates are to be revoked. User Identities can be specified by using one of four formats: 1) the user's Session Initiation Protocol (SIP) address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\\logon (for example, litwareinc\\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). User Identities can also be referenced by using the user's Active Directory distinguished name.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

String value or Microsoft.Rtc.Management.ADConnect.Schema.ADUser object. The **Revoke-CsClientCertificate** cmdlet accepts pipelined input of string values representing the Identity of a user account. The cmdlet also accepts pipelined input of user objects.
  
    
    

## Return Types

None. Instead, the **Revoke-CsClientCertificate** cmdlet revokes instances of the Microsoft.Rtc.Management.UserPinService.CertInfoDetails object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsClientCertificate](get-csclientcertificate.md)
