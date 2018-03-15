---
title: "Debug-CsAddressBookReplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c138f274-7a1f-4074-b6a2-548274af5199
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Debug-CsAddressBookReplication
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies replication between Active Directory and the Lync Server 2013 Address book service. This cmdlet was introduced in Lync Server 2013.
  
```
Debug-CsAddressBookReplication [-DomainController <String>] [-User <String>] [-VerifyReplication <SwitchParameter>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PoolFqdn <Fqdn>] [-VerifyNormalization <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies Address book replication for the current pool. To verify replication for a specified pool, include the PoolFqdn parameter followed by the fully qualified domain name of the pool to be verified.
  
```
Debug-CsAddressBookReplication
```

### Example 2

In Example 2, the User parameter is included when verifying Address book replication for the current pool. When the User parameter is included, additional related information is returned for the specified user.
  
```
Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com"
```

### Example 3

Example 3 uses the VerifyReplication parameter to make a change to the specified user account and then verify that this change can be successfully replicated to the Address Book.
  
```
Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com" -VerifyReplication 
```

### Example 4

The command shown in Example 4 uses the VerifyNormalization parameter to return information about user accounts where Address Book normalization rules could not be applied.
  
```
Debug-CsAddressBookReplication -VerifyNormalization
```

## Detailed Description
<a name="DetailedDescription"> </a>

Address Book servers are intermediaries between Active Directory Domain Services (AD DS) and Microsoft Lync Server. The Address Book server ensures that the user information stored in Lync Server is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database.
  
The **Debug-CsAddressBookReplication** cmdlet enables administrators to verify that data is being replicated between Active Directory and Lync Server. Fully testing replication between Active Directory and the Address Book server can potentially be time-consuming and resource-intensive; because of that, it is recommended that **Debug-CsAddressBookReplication** only be used in troubleshooting scenarios. If you want to periodically "spot check" the functioning of your Address Book server you should use the **Test-CsAddressBookService** cmdlet and/or the **Test-CsAddressBookWebQuery** cmdlet instead. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Debug-CsAddressBookReplication"}
  
 **Lync Server Control Panel:** The functions carried out by the D **ebug-CsAddressBookReplication** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DomainController_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a domain controller to connect to when verifying Address book replication. If this parameter is not included then the cmdlet will use the first available domain controller.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _PoolFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool being checked. If this parameter is not included then the **Debug-CsAddressBookReplication** cmdlet will verify the current pool.  <br/> |
| _User_ <br/> |Optional  <br/> |System.String  <br/> |When included, returns detailed replication information for the specified user accounts. The user account to be verified can be specified by using the user's SIP address, email address, or SamAccountName.  <br/> |
| _VerifyNormalization_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If specified, detailed information will be returned for any user accounts where Address book normalization failed. Normalization rules are used to convert phone numbers to the E.164 format used by Lync Server 2013.  <br/> |
| _VerifyReplication_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, the **Debug-CsAddressBookReplication** cmdlet will modify the specified user account in Active Directory and then verify that the changes are replicated to the Address book. Note that the user account modification is for testing purposes only, and will not actually change the property values of that account.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Debug-CsAddressBookReplication** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Debug-CsAddressBookReplication** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.Activities.Database.AddressBookReplicationTaskOutput object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsAddressBookService](test-csaddressbookservice.md)
  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

