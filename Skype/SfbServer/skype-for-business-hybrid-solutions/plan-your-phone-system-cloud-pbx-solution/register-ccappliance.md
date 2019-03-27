---
title: "Register-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/18/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 01eed3c5-af68-4db7-90b3-d28ebe7ffef1
description: "The Register-CcAppliance cmdlet registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Skype for Business Cloud Connector Edition management service."
---

# Register-CcAppliance
 
The Register-CcAppliance cmdlet registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Skype for Business Cloud Connector Edition management service.
  
```
Register-CcAppliance [[-SiteName] <string>] [[-ApplianceName] <string>] [-Local]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example registers the current appliance information to an online tenant configuration:
  
```
Register-CcAppliance
```

### Example 2

The next example checks configuration for registration locally without connecting to an online tenant configuration:
  
```
Register-CcAppliance -Local
```

### Example 3

The next example registers the current appliance with the name "Appliance1" to the PSTN site "Site1":
  
```
Register-CcAppliance -SiteName Site1 -ApplianceName Appliance1
```

## Detailed Description
<a name="DetailedDescription"> </a>

You must provide the tenant admin account name and password. Use the account you have created for Cloud Connector online management. 
  
In release 1.4.2 and earlier, follow the instructions to provide the external certificate password, safe mode admin password, domain admin password, and VM admin password. 
  
In release 2.0 and later, follow the instructions to provide the external certificate password, CceService password and CABackupFile password.
  
At the end of registration, restart the Cloud Connector management service and log on to the services as CceService account.
  
SiteName combined with the Edge Server external FQDN in the CloudConnector.ini file is considered a PSTN site identity. If neither the SiteName nor the Edge Server external FQDN has been used to register a site, a new site will be created for this appliance in an online tenant configuration. If a PSTN site identity is found, a PSTN site will use this identity and the appliance will be registered to this PSTN site. 
  
In the following situation, the cmdlet will fail and indicate that Site1 is already registered: 
  
- SiteName is Site1 and the Edge Server external FQDN is edgserver1.contoso.com. 
    
- A PSTN site whose SiteName is Site1 and Edge Server external FQDN is edgserver.contoso.com.
    
- A PSTN site whose SiteName is NewSite and Edge Server external FQDN is edgserver1.contoso.com has been registered. 
    
ApplianceName combined with the Mediation Server FQDN in CloudConnector.ini file is considered an Appliance Identity. If neither the ApplianceName nor the Mediation Server FQDN has been used to register an appliance, a new appliance will be created in the online tenant configuration. If the appliance is already registered, the cmdlet will fail.
  
In the following situation, the cmdlet will fail and indicate that the appliance is already registered: 
  
- ApplianceName is Appliance1 and Mediation server FQDN is ms1.vdomain.com.
    
- In the current PSTN site, if an appliance whose name Appliance1 and Mediation Server FQDN is ms.vdomain.com or an appliance whose name NewAppliance and Mediation server FQDN is ms1.vdomain.com has been registered.
    
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
  

