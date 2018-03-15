---
title: "Assign conferencing policies to support anonymous users in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 662de022-1111-40f7-bad4-f2b686f30973
description: "By default, all users are prevented from inviting anonymous users to participate in a meeting. You control who can invite anonymous users by configuring a conferencing policy to support anonymous users, and applying that conferencing policy to specific users. For details about how to configure a conferencing policies to support anonymous users, see Create or modify a conferencing policy in Lync Server 2013 and Managing federation and external access to Lync Server 2013."
---

# Assign conferencing policies to support anonymous users in Lync Server 2013
[]
By default, all users are prevented from inviting anonymous users to participate in a meeting. You control who can invite anonymous users by configuring a conferencing policy to support anonymous users, and applying that conferencing policy to specific users. For details about how to configure a conferencing policies to support anonymous users, see [Create or modify a conferencing policy in Lync Server 2013](create-or-modify-a-conferencing-policy.md) and [Managing federation and external access to Lync Server 2013](managing-federation-and-external-access-to-lync-server-2013.md).
  
Use the procedure in this section to apply a conferencing policy that you have already created to one or more users or user groups.
  
> [!NOTE]
> In addition to configuring and applying a policy to enable users to invite anonymous users, you must also enable support for anonymous users for your organization. For details, see [Configure policies to control public user access in Lync Server 2013](configure-policies-to-control-public-user-access.md). 
  
### To configure a user policy for anonymous participation in meetings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing**, and then do one of the following:
    
1. To create a new user policy, click **New**, and then click **User policy**. Create a unique name in the **Name** field that indicates what the user policy covers (for example, EnableAnonymous for a user policy that enables communications with anonymous users). 
    
2. To configure an existing user policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.
    
4. In the **Conferencing Policies** dialog box, select the **Allow participants to invite anonymous users** check box. 
    
5. Click **Commit**.
    
6. In the left navigation bar, click **Users**, search on the user account that you want to configure. 
    
7. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
8. In **Edit Lync Server User** under **Conferencing policy**, select the user policy with the anonymous user access configuration that you want to apply to this user. 
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default server installation settings and are applied automatically by the server. 
  
To enable users to invite anonymous users to conferences, you must also enable support for anonymous users in your organization. For details, see [Configure policies to control public user access in Lync Server 2013](configure-policies-to-control-public-user-access.md) in the Deployment documentation or the Operations documentation. 

