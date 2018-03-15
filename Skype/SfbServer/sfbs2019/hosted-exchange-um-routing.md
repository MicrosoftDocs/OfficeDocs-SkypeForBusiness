---
title: "Hosted Exchange UM routing in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6c90dc8b-6aef-4ce8-b483-37c7b5a553c2
description: "The Exchange UM Routing application runs on the Front End Server to route calls, either to an on-premises Microsoft Exchange Server Unified Messaging (UM) deployment or to hosted Exchange UM service."
---

# Hosted Exchange UM routing in Lync Server 2013
[]
The Exchange UM Routing application runs on the Front End Server to route calls, either to an on-premises Microsoft Exchange Server Unified Messaging (UM) deployment or to hosted Exchange UM service.
  
## The ExUM Routing Application

The Lync Server 2013 Exchange UM Routing application uses information from user account settings and from hosted voice mail policy parameters to determine how to route calls for hosted voice messaging, as shown in the following diagram.
  
**Example of mixed deployment Exchange UM routing**

![On-premises Lync Server Exchange UM deployment](media/HEXUMRouting.jpg)
  
Exchange UM routing can be configured to route calls to users who are enabled for on-premises Exchange UM, to users who are enabled for hosted Exchange UM, or to a combination of the two.
  
For example, suppose that Roy's mailbox and Exchange UM service are homed in an on-premises Exchange deployment.
  
- The proxy address information from Roy's user account provides the information that the ExUM Routing application uses to route his calls to an on-premises Exchange UM server.
    
Alice's mailbox and Exchange UM service are located at a hosted Exchange service provider's data center. Routing for her Exchange UM calls is configured as follows:
  
- The values set in the msExchUCVoiceMailSettings attribute of Alice's user account tell the ExUM Routing application to check for routing details in a hosted voice mail policy.
    
    > [!NOTE]
    > The value of the msExchUCVoiceMailSettings attribute can be set by either the Exchange service provider or the Lync Server 2013 administrator. In the example shown in the preceding diagram, the value (CsHostedVoiceMail=1) was set by the Lync Server 2013 administrator to enable hosted voice mail for Alice. For details about this attribute, see [Hosted Exchange user management in Lync Server 2013](hosted-exchange-user-management.md). 
  
- The hosted voice mail policy that is assigned to Alice's user account provides routing details: 
    
  - Destination is the hosted Exchange UM service provider (ls.ExUm. _\<hostedExchangeServer\>_.com in this example).
    
  - Organizations are identified by the tenant IDs, which are the routing FQDNs for SIP messages for Exchange Server tenants that are located on ls.ExUm. _\<hostedExchangeServer\>_.com (corp.contoso.com and corp.litwareinc.com in this example).
    
    > [!NOTE]
    > The FQDN for Exchange Online is exap.um.outlook.com. 
  
    For details, see [Hosted voice mail policies in Lync Server 2013](hosted-voice-mail-policies.md).
    
> [!NOTE]
> If both the msExchUCVoiceMailSettings attribute and the UM proxy address settings are present in a user account, the msExchUCVoiceMailSettings attribute takes precedence. 
  

