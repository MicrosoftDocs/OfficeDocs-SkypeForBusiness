---
title: 'Configure support for blocked external domains'
ms:assetid: 49103138-e1ab-42bf-91aa-57cf23bbf260
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619176(v=OCS.15)
ms:contentKeyID: 49733638
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "If you have configured support for federated partners, you can manage which domains will be blocked from federating with your organization"
---


# Configure support for blocked external domains in Skype for Business Server 

If you have configured support for federated partners, you can manage which domains will be blocked from federating with your organization. The list of blocked domains will act as a block list (listing of explicit entries that are not to be allowed) and will apply in federated domain discovery, if you have this option enabled. For details, see [Enable or disable discovery of federation partners](../access-edge/enable-or-disable-discovery-of-federation-partners.md).

Block one or more external domains from connecting to your organization. To do this, add the domain to the list of blocked domains.


## To add an external domain to the list of blocked domains

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

