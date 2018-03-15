---
title: "Grant-CsOUPermission"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26d8bdbf-abf0-4ca3-b9ab-fbb355fbcca1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Grant-CsOUPermission
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Grants Lync Server management rights on an Active Directory organizational unit (OU). This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 grants user management rights (-ObjectType "user") to the Redmond OU in the domain litwareinc.com.
  
```
Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"
```

### EXAMPLE 2

In Example 2, management rights are granted for three different objects (user, contact, inetOrgPerson) for the Redmond OU in the domain litwareinc.com.
  
```
Grant-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user","contact","inetOrgPerson"
```

### EXAMPLE 3

In Example 3, user management rights are simultaneously granted for three different OUs: Redmond, Dublin, and Tokyo. To carry out this task, the first command in the example creates an array variable named $x; this variable holds the distinguished names of the three Active Directory OUs where rights will be granted. In the second command, a foreach loop is created that takes each OU stored in the array and runs the **Grant-CsOUPermission** cmdlet against that organizational unit. In turn, that command grants user management rights for each OU in the array. 
  
```
$x = "ou=Redmond,dc=litwareinc,dc=com", "ou=Dublin,dc=litwareinc,dc=com", "ou=Tokyo,dc=litwareinc,dc=com"
foreach ($i in $x) {Grant-CsOUPermission -OU $i -ObjectType "user"}
```

## Detailed Description
<a name="sectionSection1"> </a>

If you have locked down your Active Directory domain (that is, if you have disabled permission inheritance) then the domain preparation that takes place when you install Lync Server will not be able to add the rights needed to manage users, computers, contacts, application contacts, and InetOrg persons. (Domain administrators will still be able to manage these objects, but no one else, including members of the RTCUniversalUserAdmins group, will have management rights.) In that case, you will need to use the **Grant-CsOUPermission** cmdlet to give the required security groups the required rights. This must be done on a container-by-container basis. 
  
Note that this cmdlet only grants rights to a set of predefined security groups; the cmdlet cannot be used to grant rights to arbitrary security groups or to individual users.
  
Rights granted by using the **Grant-CsOUPermission** cmdlet can later be removed by using the **Revoke-CsOUPermission** cmdlet. If you run that cmdlet, then the groups initially granted the OU rights will no longer have those Lync Server management rights for the specified Active Directory container. In that case, you will need to be an enterprise administrator or a domain administrator in order to manage Lync Server or one of its components. 
  
Who can run this cmdlet: You must be a domain administrator in order to run the **Grant-CsOUPermission** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Grant-CsOUPermission"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ObjectType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.ObjectType  <br/> |Type of object covered by these rights. Valid values are:  <br/> User  <br/> Computer  <br/> Contact  <br/> AppContact  <br/> InetOrgPerson  <br/> Device (required for creating common area phones)  <br/> To assign multiple object types in the same command, separate the object types by using commas: -ObjectType "user","computer","contact". Note, however, that you can only specify a maximum of three object types per command.  <br/> |
| _OU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name of the OU where rights are to be granted. For example: -OU "ou=Redmond,dc=litwareinc,dc=com".Note that you can only grant rights to a single OU per command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU is located. If this parameter is not included, then the **Grant-CsOUPermission** cmdlet will look for the OU on the current domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables administrators to specify the fully qualified domain name (FQDN) of the domain controller to be used when running the **Grant-CsOUPermission** cmdlet. If not specified, the cmdlet will use the first available domain controller.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Grant-CsOUPermission** cmdlet on a computer with an account in your domain.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\OUPermissions.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Grant-CsOUPermission** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Grant-CsOUPermission** cmdlet does not return any objects or values. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Revoke-CsOUPermission](revoke-csoupermission.md)
  
[Test-CsOUPermission](test-csoupermission.md)

