---
title: "Configure Cloud Voicemail service"
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

# Configure Cloud Voicemail service
<!-- PM Roy Kuntz  See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 
This article describes how to configure Microsoft Cloud Voicemail service for your Skype for Business on-premises users.  

This article assumes that you already have Skype for Business Server deployed in a supported topology, and that you have met the prerequisites for setting up hybrid connectivity.

For more information about the benefits, planning considerations, and requirements for implementing Cloud Voicemail, see [Plan Cloud Voicemail service](plan-cloud-voicemail.md).

 <!--See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->


Configuring Cloud Voicemail involves the following tasks:

1.  Ensure you have met the prerequisites as described in [Plan Cloud Voicemail service](plan-cloud-voicemail.md).

2.  Ensure you have set up hybrid connectivity as described in [Plan hybrid connectivity](plan-hybrid-connectivity.md) and [Configure hybrid connectivity](configure-hybrid-connectivity.md).

3.  [Configure Cloud Voicemail as the hosting provider on the Edge Server](#configure-cloud-voicemail-as-the-hosting-provider-on-the-edge-server).

4.  [Enable a User for Cloud Voicemail](#enable-a-user-for-cloud-voicemail).

5. [Configure Cloud Voicemail routing]




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
**Questions:**
- **Replace -Identity "Exchange Online" with what?** seems likely there's a new option needed for Exch on prem
- **Replace -ProxyFqdn "exap<span></span>.um.outlook.com" with what?** Seems likely this will be different if Exch is online vs onprem.
- **What changes are there to the command when integrating with Exch on prem?**
- **Is this the only command in integrating with exchange OL, or is this specific to UM?** the integration for Exch OL that doesn't involve Exch UM is not clearly documented

## Enable a user for Cloud Voicemail

To enable a user’s voice mail calls to be routed to Cloud Voicemail, you use the **[Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/set-csuser?view=skype-ps)** cmdlet with the HostedVoiceMail parameter. 

For example, the following command enables a user account for Cloud Voicemail: 

```Set-CsUser -Identity "User1" -HostedVoiceMail $True```

The cmdlet verifies that a Cloud Voicemail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.

The next example disables a user account for hosted voice mail:

```Set-CsUser -Identity "User1" -HostedVoiceMail $False```

The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

##Configure Cloud Voicemail routing

The [Exchange UM] Routing application runs on the Front End Server to route calls to the Cloud Voicemail service.

The Routing application uses information from user account settings and from hosted voice mail policy parameters to determine how to route calls for hosted voice messaging, as shown in the following diagram.

**INSERT DIAGRAM HERE**

Cloud Voicemail routing can be configured to route calls to users who are enabled for on-premises Exchange UM, to users who are enabled for Cloud Voicemail, or to a combination of the two.

For example, suppose that Roy’s mailbox and Exchange UM service are homed in an on-premises Exchange deployment.

The proxy address information from Roy’s user account provides the information that the Routing application uses to route his calls to an on-premises Exchange UM server.

Now assume that Alice’s mailbox and Exchange UM service are located at a hosted Exchange service provider’s data center. Routing for her Exchange UM calls is configured as follows:

- The values set in the msExchUCVoiceMailSettings attribute of Alice’s user account tell the  Routing application to check for routing details in a hosted voice mail policy.

- The hosted voice mail policy that is assigned to Alice’s user account provides routing details: 

   - Destination is the hosted Exchange UM service provider (ls.ExUm.<hostedExchangeServer>.com in this example).

   - Organizations are identified by the tenant IDs, which are the routing FQDNs for SIP messages for Exchange Server tenants that are located on ls.ExUm.<hostedExchangeServer>.com (corp.contoso.com and corp.contoso2.com in this example).

   For more information, see Hosted voiemail policies in 

Note:  The value of the msExchUCVoiceMailSettings attribute can be set by either the Exchange service provider or the Skypoe for Business Server administrator. In the example shown in the preceding diagram, the value (CsHostedVoiceMail=1) was set by the Skype for Business Server administrator to enable hosted voice mail for Alice. For details about this attribute, see Hosted Exchange user management in Skype for Business Server.

Note:  If both the msExchUCVoiceMailSettings attribute and the UM proxy address settings are present in a user account, the msExchUCVoiceMailSettings attribute takes precedence. 


