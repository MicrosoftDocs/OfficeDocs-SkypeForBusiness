---
title: 'Manage SIP federated providers for your organization'
ms.reviewer: 
ms:assetid: c78d7e9b-c496-40c6-9249-06ced9cb87f3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552455(v=OCS.15)
ms:contentKeyID: 48679566
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to configure support for users of SIP federated providers."
---

# Manage SIP federated providers for your organization in Skype for Business Server

To configure support for users of SIP federated providers, you need to do the following:

  - Configure one or more external user access policies to support communicating with SIP federated provider contacts

  - Specify which hosted providers you want to support

  - Specify which public IM providers you want to support

## Create or edit public SIP federated providers in Skype for Business Server

Public instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by public providers.

Skype for Business Server has public provider configurations for instant messaging. Each public provider is configured with the provider’s Edge server fully qualified domain name, and the default verification level **Allow users to communicate only with people on their Contacts list who use this provider**.

As a default setting, none of the public providers are enabled. You should complete license agreement and provisioning work before enabling the public providers. You can enable the provider before completing the licensing and provisioning work. Users will not be able to communicate with contacts on those providers until the pre-requisite work is completed. For details on licensing and provisioning of public providers, see [Configure policies to control public user acces](../external-access-policies/configure-policies-to-control-public-user-access.md).

Use the following procedure to create or edit Public providers.


### To create or edit public providers

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Federation and External Access**, and then click **SIP Federated Providers**.

4.  If you need to create a new Public provider, click **New** and then click **Public provider**.

5.  If you need to edit an entry from the list of Public providers, select a public provider, click **Edit**, then click **Show details**.

6.  On the **Edit SIP Federated Provider** page, you can type or edit the following settings:
    
      - **Enable communications with this provider**   Selecting this setting enables IM with this provider’s users.
    
      - **Provider name:**   A required property, type the name of the provider as it will be reflected in the listing of SIP Federated Providers.
    
      - **Access Edge service (FQDN):**   A required property, type the fully qualified domain name of the Access Edge service of the provider that you are configuring. This information is provided as a default item, and should only be changed if the public provider makes a change to the FQDN of the Access Edge service at the public provider.
    
      - **Default verification level:**   The default setting, **Allow users to communicate with people on their Contacts list who use this provider** will limit communication to contacts that you have accepted and are in your contact list.
        
        Selecting **Allow users to communicate with everyone using this provider** removes the restriction that you must have received and accepted a contact invite. This setting does not limit who can contact you from the public provider’s network.

7.  When you are done configuring the settings, click **Commit** to save, or click **Cancel** to discard your changes.

## Create or edit hosted SIP federated providers in Skype for Business Server

Hosted provider instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by hosted providers.

Each hosted provider is configured with the provider’s Edge server fully qualified domain name, and the default verification level **Allow users to communicate only with people on their Contacts list who use this provider**.

Use the following procedure to create or edit hosted providers.

### To create or edit hosted providers

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Federation and External Access**, and then click **SIP Federated Providers**.

4.  If you need to create a new Hosted provider, click **New** and then click **Hosted provider**.

5.  If you need to edit an entry from the list of Hosted providers, select a hosted provider, click **Edit**, then click **Show details**.

6.  On the **Edit SIP Federated Provider** page, you can type or edit the following settings:
    
      - **Enable communications with this provider**   Selecting this setting enables communications with this provider’s users.
    
      - **Provider name:**   A required property, type the name of the provider as it will be reflected in the listing of SIP Federated Providers.
    
      - **Access Edge service (FQDN):**   A required property, type the fully qualified domain name of the Access Edge service of the hosted provider that you are configuring. This information should be provided by the hosted provider, and should only be changed if the hosted provider makes a change to the FQDN of the Access Edge service at the hosted provider.
    
      - **Default verification level:**   The default setting, **Allow users to communicate with people on their Contacts list who use this provider** will limit communication to contacts that you have accepted and are in your contact list.
        
        Selecting **Allow users to communicate with everyone using this provider** removes the restriction that you must have received and accepted a contact invite. This setting does not limit who can contact you from the hosted provider’s network.

7.  When you are done configuring the settings, click **Commit** to save, or click **Cancel** to discard your changes.


## See Also


[Configure policies to control public user acces](../external-access-policies/configure-policies-to-control-public-user-access.md)

[Enable or disable federation and public IM connectivity](../access-edge/enable-or-disable-federation-and-public-im-connectivity.md)

