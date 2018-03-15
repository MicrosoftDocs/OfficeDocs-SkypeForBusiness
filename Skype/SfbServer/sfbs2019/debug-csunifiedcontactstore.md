---
title: "Debug-CsUnifiedContactStore"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8e92d262-604d-41b1-9530-947765025a79
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Debug-CsUnifiedContactStore
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies whether the contacts for a user (or group of users) are stored in the unified contacts store.
  
 This cmdlet was introduced in the Cumulative Updates for Lync Server 2013: February 2013. 
  
```
Debug-CsUnifiedContactStore -Identity <UserIdParameter> [-ContactDataExportFileName <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies the unified contact store status for all the users who have accounts homed on the pool atl-cs-001.litwareinc.com.
  
```
Debug-CsUnifiedContactStore -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

In Example 2, the unified contact store status is verified for a single user: the user with the SIP address "kenmyer@litwareinc.com".
  
```
Debug-CsUnifiedContactStore -Identity "kenmyer@litwareinc.com"
```

## Detailed Description
<a name="sectionSection1"> </a>

The unified contact store (introduced in Lync Server 2013 enables users to access their contact list from multiple applications, including Microsoft Lync 2013, Outlook 2013, and Outlook Web App. This access is made available by storing contact information in a single location: Microsoft Exchange Server 2013.
  
The **Debug-CsUnifiedContactStore** cmdlet enables administrators to verify whether a specific user or a specific set of users (that is, all the users with accounts homed in a particular pool) have their contact lists stored in the unified contact store. If you run the **Debug-CsUnifiedContactStore** cmdlet against a specific user account, the cmdlet will indicate whether that user's contacts have been moved for the unified contact store, the number of attempts that have been made to move those contacts, and the date and time when Lync Server last tried to migrate the contact list. When called against a pool, the **Debug-CsUnifiedContactStore** cmdlet returns data similar to this: 
  
FrontEnd: atl-cs-001.litwareinc.com 
  
UcsDisabledCount: 44
  
UcsAllowedCount: 129
  
UcsMigratingCount: 11
  
UcsMigratedCount: 
  
FailedUserData:
  
The **Debug-CsUnifiedContactStore** cmdlet, and the ContactDataExportFileName parameter, can also be used to export contact information for a user to an XML file. 
  
To return a list of all the role-based access control (RBAC) roles that this cmdlet has been assigned to (including any custom RBAC roles that you have created), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Debug-CsUnifiedContactStore"}
  
 **Lync Server Control Panel:** The functions carried out by the **Debug-CsUnifiedContactStore** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |SIP address of an individual user whose unified contact store status is being verified. (You can specify only one user per command.) For example:  <br/> -Identity "kenmyer@litwareinc.com"  <br/> When specifying the SIP address, the sip: prefix is optional. This syntax will also work:  <br/> -Identity "sip:kenmyer@litwareinc.com"  <br/> |
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the Registrar pool whose unified contact store status is being verified. All user accounts homed on the specified pool will be checked. For example:  <br/> -PoolFqdn "atl-cs-001.litwareinc.com"  <br/> |
| _ContactDataExportFileName_ <br/> |Optional  <br/> |System.String  <br/> |File path for the XML file that will contain the contacts for the specified user when those contacts exported from the unified contact store. For example:  <br/> -ContactDataExportFileName "C:\Exports\KenMyer.xml"  <br/> Note that you must include the Identity parameter and the SIP address for the user whose contacts you want to export. If that user has not been enabled for the unified contact store, the command will terminate and no contacts will be exported.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any nonfatal error message that might occur when running the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Debug-CsUnifiedContactStore** cmdlet does not accept pipelined data. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Debug-CsUnifiedContactStore** cmdlet returns instances of the Microsoft.Rtc.Management.Presence.Cmdlets.GetUcsFrontEndData object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)

