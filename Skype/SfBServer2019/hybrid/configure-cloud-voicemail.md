---
title: "Configure Cloud Voicemail"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/9/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing cloud-based voicemail for users homed on Skype for Business Server."
---

# Configure Cloud Voicemail Service
<!-- PM Roy Kunz  See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 
See the [Plan Cloud Voicemail Service](plan-cloud-voicemail.md) article for an overview of Cloud Voicemail functionality.
 <!--See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->

## Shared SIP Address Space
<!--https://technet.microsoft.com/en-us/library/gg398067(v=ocs.15).aspx#Shared SIP Address Space -->

**QUESTION:<BR> PLEASE AFFIRM: ARE WE USING A SHARED SIP ADDRESS SPACE? <BR> Is this already configured as part of hybrid config?**

To integrate Skype for Business Server 2019 with  Cloud voicemail, you must configure _a shared SIP address space_. In this configuration, the same SIP domain address space is available to both Skype for Business Server 2019 and the  Cloud voicemail service provider.

>[!NOTE]
> Use of the shared SIP address space is similar to the approach used in a cross-premises Skype for Business Server 2019 environment, in which some users are homed in the Skype for Business Server deployment and some are homed in a hosted deployment (such as Skype for Business Online). The SIP domain is split between them. When you integrate Skype for Business Server 2019 with  Cloud voicemail, ensure that you include  Cloud voicemail in the shared SIP address space. 

1. Configure the Edge Server for federation by running the **[Set-CsAccessEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csaccessedgeconfiguration?view=skype-ps)** cmdlet to set the following parameters:
    - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests.
    - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario.
    - **EnablePartnerDiscovery** specifies whether Skype for Business Server 2019 will use DNS records to try to discover partner domains that are not listed in the Active Directory allowed domains list. If False, Skype for Business Server 2019 will federate only with domains that are found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners.
2. Replicate the Central Management store to the Edge Server and verify the replication. For details, follow the steps in https://technet.microsoft.com/en-us/library/gg398983(v=ocs.15).aspx 
3. Configure a _hosting provider_ on the Edge Server by running the **[New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/new-cshostingprovider?view=skype-ps)** cmdlet to set the following parameters:
    - **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, **Cloud voicemail**.
    - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Must be set to **True**.
    - **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. Must be set to **True**.
    - **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server 2019 accounts. Must be set to **False**.
    - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, **proxyserver<span></span>.fabrikam.com**. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.
     - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server 2019 topology. Must be set to **False**.

**QUESTION:<BR> NEED THE PROXY FQDN FOR  CLOUD VM**

## Enable Users for Cloud Voicemail

To enable a user’s voice mail calls to be routed to  Cloud voicemail, you must run the **[Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/set-csuser?view=skype-ps)** cmdlet to set the value of the HostedVoiceMail parameter. This parameter also signals Skype for Business Server 2019 to light up the “call voice mail” indicator.

- The following example enables Pilar Ackerman’s user account for Cloud Voicemail: \
     `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True`

    The cmdlet verifies that a Cloud Voicemail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.
- The following example disables Pilar Ackerman’s user account for hosted voice mail:  \
    `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False`

**QUESTION:<BR> Verify: are we still using the HostedVoiceMail parameter, or is there a new parameter not yet public?<br> If the user is already on hosted exchange UM is this part needed?<br> What about migrating users from hosted EXCH UM to Cloud VM?**

The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

