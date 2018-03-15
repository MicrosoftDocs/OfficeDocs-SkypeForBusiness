---
title: "Revoke-CsOUPermission"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de0542c9-6d11-4038-9b4a-757338d61fae
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Revoke-CsOUPermission
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Revokes the Lync Server management permissions that have been granted on an Active Directory organizational unit (OU). This cmdlet was introduced in Lync Server 2010.
  
```
Revoke-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 revokes user management permissions (-ObjectType "user") for the Redmond OU in the domain litwareinc.com.
  
```
Revoke-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"
```

### EXAMPLE 2

In Example 2, three different management permissions (user, contact, and inetOrgPerson objects) are removed from the Redmond OU in the domain litwareinc.com.
  
```
Revoke-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user","contact","inetOrgPerson"
```

## Detailed Description
<a name="sectionSection1"> </a>

If you have locked down your Active Directory domain (that is, if you have disabled permission inheritance) then the domain preparation that takes place when you install Lync Server will not be able to add the permissions needed to manage users, computers, contacts, application contacts, and InetOrg persons. (Enterprise administrators and domain administrators will still be able to manage these objects, but no one else, including members of the RTCUniversalServerAdmins group, will have management permissions.) In that case, you will need to use the **Grant-CsOUPermission** cmdlet to grant the required security groups the required permissions. This must be done on a container-by-container basis for each Active Directory container that includes Lync Server user accounts. 
  
Permissions granted by using the **Grant-CsOUPermission** cmdlet can later be removed by using **Revoke-CsOUPermission**. If you run the **Revoke-CsOUPermission** cmdlet against an OU you will then need to be an enterprise administrator or a domain administrator in order to manage Lync Server users in that OU. 
  
Who can run this cmdlet: You must be a domain administrator in order to run the **Revoke-CsOUPermission** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Revoke-CsOUPermission"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ObjectType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.ObjectType  <br/> |Type of object covered by these permissions. Valid values are:  <br/> User  <br/> Computer  <br/> Contact  <br/> AppContact  <br/> InetOrgPerson  <br/> To revoke permissions to multiple object types in the same command, separate the object types by using commas: -ObjectType "user","computer","contact".  <br/> |
| _OU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name of the OU where permissions are to be removed. For example: -OU "ou=Redmond,dc=litwareinc,dc=com".You can only remove permissions from a single OU per command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU is located. If this parameter is not included the **Revoke-CsOUPermission** cmdlet will look for the OU in the current domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the fully qualified domain name (FQDN) of the domain controller to be used when running the **Revoke-CsOUPermission** cmdlet. If not specified, the cmdlet will use the first available domain controller.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of a global catalog server in your domain. This parameter is not required if you are running the **Revoke-CsOUPermission** cmdlet on a computer with an account in your domain.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\OUPermissions.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Revoke-CsOUPermission** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Revoke-CsOUPermission** cmdlet does not return any objects or values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Grant-CsOUPermission](grant-csoupermission.md)
  
[Test-CsOUPermission](test-csoupermission.md)

