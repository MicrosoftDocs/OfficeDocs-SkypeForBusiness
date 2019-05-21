---
title: 'Manage SIP federated domains for your organization'
ms.reviewer: 
ms:assetid: abc48829-e5cf-4651-bc38-899192f5c3bc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552454(v=OCS.15)
ms:contentKeyID: 48679565
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to manage and configure SIP domains that you can federate with,"
---

# Manage SIP federated domains for your organization in Skype for Business Server


To manage and configure SIP domains that you can federate with, you can do the following:

  - Create or edit an allowed domain list of SIP federated partner domains.

  - Create or edit a blocked domain list of SIP federated domains.

## Configure support for allowed external domains in Skype for Business Server

If you have configured support for federated partners, you can manage which specific domains can federate with your organization. You configure one or more specific external domains as allowed federated domains. To do this, add each domain to the list of allowed domains. Even if partner discovery is enabled for your organization, do this if the domain is a federated partner that might need to communicate with more than 1,000 of your users or might need to send more than 20 messages per second. If partner discovery is not enabled for your organization, only users of external domains that you add to the allowed domains list can participate in IM and conferencing with users in your organization. If you want to restrict access for a federated domain to a specific server running the Access Edge service of the federated partner, you can specify the domain name of the server running the Access Edge service for each domain in the list of allowed domains.

> [!NOTE]  
> This procedure describes how to configure support for specific domains, but implementing support for federated users also requires that you enable support for federated users for your organization, and configure and apply policies to control which users can collaborate with federated users. For details about enabling support for federated users, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md). For details about configuring policies to control federation, see [Configure policies to control federated user access](../external-access-policies/configure-policies-to-control-federated-user-access.md).

### To add an external domain to the list of allowed domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3.  In the left navigation bar, click **External User Access**, and then click **Federated Domains**.
4.  On the **Federated Domains** page, click **New**, and then click **Allowed domain**.
5.  In **New Federated Domains**, do the following:
    
      - In **Domain name (or FQDN)**, type the name of the federated partner domain.       

        > [!NOTE]  
        > This name must be unique and cannot already exist as an allowed domain for this server running the Access Edge service. The name cannot exceed 256 characters in length.<BR><br>The search on the federated partner domain name performs a suffix match. For example, if you type **contoso.com**, the search will also return the domain **it.contoso.com**.<BR><br>A federated partner domain cannot simultaneously be blocked and allowed. Skype for Business Server prevents this from happening so that you do not have to sync up your lists.
    
      - If you want to restrict access for this federated domain to users of a specific server running the Access Edge service, in **Access Edge service (FQDN)**, type the FQDN of the federated domain’s server running the Access Edge service.    
      - If you want to provide additional information, in **Comment**, type information that you want to share with other system administrators about this configuration.

6.  Click **Commit**.
7.  Repeat steps 4 through 6 for each federated partner domain that you want to allow.

To enable federated user access, you must also enable support for federated user access in your organization. For details, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md).

Additionally, you must configure and apply the policy to users that you want to be able to collaborate with federated users. For details, see [Configure policies to control federated user access](../external-access-policies/configure-policies-to-control-federated-user-access.md).

## Configure support for blocked external domains in Skype for Business Server 

If you have configured support for federated partners, you can manage which domains will be blocked from federating with your organization. The list of blocked domains will act as a block list (listing of explicit entries that are not to be allowed) and will apply in federated domain discovery, if you have this option enabled. For details, see [Enable or disable discovery of federation partners](../access-edge/enable-or-disable-discovery-of-federation-partners.md).

Block one or more external domains from connecting to your organization. To do this, add the domain to the list of blocked domains.


### To add an external domain to the list of blocked domains

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
3.  In the left navigation bar, click **External User Access**.
4.  Click **Federated Domains**, click **New**, and then click **Blocked domain**.
5.  In **New Federated Domains**, do the following:
    
      - In **Domain name (or FQDN)**, type the name of the federated partner domain that you want to block.

        > [!NOTE]  
        > The name cannot exceed 256 characters in length.<BR><br>The search on the federated partner domain name performs a suffix match. For example, if you type **contoso.com**, the search will also return the domain **it.contoso.com**.<BR><br>A federated partner domain cannot simultaneously be blocked and allowed. Skype for Business Server prevents this from happening so that you do not have to sync up your lists.
   
      - (Optional) In **Comment**, type information that you want to share with other system administrators about this configuration.

6.  Click **Commit**.
7.  Repeat steps 4 through 6 for each federated partner that you want to block.

To enable federated user access, you must also enable support for federated user access in your organization. For details, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md).

Additionally, you must configure and apply the policy to users that you want to be able to collaborate with federated users. For details, see [Configure policies to control federated user access](../external-access-policies/configure-policies-to-control-federated-user-access.md).


## See Also

[Configure policies to control federated user access](../external-access-policies/configure-policies-to-control-federated-user-access.md)  

[Enable or disable federation and public IM connectivity](../access-edge/enable-or-disable-federation-and-public-im-connectivity.md)

[Enable or disable discovery of federation partners](../access-edge/enable-or-disable-discovery-of-federation-partners.md)
  

