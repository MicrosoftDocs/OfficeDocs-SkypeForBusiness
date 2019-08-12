---
title: 'Configuring federation support for a Skype for Business Online customer'
ms.reviewer: 
ms:assetid: e5f7f38d-ede5-4af3-88c2-026e8a78df12
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202193(v=OCS.15)
ms:contentKeyID: 48185669
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "If you deploy Skype for Business in your organization, you can federate with the domains of one or more Skype for Business Online customers. "
---

# Configuring federation support for a Skype for Business Online customer in Skype for Business Server 

You can provide communications services to users in your organization in any of the following ways:

  - Deploying Skype for Business Server in your organization (known as *on-premises services*) and setting up Skype for Business  user accounts in your organization.
  - Setting up a Microsoft Skype for Business Online customer account with a Hosting Provider and setting up user accounts with the Hosting Provider (known as *online services*).

If you deploy Skype for Business in your organization, you can federate with the domains of one or more Skype for Business Online customers. To enable federation between users of your on-premises Skype for Business deployment and users of a Skype for Business Online customer, you must configure support for the domain and users of the Skype for Business Online customer.

> [!NOTE]  
> This documentation describes only the procedures for configuring your organization to support federation with an Skype for Business Online customer. This documentation does not describe the procedures for configuring the Skype for Business Online customer to support federation. 

## Prerequisites for federating with a Skype for Business Online customer

To federate with a Skype for Business Online customer, you should have already completed initial deployment and configuration of Skype for Business Server in your organization. This includes the following:

  - Deploying at least one Standard Edition server or one Enterprise Edition Front End pool in your organization. 
  - Enabling internal user accounts for Skype for Business Server. 
  - Deploying at least one Edge Server and the other components required to support external user access. For details, see [Managing federation and external access to Skype for Business Server](../managing-federation-and-external-access.md).
  - Enabling federation support within your organization and configuring the appropriate method for controlling access by federated domains. For details, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md) and [Manage SIP federated providers for your organization](../sip-providers/manage-sip-federated-providers-for-your-organization.md).
  - Enabling external user access for users in your organization. For details, see [Assign an external user access policy to a Skype for Business enabled user](../external-access-policies/assign-an-external-user-access-policy.md).



## Configure federation support for a Skype for Business Online domain

Federating with a Skype for Business Online customer requires you to complete the following steps:

  - Configure support for the domain of the Skype for Business Online 2010 customer (for example, contoso.onmicrosoft.com). As specified in [Prerequisites for federating with a Skype for Business Online customer](#prerequisites-for-federating-with-a-skype-for-business-online-customer), you should have already enabled federation for your organization. Enabling federation requires specifying the method to be used to control access by federated domains. If you configured your organization to use discovery, adding the domain to your organization’s allowed list is optional. If you did not enable domain discovery, then you must add the domain name of the Skype for Business Online customer to your allowed domains list. You can add a domain name either by using Skype for Business Server Control Panel or by running the **New-CSAllowedDomain** cmdlet. For details about using Skype for Business Server Control Panel, including enabling discovery of domains, see [Manage SIP federated providers for your organization in Skype for Business Server](../sip-providers/manage-sip-federated-providers-for-your-organization.md). For details about using the **New-CSAllowedDomain** cmdlet to add a domain, see [New-CsAllowedDomain](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAllowedDomain).

    > [!NOTE]  
    > A Skype for Business Online customer can have multiple domains. If you want to federate with more than one of the domains, you must configure support for each individual domain with which you want to support federation, and the administrator of the Skype for Business Online customer must enable federation for each of the domains to be federated.

  - Configure support for the hosting provider of the Skype for Business Online customer domain with which you want to federate. Use the procedure in this section to configure support for hosting provider.

    > [!NOTE]  
    > This step is required only for federation with a domain of a Skype for Business Online customer, not for federation with any domain that is deployed on-premises at a federated partner’s location.


### To configure support for a hosting provider

1.  From a Front End Server, Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

2.  Run the **New-CsHostingProvider** cmdlet to create and configure the hosting provider. For example, run:
    
        New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification -Enabled $True -EnabledSharedAddressSpace $False -HostsOCSUsers $False -IsLocal $False
    
    The preceding example sets the following parameters:
    
      - **Identity** specifies a unique string value identifier for the hosting provider that you are creating. Note that the command will fail if an existing provider has already been configured with that Identity.
    
      - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. This value cannot be modified. If the hosting provider changes its proxy server you will need to delete and then recreate the entry for that provider.
    
      - **VerificationLevel** specifies how (or if) messages sent from a hosting provider are verified to ensure that they were sent from that provider.
    
      - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to **True**.
    
      - **EnabledSharedAddressSpace** indicates whether the hosting provider is being used in a shared SIP address space (split domain) scenario.
    
      - **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server accounts. If **False**, the provider hosts other account types, such as Microsoft Exchange accounts.
    
      - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server topology.
    
    For details about using this cmdlet, see [New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider).

## Configure user access for federation with a Skype for Business Online customer 

You must configure the user accounts of all the users in your organization in order for them be allowed to communicate with federated partners. This configuration is applied for all federated partners, including any Microsoft Skype for Business Online customer domains with which you support federation. For details about configuring federation support for user accounts, see [Configure policies to control federated user access](../external-access-policies/configure-policies-to-control-federated-user-access.md) and [Assign an external user access policy to a Skype for Business enabled user](../external-access-policies/assign-an-external-user-access-policy.md).

## Verify communications with a Skype for Business Online customer in Skype for Business Server

To enable Skype for Business users in your organization to communicate with users of a Skype for Business Online customer, you must have completed the following steps:

  - Met all prerequisites. This includes deploying your internal and edge servers, enabling federation support for your organization, and setting up user accounts. For details, see [Prerequisites for federating with a Skype for Business Online customer](#prerequisites-for-federating-with-a-skype-for-business-online-customer).
  - Configured domain access support in your internal deployment. This includes creating a host provider entry and configuring your deployment to allow access from the Skype for Business Online customer’s domain. For details, see [Configure federation support for a Skype for Business Online domain](#configure-federation-support-for-a-skype-for-business-online-domain).
  - Configured your user accounts to support federation. For details, see [Configure user access for federation with a Skype for Business Online customer](#configure-user-access-for-federation-with-a-skype-for-business-online-customer).

After you complete all of these steps and the administrator of the Skype for Business Online customer completes all configuration of their online services to support federation with your organization, verify communications by testing communications between an internal user in your organization and a user of the Skype for Business Online customer. If communication is not successful, use the Logging Tool from your Edge Server to capture log and trace files in order to troubleshoot the problem. 
