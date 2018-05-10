---
title: "Configure cloud Voicemail"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/9/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing cloud-based voicemail for users homed on-premises."
---

# Configure Cloud Voicemail Service

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 

This feature allows Skype for Business Server to use the same Cloud Voicemail Service (located in Azure) as Skype for Business Online users, as described in [Check Skype for Business voicemail and options] (https://support.office.com/en-us/article/Check-Skype-for-Business-voicemail-and-options-2deea7f8-831f-4e85-a0d4-b34da55945a8?ui=en-US&rs=en-US&ad=US). Unanswered calls will be sent by the Server to the Service (i.e. from on-prem to online). The Service will process the voicemail, including transcription. The Service will then deposit the voicemail in the Exchange mailbox of the users, regardless of whether they are homed on-prem or online (as is done for Cloud PBX users). Users will have access to their voicemail both from the Skype for Business client and from their Exchange mailbox (as is currently the case). On-prem users will be able to use the web based portal to manage the same user facing parameters available for online users. An admin will have controls over the same range of controls available for online users. See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for example. 


## Leveraged from 2013

This article provides an overview of the architecture for on-premises and hosted Exchange UM integration, including supported modes, shared SIP space, and routing considerations.


### Hosted Exchange UM integration architecture in Skype for Business Server 2019
was https://technet.microsoft.com/en-us/library/gg398067(v=ocs.15).aspx 

<!-- PM Roy Kunz  -->
The Skype for Business Server 2019 ExUM Routing application supports integration with an on-premises Exchange Unified Messaging (UM) deployment, with Exchange UM hosted by a service provider, or with a combination of the two. The following diagram shows all three possibilities. 

The following modes are supported:

- **On-premises deployment**: Skype for Business Server 2019 and Exchange UM are both deployed on local servers within your enterprise.
- **Cross-premises deployment**: Skype for Business Server 2019 is deployed on local servers within your enterprise and Exchange UM is hosted in an online service provider’s facility, such as a Microsoft Exchange Online data center.
- **Mixed deployment**: Your Skype for Business Server 2019 deployment has some user mailboxes homed on local Exchange servers within your enterprise and some mailboxes homed in a hosted Exchange service data center.
> [NOTE] 
> The mixed deployment can be used as a transitional solution during evaluation and phased migration of users to hosted Exchange UM, or a permanent solution if you opt to keep some users’ Exchange UM services on-premises after transferring others. 

#### Shared SIP Address Space
https://technet.microsoft.com/en-us/library/gg398067(v=ocs.15).aspx#Shared SIP Address Space 

To integrate Skype for Business Server 2019 with an on-premises Exchange UM deployment, you grant Skype for Business Server 2019 permission to read Exchange UM Active Directory Domain Services objects. This approach does not work for integration with hosted Exchange UM, however, because Skype for Business Server 2019 and Exchange UM are installed in separate forests with no trust between them.
To integrate Skype for Business Server 2019 with hosted Exchange UM, you must configure _a shared SIP address space_. In this configuration, the same SIP domain address space is available to both Skype for Business Server 2019 and the hosted Exchange UM service provider.

>[NOTE]
> Use of the shared SIP address space is similar to the approach used in a cross-premises Skype for Business Server 2019 environment, in which some users are homed in the on-premises deployment and some are homed in a hosted deployment (such as Skype for Business Online). The SIP domain is split between them. When you integrate Skype for Business Server 2019 with hosted Exchange UM, ensure that you include the Exchange UM service provider in the shared SIP address space. 

1. Configure the Edge Server for federation by running the Set-CsAccessEdgeConfiguration cmdlet to set the following parameters:
    - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests.
    - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario.
    - **EnablePartnerDiscovery** specifies whether Skype for Business Server 2019 will use DNS records to try to discover partner domains that are not listed in the Active Directory allowed domains list. If False, Skype for Business Server 2019 will federate only with domains that are found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners.
2. Replicate the Central Management store to the Edge Server and verify the replication. For details, see [Export your Skype for Business Server 2019 topology](#export-your-Skype for Business-server-2019-topology-and-copy-it-to-external-media-for-edge-installation) in the Deployment documentation.
3. Configure a _hosting provider_ on the Edge Server by running the **New-CsHostingProvider** cmdlet to set the following parameters:
- **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, **Hosted Exchange UM**.
- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Must be set to **True**.
- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. Must be set to **True**.
- **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server 2019 accounts. Must be set to **False**.
- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, **proxyserver<span></span>.fabrikam.com**. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.
- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server 2019 topology. Must be set to **False**.

##### Export your Skype for Business Server 2019 topology and copy it to external media for edge installation
https://technet.microsoft.com/en-us/library/gg398983(v=ocs.15).aspx 

After you publish your topology, the Skype for Business Server Deployment Wizard needs access to the Central Management store data in order to start the deployment process on the server. In the internal network, the data is available directly from the servers, but Edge Servers that are not in the internal domain cannot access the data. To make the topology configuration data available for an Edge Server deployment, you must export the topology data to a file and copy it to external media (for example, a USB drive or a network share that is available from the Edge Server) before you run the Skype for Business Server Deployment Wizard on the Edge Server. Use the following procedure to make your topology configuration data available on the Edge Server that you are deploying.

>[NOTE]
>After you install Skype for Business Server 2019 on an Edge Server, you manage the Edge Server using the administrative tools in the internal network, which automatically replicate configuration to any Edge Servers in your deployment. The only exception is assigning and installing certificates and stopping and starting services, both of which must be done on the Edge Server. 

To make your topology data available on an Edge Server by using Skype for Business Server Management Shell:

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.

2. In the Skype for Business Server Management Shell, run the following cmdlet:

```
Export-CsConfiguration -FileName <ConfigurationFilePath.zip>
```

3. Copy the exported file to external media (for example, a USB drive or a network share that is available from the Edge Server during deployment).

### Hosted Exchange UM routing in Skype for Business Server 2019

https://technet.microsoft.com/en-us/library/gg398512(v=ocs.15).aspx 

The Exchange UM Routing application runs on the Front End Server to route calls, either to an on-premises Microsoft Exchange Server Unified Messaging (UM) deployment or to hosted Exchange UM service.

#### The ExUM Routing Application

The Skype for Business Server 2019 Exchange UM Routing application uses information from user account settings and from hosted voice mail policy parameters to determine how to route calls for hosted voice messaging.

Exchange UM routing can be configured to route calls to users who are enabled for on-premises Exchange UM, to users who are enabled for hosted Exchange UM, or to a combination of the two.

For example, suppose that Roy’s mailbox and Exchange UM service are homed in an on-premises Exchange deployment.

- The proxy address information from Roy’s user account provides the information that the ExUM Routing application uses to route his calls to an on-premises Exchange UM server.

Alice’s mailbox and Exchange UM service are located at a hosted Exchange service provider’s data center. Routing for her Exchange UM calls is configured as follows:

- The values set in the msExchUCVoiceMailSettings attribute of Alice’s user account tell the ExUM Routing application to check for routing details in a hosted voice mail policy.
>[NOTE]
>The value of the msExchUCVoiceMailSettings attribute can be set by either the Exchange service provider or the Skype for Business Server 2019 administrator. In the example shown in the preceding diagram, the value (CsHostedVoiceMail=1) was set by the Skype for Business Server 2019 administrator to enable hosted voice mail for Alice. For details about this attribute, see Hosted Exchange user management in Skype for Business Server 2019. 

- The hosted voice mail policy that is assigned to Alice’s user account provides routing details: 

    - Destination is the hosted Exchange UM service provider (ls.ExUm.<hostedExchangeServer>.com in this example).
    - Organizations are identified by the tenant IDs, which are the routing FQDNs for SIP messages for Exchange Server tenants that are located on ls.ExUm.<hostedExchangeServer>.com (corp<span></span>.contoso.com and corp<span></span>.litwareinc.com in this example).

    > [NOTE]
    > The FQDN for Exchange Online is exap.um<span></span>.outlook.com. 

For details, see Hosted voice mail policies in Skype for Business Server 2019.

> [NOTE]
> If both the msExchUCVoiceMailSettings attribute and the UM proxy address settings are present in a user account, the msExchUCVoiceMailSettings attribute takes precedence. 

### Hosted Exchange user management in Skype for Business Server 2019

To provide voice mail services for Skype for Business Server 2019 users whose mailboxes are located on a hosted Exchange service, you must enable their user accounts for hosted voice mail.

> [NOTE]
> Before a Skype for Business Server 2019 user can be enabled for hosted voice mail, a hosted voice mail policy that applies to the corresponding user account must be deployed. The policy can be global, site, or per-user in scope, as long as it applies to the user whom you want to enable. For details, see [Hosted voice mail policies in Skype for Business Server 2019](#hosted-voice-mail-policies-in-Skype for Business-server-2019). 

##### The msExchUCVoiceMailSettings Attribute

Skype for Business Server 2019 introduces a new user attribute named **msExchUCVoiceMailSettings**, which is created as part of the Skype for Business Server 2019 Active Directory schema preparation. This multivalued attribute holds voice mail settings that are shared by Skype for Business Server 2019 and the hosted Exchange service.

The hosted Exchange service may in some cases set the value of the msExchUCVoiceMailSettings attribute in the process of enabling Exchange UM, or during the process of transferring mailboxes to a hosted Exchange Server. If this attribute is not set by Exchange, the Skype for Business Server 2019 administrator must set it by running the Set-CsUser cmdlet, as described earlier in this topic.

The attribute’s key/value pairs and their authors are shown in the following table.

The msExchUCVoiceMailSettings Attribute Key/Value Pairs

|Value   |Author   |Meaning   |
|---------|---------|---------|
|ExchangeHostedVoiceMail=1  |    Exchange     |  User has been enabled for hosted UM access by Exchange Server. The Exchange UM Routing application will check the user’s hosted voice mail policy for routing details.       |
|ExchangeHostedVoiceMail=0     |    Exchange     |  User has been disabled for hosted UM access by Exchange Server.       |
|CsHostedVoiceMail=1     | Skype for Business Server        |  User has been enabled for hosted UM access by Skype for Business Server 2019. The Skype for Business Server 2019 ExUM Routing application will check the user’s hosted voice mail policy for routing details.       |
|CsHostedVoiceMail=0     |    Skype for Business Server     |   User has been disabled for hosted UM access by Skype for Business Server 2019.      |


> [NOTE]
> If the attribute already has values other than one of the Skype for Business Server 2019 key/value pairs (CSHostedVoiceMail=0 or CSHostedVoiceMail=1), a warning will indicate that the attribute may be managed by a different application. For example, a warning is displayed if the key/value pair ExchangeHostedVoiceMail=0 or ExchangeHostedVoiceMail=1 is already present. In that case, you can change the value by editing it the Active Directory, or run the following cmdlet to set the value to null: `Set-CsUser –identity user –HostedVoicemail $null` 

##### Enabling Users for Hosted Voice Mail

To enable a user’s voice mail calls to be routed to hosted Exchange UM, you must run the Set-CsUser cmdlet to set the value of the HostedVoiceMail parameter. This parameter also signals Skype for Business Server 2019 to light up the “call voice mail” indicator.

- The following example enables Pilar Ackerman’s user account for hosted voice mail:`Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True`

    The cmdlet verifies that a hosted voice mail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.
- The following example disables Pilar Ackerman’s user account for hosted voice mail: `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False`

    The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

For details about using the Set-CsUser cmdlet, see the Skype for Business Server Management Shell documentation.

### Hosted voice mail policies in Skype for Business Server 2019

A _hosted voice mail policy_ provides information to the Skype for Business Server 2019 ExUM Routing application about where to route calls for users whose mailboxes are located on a hosted Exchange service.

> [NOTE]
> Hosted voice mail policies are required only for Skype for Business Server 2019 integration with hosted Exchange UM. They are not needed for integration with on-premises Exchange UM. 

####  Hosted Voice Mail Policy Scope

Hosted voice mail policy scope determines the hierarchical level at which the policy applies. You can configure hosted voice mail policies with the following scope levels:
- The _global policy_ can potentially affect all users in the Skype for Business Server 2019 deployment. If a user is enabled for hosted Exchange UM access and has not been assigned a per-user policy, and if a site policy has not been assigned to the user’s site, the global policy applies. The global policy is installed with Skype for Business Server 2019. You can modify it to meet your needs, but you cannot rename or delete it.
- A _site_ policy can affect all users that are homed on the site for which the policy is defined. If a user is configured for hosted Exchange UM access and has not been assigned a per-user policy, the site policy applies.
- A _per-user_ policy can affect only individual users or groups. To enforce a per-user policy, you must explicitly assign the policy to individual users, groups, and contact objects.

> [NOTE]
> In most cases, only one hosted voice mail policy is required. You can often modify the global policy to meet all your needs. If you deploy multiple hosted voice mail policies, all such policies have per-user scope. 

#### Hosted Voice Mail Policy Attributes

A voice mail policy defines two attributes that the Skype for Business Server 2019 ExUM Routing application inserts in the request URI of an INVITE message that is sent to the hosted Exchange UM implementation:

- **Destination**: The fully qualified domain name (FQDN) of the hosted Exchange UM service. This value is used by the on-premises Skype for Business Server Edge Server for routing purposes.
> [NOTE] 
> The FQDN for Exchange Online is exap.um<span></span>.outlook.com. 

- **Organization**: The FQDN of the tenant on the hosted Exchange UM service that homes your Skype for Business Server 2019 users’ mailboxes. A voice mail policy can contain multiple organizations. If more than one organization is included in the policy, this attribute must be a comma-separated list of the Exchange Server tenants that home your Skype for Business Server 2019 user mailboxes.
> [NOTE] 
> The tenant administrator of your hosted Exchange UM service will provide the necessary values for your Destination and Organization attribute settings. To configure your policy, you must run the New-CsHostedVoicemailPolicy cmdlet or use the Set-CsHostedVoicemailPolicy cmdlet to modify one that exists (for example, the global policy). 

For details about managing hosted voice mail policies, see the Skype for Business Server Management Shell documentation for the following cmdlets:

- New-CsHostedVoicemailPolicy
- Set-CsHostedVoicemailPolicy
- Get-CsHostedVoicemailPolicy 

#### Per-User Voice Mail Policy Assignment

If your hosted voice mail policy is defined with per-user scope, you must explicitly assign it. You can run the Grant-CsHostedVoicemailPolicy cmdlet to assign the policy to individual users or groups.

For details about assigning or removing a per-user hosted voice mail policy, see the Skype for Business Server Management Shell documentation for the following cmdlets:
- Grant-CsHostedVoicemailPolicy
- Remove-CsHostedVoicemailPolicy




