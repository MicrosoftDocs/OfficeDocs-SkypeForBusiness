---
title: "Configure support for blocked external domains in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 49103138-e1ab-42bf-91aa-57cf23bbf260
description: "If you have configured support for federated partners, you can manage which domains will be blocked from federating with your organization. The list of blocked domains will act as a block list (listing of explicit entries that are not to be allowed) and will apply in federated domain discovery, if you have this option enabled. For details, see Enable or disable discovery of federation partners in Lync Server 2013."
---

# Configure support for blocked external domains in Lync Server 2013
[]
If you have configured support for federated partners, you can manage which domains will be blocked from federating with your organization. The list of blocked domains will act as a block list (listing of explicit entries that are not to be allowed) and will apply in federated domain discovery, if you have this option enabled. For details, see [Enable or disable discovery of federation partners in Lync Server 2013](enable-or-disable-discovery-of-federation-partners.md).
  
Block one or more external domains from connecting to your organization. To do this, add the domain to the list of blocked domains.
  
### To add an external domain to the list of blocked domains

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **External User Access**.
    
4. Click **Federated Domains**, click **New**, and then click **Blocked domain**.
    
5. In **New Federated Domains**, do the following:
    
  - In **Domain name (or FQDN)**, type the name of the federated partner domain that you want to block. 
    
    > [!NOTE]
    > The name cannot exceed 256 characters in length. > The search on the federated partner domain name performs a suffix match. For example, if you type contoso.com, the search will also return the domain **it.contoso.com**. > A federated partner domain cannot simultaneously be blocked and allowed. Lync Server 2013 prevents this from happening so that you do not have to synch up your lists. 
  
  - (Optional) In **Comment**, type information that you want to share with other system administrators about this configuration. 
    
6. Click **Commit**.
    
7. Repeat steps 4 through 6 for each federated partner that you want to block.
    
To enable federated user access, you must also enable support for federated user access in your organization. For details, see [Enable or disable remote user access in Lync Server 2013](enable-or-disable-remote-user-access.md).Additionally, you must configure and apply the policy to users that you want to be able to collaborate with federated users. For details, see [Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md).

