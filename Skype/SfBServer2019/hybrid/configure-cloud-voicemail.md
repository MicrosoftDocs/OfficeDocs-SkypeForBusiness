---
title: "Configure Cloud Voicemail service"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 5/9/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing cloud-based voicemail for users homed on Skype for Business Server."
---

# Configure Cloud Voicemail service


[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 
This article describes how to configure Microsoft Cloud Voicemail service for your Skype for Business on-premises users.  

This article assumes that you already have Skype for Business Server deployed in a supported topology, and that you have met the prerequisites for setting up hybrid connectivity.

For more information about the benefits, planning considerations, and requirements for implementing Cloud Voicemail, see [Plan Cloud Voicemail service](plan-cloud-voicemail.md).




Configuring Cloud Voicemail involves the following tasks:

1.  Ensure you have met the prerequisites as described in [Plan Cloud Voicemail service](plan-cloud-voicemail.md).

2.  Ensure you have set up hybrid connectivity as described in [Plan hybrid connectivity](plan-hybrid-connectivity.md) and [Configure hybrid connectivity](configure-hybrid-connectivity.md).

3.  [Configure Cloud Voicemail as the hosting provider on the Edge Server](#configure-cloud-voicemail-as-the-hosting-provider-on-the-edge-server) as described in this article.

4. Configure a hosted voicemail policy [Configure Cloud Voicemail routing](#configure-cloud-voicemail-routing) as described in this article.

5.  [Enable a User for Cloud Voicemail](#enable-a-user-for-cloud-voicemail) as described in this article.




## Configure Cloud Voicemail as the hosting provider on the Edge Server 

You configure Cloud Voicemail as the hosting provider on the Edge Server by using the New-CsHostingProvider cmdlet with the following parameters:

- **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, Cloud Voicemail. 

- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. This parameter must be set to True.

- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. This parameter must be set to True.

- **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server accounts. This parameter must be set to False.

- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, proxyserver.contoso.com. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.

- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server topology. This parameter must be set to False.

For example, in the Skype for Business Management shell, the following cmdlet ...


```
New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification
```



##Configure a hosted voicemail policy

The Cloud Voicemail routing application runs on the Front End Server to route calls to the Cloud Voicemail service.

The routing application uses information from user account settings and from hosted voice mail policy parameters to determine how to route calls for hosted voice messaging, as shown in the following diagram.

NATHAN WILL REWRITE THIS SECTION...  

**INSERT DIAGRAM HERE**

Cloud Voicemail routing can be configured to route calls to users who are enabled for on-premises Exchange UM, to users who are enabled for Cloud Voicemail, or to a combination of the two.

For example, assume that Roy’s mailbox and Exchange UM service are homed in an on-premises Exchange deployment.

The proxy address information from Roy’s user account provides the information that the routing application uses to route his calls to an on-premises Exchange UM server.

For another example, assume that Alice’s mailbox and Exchange UM service are located at a hosted Exchange service provider’s data center. Routing for her Exchange UM calls is configured as follows:

**HOW DOES THE FOLLOWING CHANGE FOR CLOUD VOICEMAIL?**

- The values set in the msExchUCVoiceMailSettings attribute of Alice’s user account tell the routing application to check for routing details in a hosted voice mail policy.

- The hosted voice mail policy that is assigned to Alice’s user account provides routing details: 

   - Destination is the hosted Exchange UM service provider (ls.ExUm.<hostedExchangeServer>.com in this example).

   - Organizations are identified by the tenant IDs, which are the routing FQDNs for SIP messages for Exchange Server tenants that are located on ls.ExUm.<hostedExchangeServer>.com (corp.contoso.com and corp.contoso2.com in this example).

   For more information, see Hosted voiemail policies in **INSERT LINK HERE**.

Note:  The value of the msExchUCVoiceMailSettings attribute can be set by either the Exchange service provider or the Skype for Business Server administrator. In the example shown in the preceding diagram, the value (CsHostedVoiceMail=1) was set by the Skype for Business Server administrator to enable hosted voice mail for Alice. For details about this attribute, see Hosted Exchange user management in Skype for Business Server.

Note:  If both the msExchUCVoiceMailSettings attribute and the UM proxy address settings are present in a user account, the msExchUCVoiceMailSettings attribute takes precedence. 

## Enable a user for Cloud Voicemail

NATHAN WILL FIX SYNTAX....

To enable a user’s voice mail calls to be routed to Cloud Voicemail, you use the **[Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/set-csuser?view=skype-ps)** cmdlet with the HostedVoiceMail parameter. 

For example, the following command enables a user account for Cloud Voicemail: 

```Set-CsUser -Identity "User1" -HostedVoiceMail $True```

The cmdlet verifies that a Cloud Voicemail policy--at the global, site, or user level--applies to this user. If no policy applies, the cmdlet fails.  

The next example disables a user account for hosted voice mail:

```Set-CsUser -Identity "User1" -HostedVoiceMail $False```

The cmdlet verifies that no hosted voice mail policy--at the global, site, or user level--applies to this user. If a policy does apply, the cmdlet fails.


Note:  uSER MUST be enterprise voice enabled.