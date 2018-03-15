---
title: "Hosted voice mail policies in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d62a35ed-cbe2-4f06-86b4-e192c18435c1
description: "In this articleHosted Voice Mail Policy ScopeHosted Voice Mail Policy AttributesPer-User Voice Mail Policy Assignment"
---

# Hosted voice mail policies in Lync Server 2013
[]
 **In this article**
  
[Hosted Voice Mail Policy Scope](#sectionSection0)
  
[Hosted Voice Mail Policy Attributes](#sectionSection1)
  
[Per-User Voice Mail Policy Assignment](#sectionSection2)
  
A hosted voice mail policy provides information to the Lync Server 2013 ExUM Routing application about where to route calls for users whose mailboxes are located on a hosted Exchange service. 
  
> [!NOTE]
> Hosted voice mail policies are required only for Lync Server 2013 integration with hosted Exchange UM. They are not needed for integration with on-premises Exchange UM. 
  
## Hosted Voice Mail Policy Scope
<a name="sectionSection0"> </a>

Hosted voice mail policy scope determines the hierarchical level at which the policy applies. You can configure hosted voice mail policies with the following scope levels:
  
- The global policy can potentially affect all users in the Lync Server 2013 deployment. If a user is enabled for hosted Exchange UM access and has not been assigned a per-user policy, and if a site policy has not been assigned to the user's site, the global policy applies. The global policy is installed with Lync Server 2013. You can modify it to meet your needs, but you cannot rename or delete it. 
    
- A site policy can affect all users that are homed on the site for which the policy is defined. If a user is configured for hosted Exchange UM access and has not been assigned a per-user policy, the site policy applies. 
    
- A per-user policy can affect only individual users or groups. To enforce a per-user policy, you must explicitly assign the policy to individual users, groups, and contact objects. 
    
> [!NOTE]
> In most cases, only one hosted voice mail policy is required. You can often modify the global policy to meet all your needs. If you deploy multiple hosted voice mail policies, all such policies have per-user scope. 
  
## Hosted Voice Mail Policy Attributes
<a name="sectionSection1"> </a>

A voice mail policy defines two attributes that the Lync Server 2013 ExUM Routing application inserts in the request URI of an INVITE message that is sent to the hosted Exchange UM implementation:
  
- **Destination**: The fully qualified domain name (FQDN) of the hosted Exchange UM service. This value is used by the on-premises Lync Server Edge Server for routing purposes.
    
    > [!NOTE]
    > The FQDN for Exchange Online is exap.um.outlook.com. 
  
- **Organization**: The FQDN of the tenant on the hosted Exchange UM service that homes your Lync Server 2013 users' mailboxes. A voice mail policy can contain multiple organizations. If more than one organization is included in the policy, this attribute must be a comma-separated list of the Exchange Server tenants that home your Lync Server 2013 user mailboxes.
    
> [!NOTE]
> The tenant administrator of your hosted Exchange UM service will provide the necessary values for your Destination and Organization attribute settings. To configure your policy, you must run the New-CsHostedVoicemailPolicy cmdlet or use the Set-CsHostedVoicemailPolicy cmdlet to modify one that exists (for example, the global policy). 
  
For details about managing hosted voice mail policies, see the Lync Server Management Shell documentation for the following cmdlets:
  
- New-CsHostedVoicemailPolicy
    
- Set-CsHostedVoicemailPolicy
    
- Get-CsHostedVoicemailPolicy
    
## Per-User Voice Mail Policy Assignment
<a name="sectionSection2"> </a>

If your hosted voice mail policy is defined with per-user scope, you must explicitly assign it. You can run the Grant-CsHostedVoicemailPolicy cmdlet to assign the policy to individual users or groups.
  
For details about assigning or removing a per-user hosted voice mail policy, see the Lync Server Management Shell documentation for the following cmdlets:
  
- Grant-CsHostedVoicemailPolicy
    
- Remove-CsHostedVoicemailPolicy
    

