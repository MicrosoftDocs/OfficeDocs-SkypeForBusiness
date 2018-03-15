---
title: "Create a site-level hosted voice mail policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 145892c8-a6ca-45fb-9e83-786f709dd775
description: "A site policy can impact all users that are homed on the site for which the policy is defined. If a user is configured for hosted Exchange UM access and has not been assigned a Per-user policy, the site policy applies. If you have not deployed a site policy, the global policy applies."
---

# Create a site-level hosted voice mail policy in Lync Server 2013
[]
A site policy can impact all users that are homed on the site for which the policy is defined. If a user is configured for hosted Exchange UM access and has not been assigned a Per-user policy, the site policy applies. If you have not deployed a site policy, the global policy applies. 
  
For details about configuring site policies, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
    
- [Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)
    
- [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
    
### To create a site hosted voice mail policy

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the New-CsHostedVoicemailPolicy cmdlet to create the policy. For example, run:
    
  ```
  New-CsHostedVoicemailPolicy -Identity site:Redmond -Destination ExUM.fabrikam.com -Description "Hosted voice mail policy for the Redmond site." -Organization "corp1.litwareinc.com, corp2.litwareinc.com"
  ```

    This example creates a hosted voice mail policy with site scope, and sets the following parameters:
    
  - **Identity** specifies a unique identifier for the policy, which includes the scope. For a policy with site scope, the Identity parameter value must be specified in the format  `site:` *\<name\>*  , for example,  `site:Redmond`.
    
  - **Destination** specifies the fully qualified domain name (FQDN) of the hosted Exchange UM service. This parameter is optional, but if you attempt to enable a user for hosted voice mail and the user's assigned policy does not have a Destination value, the enable will fail. 
    
  - **Description** provides optional descriptive information about the policy. 
    
  - **Organization** specifies a comma-separated list of the Exchange tenants that home Lync Server 2013 users. Each tenant must be specified as the FQDN of that tenant on the hosted Exchange UM service. 
    

