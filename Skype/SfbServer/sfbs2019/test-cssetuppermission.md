---
title: "Test-CsSetupPermission"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 604ccb97-278a-4588-9ab8-991aaabae275
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsSetupPermission
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies that the required permissions needed to install Lync Server or one of its components have been configured on the specified Active Directory container. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsSetupPermission -ComputerOU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 checks to see if the required setup permissions have been applied to the CsServers OU in the litwareinc.com domain.
  
```
Test-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"
```

## Detailed Description
<a name="sectionSection1"> </a>

The domain preparation that takes place when you install Lync Server does not automatically add the permissions that enable members of the RTCUniversalServerAdmins group to run the **Enable-CsTopology** cmdlet. That means that, by default, you must be a domain administrator in order to enable a topology. To give members of the RTCUniversalServerAdmins group the right to enable a topology, you must run the **Grant-CsSetupPermissions** cmdlet. In addition, you will need to run this cmdlet against each Active Directory container that houses computers running Lync Server. 
  
The **Test-CsSetupPermission** cmdlet enables you to determine whether or not the requisite permissions have been added to a given Active Directory container (that is, a container hosting computers running Lync Server). The **Test-CsSetupPermission** cmdlet returns True if the correct permissions have been applied, and returns False if the correct permissions have not been applied. If the cmdlet returns False, you will need to run the **Grant-CsSetupPermission** cmdlet in order to make the necessary changes to the Active Directory container. 
  
Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsSetupPermission"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerOU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name of the organizational unit (OU) that contains the accounts for the computers running Lync Server. For example: "ou=CsServers,dc=litwareinc,dc=com".  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU to be checked is located. If this parameter is not included, then the **Test-CsSetupPermission** cmdlet will look for the OU in the current domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller in your domain. This parameter is not required if you are running the **Test-CsSetupPermission** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Test-CsSetupPermission** cmdlet on a computer with an account in your domain.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Reports detailed activity to the screen as the cmdlet runs.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Test-CsSetupPermission** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsSetupPermission** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Grant-CsSetupPermission](grant-cssetuppermission.md)
  
[Revoke-CsSetupPermission](revoke-cssetuppermission.md)

