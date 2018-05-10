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
description: "Instructions for implementing cloud-based voicemail for users homed Skype for Business Server."
---

# Configure Cloud Voicemail Service

<!-- PM Roy Kunz  -->

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 

This feature allows Skype for Business Server to use the same Cloud Voicemail Service (located in Azure) as Skype for Business Online users, as described in [Check Skype for Business voicemail and options](https://support.office.com/en-us/article/Check-Skype-for-Business-voicemail-and-options-2deea7f8-831f-4e85-a0d4-b34da55945a8?ui=en-US&rs=en-US&ad=US). Unanswered calls will be sent by the Server to the Service (i.e. from on-prem to online). The Service will process the voicemail, including transcription. The Service will then deposit the voicemail in the Exchange mailbox of the users, regardless of whether they are homed on-prem or online (as is done for Cloud PBX users). Users will have access to their voicemail both from the Skype for Business client and from their Exchange mailbox (as is currently the case). On-prem users will be able to use the web based portal to manage the same user facing parameters available for online users. An admin will have controls over the same range of controls available for online users. See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for example. 

**QUESTION:<BR> WHAT IS THE OFFICIAL NAME FOR THE AZURE VM SERVICE?**


### Shared SIP Address Space
<!--https://technet.microsoft.com/en-us/library/gg398067(v=ocs.15).aspx#Shared SIP Address Space -->

**QUESTION:<BR> PLEASE AFFIRM: ARE WE USING A SHARED SIP ADDRESS SPACE?**

To integrate Skype for Business Server 2019 with Azure Cloud voicemail, you must configure _a shared SIP address space_. In this configuration, the same SIP domain address space is available to both Skype for Business Server 2019 and the Azure Cloud voicemail service provider.

>[NOTE]
> Use of the shared SIP address space is similar to the approach used in a cross-premises Skype for Business Server 2019 environment, in which some users are homed in the Skype for Business Server deployment and some are homed in a hosted deployment (such as Skype for Business Online). The SIP domain is split between them. When you integrate Skype for Business Server 2019 with Azure Cloud voicemail, ensure that you include Azure Cloud voicemail in the shared SIP address space. 

1. Configure the Edge Server for federation by running the Set-CsAccessEdgeConfiguration cmdlet to set the following parameters:
    - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests.
    - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario.
    - **EnablePartnerDiscovery** specifies whether Skype for Business Server 2019 will use DNS records to try to discover partner domains that are not listed in the Active Directory allowed domains list. If False, Skype for Business Server 2019 will federate only with domains that are found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners.
2. Replicate the Central Management store to the Edge Server and verify the replication. For details, see the following section.
3. Configure a _hosting provider_ on the Edge Server by running the **New-CsHostingProvider** cmdlet to set the following parameters:
- **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, **Azure Cloud voicemail**.
- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Must be set to **True**.
- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. Must be set to **True**.
- **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server 2019 accounts. Must be set to **False**.
- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, **proxyserver<span></span>.fabrikam.com**. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.

**QUESTION:<BR> NEED THE PROXY FQDN FOR AZURE CLOUD VM**
 
- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server 2019 topology. Must be set to **False**.

### Export your Skype for Business Server 2019 topology and copy it to external media for edge installation
<!--https://technet.microsoft.com/en-us/library/gg398983(v=ocs.15).aspx -->

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


### Enable Users for Azure Cloud Voice Mail

To enable a user’s voice mail calls to be routed to Azure Cloud voicemail, you must run the Set-CsUser cmdlet to set the value of the HostedVoiceMail parameter. This parameter also signals Skype for Business Server 2019 to light up the “call voice mail” indicator.

- The following example enables Pilar Ackerman’s user account for hosted voice mail:`Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True`

    The cmdlet verifies that a hosted voice mail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.
- The following example disables Pilar Ackerman’s user account for hosted voice mail: `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False`

    The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

For details about using the Set-CsUser cmdlet, see the Skype for Business Server Management Shell documentation.

**QUESTION:<BR> ASK KEN WITHEE WHERE THESE DOCS ARE NOW**