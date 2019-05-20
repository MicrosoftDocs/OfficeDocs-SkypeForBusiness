---
title: "Set-CcExternalCertificateFilePath"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 443d071e-633e-4337-b20b-f30cdfbd4aaf
description: "The Set-CcExternalCertificateFilePath cmdlet specifies the path where the certificate for the Mediation Server or Edge Server is stored."
---

# Set-CcExternalCertificateFilePath
 
The Set-CcExternalCertificateFilePath cmdlet specifies the path where the certificate for the Mediation Server or Edge Server is stored.
  
This certificate is required during deployment or when adding new appliances of Skype for Business Cloud Connector Edition. The command also allows importing a new certificate for the Mediation Server after the deployment.
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Set-CcExternalCertificateFilePath [-Target] <string> {EdgeServer | MediationServer} [-Path] <string> [-Import]  [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example sets the path of the certificate for the Edge Server:
  
```
Set-CcExternalCertificateFilePath -Target EdgeServer -Path C:\CloudConnector\Certificates\AdatumPublicEdge.pfx
```

### Example 2

The next example sets the path of the certificate for the Mediation Server:
  
```
Set-CcExternalCertificateFilePath -Target MediationServer -Path C:\CloudConnector\Certificates\AdatumPublicMediation.pfx
```

### Example 3

The next example updates the certificate for the Mediation Server:
  
```
Set-CcExternalCertificateFilePath -Target MediationServer -Path C:\CloudConnector\Certificates\AdatumPublicMediation.pfx -Import
```

## Detailed Description
<a name="DetailedDescription"> </a>

During the deployment, or while modifying the topology, you need to specify the path for the Edge Server certificate, and optionally for the Mediation Server certificate. 
  
The certificate for the Mediation Server is required if TLS will be used between the gateway (s) and the Mediation Server. When you deploy a Cloud Connector appliance and want to deploy TLS, you can only specify the path to the certificate that will be deployed on the Mediation Server. However, if you want to update the Mediation certificate on an already deployed appliance, you need to specify the path and the -Import parameter. To see the path, use the Get-CCExternalCertificateFilePath cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Target <br/> | Required <br/> |System.String  <br/> |Type of file path requested. Types include:  <br/> EdgeServer (default)  <br/> MediationServer  <br/> |
|Import  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that the certificate must be imported to the Mediation Server. This parameter is not needed if you deploy an appliance for first time. The parameter is required if you want to change the existing certificate on an already deployed version.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CcExternalCertificateFilePath cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Get-CcExternalCertificateFilePath](get-ccexternalcertificatefilepath.md)
  

