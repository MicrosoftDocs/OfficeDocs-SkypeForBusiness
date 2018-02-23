---
title: "Test-CsOUPermission"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9908eac9-765e-4406-bb6b-0e4dd07f85f8
description: "Verifies that the required permissions needed to manage users, computers, and other objects have been set on the specified Active Directory container. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsOUPermission
[]
Verifies that the required permissions needed to manage users, computers, and other objects have been set on the specified Active Directory container. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsOUPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 verifies that user permissions have been set on the Redmond OU in the litwareinc.com domain. 
  
```
Test-CsOUPermission -OU "ou=Redmond,dc=litwareinc,dc=com" -ObjectType "user"
```

## Detailed Description

If you have locked down your Active Directory domain (that is, if you have disabled permission inheritance), then the domain preparation that takes place when you install Skype for Business Server 2015 will not be able to add the permissions needed to manage users, computers, contacts, application contacts, and InetOrg persons. (Domain administrators will still be able to manage these objects, but no one else, including members of the RTCUniversalServerAdmins group, will have management permissions.) In that case, you will need to use the [Grant-CsOUPermission](grant-csoupermission.md) cmdlet to grant the RTCUniversalServerAdmins group the appropriate permissions. In addition, you will need to do this on a container-by-container basis.
  
The **Test-CsOUPermission** cmdlet enables you to determine whether or not the required permissions have been added to a specified Active Directory container. The **Test-CsOUPermission** cmdlet returns True if the correct permissions have been applied, and returns False if the correct permissions have not been applied. If the cmdlet returns False, you will then need to run the[Grant-CsOUPermission](grant-csoupermission.md) cmdlet in order to make the necessary changes.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ObjectType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.ObjectType  <br/> |Type of object to be checked. Valid values are:  <br/> User  <br/> Computer  <br/> Contact  <br/> AppContact  <br/> InetOrgPerson  <br/> To check multiple objects in the same kind, separate the object types by using commas:  <br/>  `-ObjectType "user","computer","contact"` <br/> |
| _OU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name of the organizational unit (OU) to be checked. For example:  <br/>  `-OU "ou=Redmond,dc=litwareinc,dc=com"` <br/> Note that you can only check a single OU per command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU to be checked is located. If this parameter is not included, then the **Test-CsOUPermission** cmdlet will look for the OU on the current domain. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller in your domain. This parameter is not required if you are running the **Test-CsOUPermission** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Test-CsOUPermission** cmdlet on a computer with an account in your domain. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\OUPermissions.html"` <br/> If this file already exists, it will be overwritten when you run the cmdlet.  <br/> |
   
## Input Types

None. The **Test-CsOUPermission** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsOUPermission** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Grant-CsOUPermission](grant-csoupermission.md)
  
[Revoke-CsOUPermission](revoke-csoupermission.md)

