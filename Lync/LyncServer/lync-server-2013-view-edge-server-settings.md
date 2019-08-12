---
title: 'Lync Server 2013: View Edge Server settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: View Edge Server settings
ms:assetid: 684154cc-cffc-4d2e-8baa-be52c625e5d7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn747890(v=OCS.15)
ms:contentKeyID: 63969612
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View Edge Server settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-20_

General Edge Server configurations should be reviewed against the data in the configuration management database—to help guarantee that all changes were documented as per the defined change control procedures.

Additional checks could include those that are described in the following sections:

<div>

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

</div>

<div>

## Verify multiple Edge Servers are identical

If multiple Edge Servers are deployed in a load balanced array, we recommend verifying that all Edge Servers in the array are configured in the same manner.

You can view settings for Edge Servers in the details pane of the Lync Server 2013 extension for the Computer Management snap-in.

</div>

<div>

## See Also


[Get-CsAllowedDomain](https://docs.microsoft.com/powershell/module/skype/Get-CsAllowedDomain)  
[Get-CsBlockedDomain](https://docs.microsoft.com/powershell/module/skype/Get-CsBlockedDomain)  
[Test-CsFederatedPartner](https://docs.microsoft.com/powershell/module/skype/Test-CsFederatedPartner)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

