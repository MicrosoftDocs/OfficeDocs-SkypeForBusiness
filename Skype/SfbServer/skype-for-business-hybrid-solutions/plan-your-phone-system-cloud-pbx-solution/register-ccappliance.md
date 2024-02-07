---
title: "Register-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/18/2017
audience: ITPro
ms.topic: conceptual
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 01eed3c5-af68-4db7-90b3-d28ebe7ffef1
description: "The Register-CcAppliance cmdlet registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Skype for Business Cloud Connector Edition management service."
---

# Register-CcAppliance
 
The Register-CcAppliance cmdlet registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Skype for Business Cloud Connector Edition management service.
  
```powershell
Register-CcAppliance [[-SiteName] <string>] [[-ApplianceName] <string>] [-Local]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example registers the current appliance information to an online tenant configuration:
  
```powershell
Register-CcAppliance
```

### Example 2

The next example checks configuration for registration locally without connecting to an online tenant configuration:
  
```powershell
Register-CcAppliance -Local
```

### Example 3

The next example registers the current appliance with the name "Appliance1" to the PSTN site "Site1":
  
```powershell
Register-CcAppliance -SiteName Site1 -ApplianceName Appliance1
```

## Detailed Description
<a name="DetailedDescription"> </a>

You must provide the tenant admin account name and password. Use the account you created for Cloud Connector online management. 
  
In release 1.4.2 and earlier, follow the instructions to provide the external certificate password, safe mode admin password, domain admin password, and VM admin password. 
  
In release 2.0 and later, follow the instructions to provide the external certificate password, CceService password and CABackupFile password.
  
At the end of registration, restart the Cloud Connector management service and sign-in the services as CceService account.
  
SiteName combined with the Microsoft Edge Server external FQDN in the CloudConnector.ini file is considered a PSTN site identity. If neither the SiteName nor the Microsoft Edge Server external FQDN is used to register a site, a new site is created for this appliance in an online tenant configuration. If a PSTN site identity is found, a PSTN site uses this identity and the appliance is registered to this PSTN site. 
  
In the following situation, the cmdlet fails and indicates that Site1 is already registered: 
  
- SiteName is Site1 and the Microsoft Edge Server external FQDN is edgserver1.contoso.com. 
    
- A PSTN site whose SiteName is Site1 and Microsoft Edge Server external FQDN is edgserver.contoso.com.
    
- A PSTN site whose SiteName is NewSite and Microsoft Edge Server external FQDN is edgserver1.contoso.com is registered.
    
ApplianceName combined with the Mediation Server FQDN in CloudConnector.ini file is considered an Appliance Identity. If the ApplianceName nor the Mediation Server FQDN has been used to register an appliance, a new appliance is created in the online tenant configuration. If the appliance is already registered, the cmdlet fails.
  
In the following situation, the cmdlet fails and indicates that the appliance is already registered: 
  
- ApplianceName is Appliance1 and Mediation server FQDN is ms1.vdomain.com.
    
- In the current PSTN site, if an appliance whose name Appliance1 and Mediation Server FQDN are ms.vdomain.com or an appliance whose name NewAppliance and Mediation server FQDN are ms1.vdomain.com is registered.
    
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|SiteName  <br/> |Optional  <br/> |System.String  <br/> |PSTN site name to which the appliance is registered. Default value is SiteName value in the CloudConnector.ini file.  <br/> |
|ApplianceName  <br/> |Optional  <br/> |System.String  <br/> |Name of the current appliance. Default value is the computer name of the host server.  <br/> |
|Local  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Check configurations for registration locally without connecting to online tenant configuration.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Register-CcAppliance cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Unregister-CcAppliance](unregister-ccappliance.md)
  
[Publish-CcAppliance](publish-ccappliance.md)
  
[Install-CcAppliance](install-ccappliance.md)
  
[Uninstall-CcAppliance](uninstall-ccappliance.md)
  

