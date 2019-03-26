---
title: 'Lync Server 2013: Modify the global hosted voice mail policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Modify the global hosted voice mail policy
ms:assetid: f059b3ce-a7d8-4ea9-b10b-0052222ec2ce
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412994(v=OCS.15)
ms:contentKeyID: 48185757
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify the global hosted voice mail policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

The *global* hosted voice mail policy is installed with Lync Server 2013. You can modify it to meet your needs, but you cannot rename or delete it. To modify the global policy, you use the Set-CsHostedVoicemailPolicy cmdlet to set the parameters to appropriate values for your specific deployment.

For details about the [Set-CsHostedVoicemailPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsHostedVoicemailPolicy) cmdlet, see the Lync Server Management Shell documentation.

<div>

## To modify the global hosted voice mail policy

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsHostedVoicemailPolicy cmdlet to set the global policy parameters for your environment. For example, run:
    
        Set-CsHostedVoicemailPolicy -Destination ExUM.fabrikam.com -Organization "corp1.litwareinc.com"
    
    Because this command does not specify the policy’s Identity parameter, Windows PowerShell command-line interface sets the following values on the global hosted voice mail policy:
    
      - **Destination** specifies the fully qualified domain name (FQDN) of the hosted Exchange UM service. This parameter is optional, but if you attempt to enable a user for hosted voice mail and the user’s assigned policy does not have a Destination value, the enable will fail.
    
      - **Organization** specifies a comma-separated list of the Exchange tenants that home Lync Server users. Each tenant must be specified as the FQDN of that tenant on the hosted Exchange UM service.
    
    <div>
    

    > [!NOTE]  
    > In the previous example cmdlet, the value “corp1.litwareinc.com” replaces any value that might already be present in the Organization parameter. For example, if the policy already contains a comma-separated list of organizations, the full list would be replaced. If you want to add an organization to the list rather than replace the entire list, run a command similar to the following.

    
    </div>
    
        $a = Get-CsHostedVoicemailPolicy
        $a.Organization += ",corp3.litwareinc.com"
        Set-CsHostedVoicemailPolicy -Organization $a.Organization

</div>

</div>

<span> </span>

</div>

</div>

</div>

