---
title: "View Edge Server settings in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 684154cc-cffc-4d2e-8baa-be52c625e5d7
description: "General Edge Server configurations should be reviewed against the data in the configuration management database—to help guarantee that all changes were documented as per the defined change control procedures."
---

# View Edge Server settings in Lync Server 2013
[]
General Edge Server configurations should be reviewed against the data in the configuration management database—to help guarantee that all changes were documented as per the defined change control procedures.
  
Additional checks could include those that are described in the following sections:
  
## Verify the Allow and block lists

Verify the SIP URI "Allow" and "Block" lists for Federated domains—to determine whether listed namespaces are still valid.
  
You can use Windows PowerShell to view the allowed and blocked lists. To review the domains on the Allowed Domains list, run the following Windows PowerShell command:
  
 `Get-CsAllowedDomain`
  
That command returns information similar to this for the domains on the Allowed Domains list:
  
Identity : contoso.com
  
Domain : contoso.com
  
ProxyFqdn :
  
Comment :
  
MarkForMonitoring : False
  
Comment :
  
To review the domains on the blocked domains list, use this command:
  
 `Get-CsBlockedDomain`
  
In turn, you'll receive information such as this for each blocked domain:
  
Identity : tailspintoys.com
  
Domain : tailspintoys.com
  
Windows PowerShell also enables you to verify that you can connection to the domains on your Allowed Domains list. For example, this command verifies the connection between your Edge Server (the TargetFqdn) and the federated domain contoso.com:
  
 `Test-CsFederatedPartner -TargetFqdn "atl-edge-001.litwareinc.com" -Domain "contoso.com"`
  
And this command verifies the connection between your Edge Server and all of the domains found on your Allowed Domains list:
  
 `Get-CsAllowedDomain | ForEach-Object {Test-CsFederatedPartner -TargetFqdn "atl-edge-001.litwareinc.com" -Domain $_.Domain}`
  
## Verify multiple Edge Servers are identical

If multiple Edge Servers are deployed in a load balanced array, we recommend verifying that all Edge Servers in the array are configured in the same manner.
  
You can view settings for Edge Servers in the details pane of the Lync Server 2013 extension for the Computer Management snap-in.
  
## See also

#### 

[Get-CsAllowedDomain](get-csalloweddomain.md)
  
[Get-CsBlockedDomain](get-csblockeddomain.md)
  
[Test-CsFederatedPartner](test-csfederatedpartner.md)

