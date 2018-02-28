---
title: "Grant-CsSetupPermission"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 753bccc1-edb4-48c9-bd0a-2db5d86f8c5e
description: "Grants Skype for Business Server 2015 setup permissions on an Active Directory organizational unit (OU). This cmdlet was introduced in Lync Server 2010."
---

# Grant-CsSetupPermission
[]
Grants Skype for Business Server 2015 setup permissions on an Active Directory organizational unit (OU). This cmdlet was introduced in Lync Server 2010.
  
```
Grant-CsSetupPermission -ComputerOU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 grants setup permissions for the CsServers OU in the domain litwareinc.com.
  
```
Grant-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"
```

## Detailed Description

The domain preparation that takes place when you install Skype for Business Server 2015 does not automatically add the permissions that enable members of the RTCUniversalServerAdmins group to run the **Enable-CsTopology** cmdlet. That means that, by default, you must be a domain administrator in order to enable a topology. To give members of the RTCUniversalServerAdmins group the right to enable a topology you must run the **Grant-CsSetupPermissions** cmdlet. In addition, you will need to run this cmdlet against each Active Directory container that houses computers running Skype for Business Server 2015.
  
Keep in mind that this cmdlet only grants permissions to the RTCUniversalServerAdmins group; the cmdlet cannot be used to grant permissions to other security groups or to individual users.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ComputerOU_ <br/> |Required  <br/> |System.String  <br/> |Distinguished name of the OU containing the accounts for the computers where Skype for Business Server 2015 will be (or has been) installed. For example: "ou=CsServers,dc=litwareinc,dc=com".  <br/> If you prefer you can leave off the domain portion of the distinguished name when specifying the OU. For example:  <br/>  `-ComputerOU "ou=CsServers"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Domain_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Name of the domain where the OU is located. If this parameter is not included, then the **Grant-CsSetupPermission** cmdlet will look for the OU in the current domain. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified name of the domain controller to be contacted when assigning the policy. For example:  <br/>  `-DomainController atl-dc-001.litwareinc.com` <br/> If not specified, the **Grant-CsSetupPermission** cmdlet will contact the nearest available domain controller when assigning the policy. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified name of the global catalog server to be contacted when assigning the policy. For example:  <br/>  `-GlobalCatalog atl-dc-001.litwareinc.com` <br/> If not specified, the **Grant-CsSetupPermission** cmdlet will contact the nearest available global catalog server when assigning the policy. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\SetupPermissions.html"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Grant-CsSetupPermission** cmdlet does not accept pipelined input.
  
## Return Types

None. The **Grant-CsSetupPermission** cmdlet does not return any objects or values.
  
## See also

#### 

[Revoke-CsSetupPermission](revoke-cssetuppermission.md)
  
[Test-CsSetupPermission](test-cssetuppermission.md)

