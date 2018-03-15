---
title: "Revoke-CsSetupPermission"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3486d164-b1a2-4d4c-9150-cef802674682
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Revoke-CsSetupPermission
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Revokes the Lync Server setup rights that have been granted on an Active Directory organizational unit (OU). This cmdlet was introduced in Lync Server 2010.
  
```
Revoke-CsSetupPermission -ComputerOU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 revokes the setup rights applied to the CsServers OU in the domain litwareinc.com.
  
```
Revoke-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"
```

## Detailed Description
<a name="sectionSection1"> </a>

The domain preparation that takes place when you install Lync Server does not automatically add the rights that enable members of the RTCUniversalServerAdmins group to run the **Enable-CsTopology** cmdlet. That means that, by default, you must be a domain administrator in order to enable a topology. To give members of the RTCUniversalServerAdmins group the right to enable a topology, you must run the **Grant-CsSetupPermissions** cmdlet. In addition, you will need to run this cmdlet against each Active Directory container that hosts computers running Lync Server. 
  
Rights granted by using the **Grant-CsSetupPermission** cmdlet can later be removed by using the **Revoke-CsSetupPermission** cmdlet. If you run that cmdlet, the RTCUniversalServerAdmins group will no longer have Lync Server setup rights for the specified Active Directory container. In that case, you will need to be an enterprise administrator or a domain administrator in order to enable a Lync Server topology. 
  
Who can run this cmdlet: You must be a domain administrator in order to run the **Revoke-CsSetupPermission** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Revoke-CsSetupPermission"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerOU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name (DN) of the OU that contains the accounts for the computers where Lync Server will be (or has been) installed. For example: -ComputerOU "ou=CsServers,dc=litwareinc,dc=com".  <br/> If you prefer you can leave off the domain portion of the distinguished name when specifying the OU. For example:  <br/> -ComputerOU "ou=CsServers"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU is located. If this parameter is not included, then the **Revoke-CsSetupPermission** cmdlet will look for the OU in the current domain.  <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified name of the domain controller to be contacted when assigning the policy. For example: -DomainController atl-dc-001.litwareinc.com.  <br/> If not specified, the **Revoke-CsSetupPermission** cmdlet will contact the nearest available domain controller when assigning the policy.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified name of the global catalog server to be contacted when assigning the policy. For example: -GlobalCatalog atl-dc-001.litwareinc.com.  <br/> If not specified, the **Revoke-CsSetupPermission** cmdlet will contact the nearest available global catalog server when assigning the policy.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\OUPermissions.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Revoke-CsSetupPermission** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

None.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Grant-CsSetupPermission](grant-cssetuppermission.md)
  
[Test-CsSetupPermission](test-cssetuppermission.md)

