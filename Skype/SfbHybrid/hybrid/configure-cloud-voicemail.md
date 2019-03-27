---
title: "Configure Cloud Voicemail service"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 2/11/2019
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing cloud-based voicemail for users homed on Skype for Business Server."
---

# Configure Cloud Voicemail service

## Overview 
This article describes how to configure Microsoft Cloud Voicemail service for your Skype for Business on-premises users.  

This article assumes that you already have Skype for Business Server deployed in a supported topology, and that you have met the prerequisites for setting up hybrid connectivity.

For more information about the benefits, planning considerations, and requirements for implementing Cloud Voicemail, see [Plan Cloud Voicemail service](plan-cloud-voicemail.md).




Configuring Cloud Voicemail involves the following tasks:

1.  Ensure that you have met the prerequisites as described in [Plan Cloud Voicemail service](plan-cloud-voicemail.md).

2.  Ensure that you have set up hybrid connectivity as described in [Plan hybrid connectivity](plan-hybrid-connectivity.md) and [Configure hybrid connectivity](configure-hybrid-connectivity.md). 

3.  [Configure Cloud Voicemail as the hosting provider on the Edge Server](#configure-cloud-voicemail-as-the-hosting-provider-on-the-edge-server) as described in this article.

4.  [Configure a hosted voicemail policy](#configure-a-hosted-voicemail-policy) as described in this article.

5.  [Assign a hosted voicemail policy](#assign-a-hosted-voicemail-policy) as described in this article.

6.  [Enable a user for Cloud Voicemail](#enable-a-user-for-cloud-voicemail) as described in this article.


## Configure Cloud Voicemail as the hosting provider on the Edge Server 

You configure Cloud Voicemail as the hosting provider on a Front End Server by using the New-CsHostingProvider cmdlet with the following parameters:

- **Identity** specifies a unique string value identifier for the hosting provider that you are creating; for example, Cloud Voicemail. 

- **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. This parameter must be set to True.

- **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. This parameter must be set to True.

- **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server accounts. This parameter must be set to False.

- **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider; for example, proxyserver.contoso.com. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then re-create the entry for that provider.

- **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server topology. This parameter must be set to False.

For example, in the Skype for Business Management shell, the following cmdlet configures Cloud Voicemail as the hosting provider:


```
New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification
```

## Configure a hosted voicemail policy

To ensure that voicemail for your organization is routed to the Cloud Voicemail service, you must configure a hosted voicemail policy for your organization. In many cases, only one hosted voicemail policy is required, and you can modify the global policy to meet all your needs. If your organization requires multiple hosted voicemail policies, you can add policies by using the new-cshostedvoicemailpolicy cmdlet.

To modify the global policy, run the following command in the Skype for Business Server management shell after updating your Organization and TenantID:

```
Set-CsHostedVoicemailPolicy -Identity Global -Description "Global Cloud Voicemail Policy" -Destination exap.um.outlook.com -Organization YourDefaultDomain.onmicrosoft.com -TenantID “11111111-1111-1111-1111-111111111111”
```

- **Destination** specifies the fully qualified domain name (FQDN) of the hosted Cloud Voicemail service. This value should be set to **exap.um.outlook.com**.

- **Organization** is the default domain assigned to your tenant. You can retrieve this information by having the tenant admin log in to office.com, click on the Admin Center app, navigate to **Setup** on the left, and click **Domains**. For example: mytenant.onmicrosoft.com.

    The Organization name is also the Default Domain name in Office 365.

- **TenantID** is used to identify your tenant in Office 365. For more information, see [Find your Office 365 tenant ID](https://support.office.com/en-us/article/find-your-office-365-tenant-id-6891b561-a52d-4ade-9f39-b492285e2c9b).

To ensure that a hosted voicemail policy was created successfully, run the following command:

```
Get-CsHostedVoicemailPolicy
```

## Assign a hosted voicemail policy

By default, the Global hosted voicemail policy is assigned to all users. If you use a different policy, before enabling users for hosted voicemail, you must first grant users the desired hosted voicemail policy by using the [Grant-CSHostedVoicemailPolicy](https://docs.microsoft.com/powershell/module/skype/grant-cshostedvoicemailpolicy?view=skype-ps) cmdlet.

For example, the following command assigns a non-Global hosted voicemail policy to a user:


```
Get-CsUser -Identity "User1" | Grant-CsHostedVoicemailPolicy -Identity "Tag:CloudVoiceMailUsers" 
```

## Enable a user for Cloud Voicemail

To enable a user’s voicemail calls to be routed to Cloud Voicemail, you use the [Set-CsUser](https://docs.microsoft.com/powershell/module/skype/set-csuser?view=skype-ps) cmdlet with the HostedVoiceMail parameter. 

For example, the following command enables a user account for Cloud Voicemail: 

```Set-CsUser -Identity "User1" -HostedVoiceMail $True```

The cmdlet verifies that a Cloud Voicemail policy--at the global, site, or user level--applies to this user. If no policy applies, the cmdlet fails.  

The next example disables a user account for Cloud Voicemail:

```Set-CsUser -Identity "User1" -HostedVoiceMail $False```

The cmdlet verifies that no hosted voicemail policy--at the global, site, or user level--applies to this user. If a policy does apply, the cmdlet fails.

> [!NOTE]
>  Users must be enterprise-voice enabled to use the Microsoft Cloud Voicemail Service.
