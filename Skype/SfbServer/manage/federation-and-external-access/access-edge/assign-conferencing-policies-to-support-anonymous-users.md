---
title: 'Assign conferencing policies to support anonymous users'
ms.reviewer: 
ms:assetid: 662de022-1111-40f7-bad4-f2b686f30973
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521007(v=OCS.15)
ms:contentKeyID: 48184333
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You control who can invite anonymous users by configuring a conferencing policy to support anonymous users, and applying that conferencing policy to specific users."
---

# Assign conferencing policies to support anonymous users in Skype for Business Server 


By default, all users are prevented from inviting anonymous users to participate in a meeting. You control who can invite anonymous users by configuring a conferencing policy to support anonymous users, and applying that conferencing policy to specific users. For details about how to configure a conferencing policies to support anonymous users, see [Create conferencing policies in Skype for Business Server](../../conferencing/create-policies.md) and [Managing federation and external access to Skype for Business Server](../managing-federation-and-external-access.md).

Use the procedure in this section to apply a conferencing policy that you have already created to one or more users or user groups.

> [!NOTE]  
> In addition to configuring and applying a policy to enable users to invite anonymous users, you must also enable support for anonymous users for your organization. For details, see [Configure policies to control public user access in Skype for Business Server](../external-access-policies/configure-policies-to-control-public-user-access.md).


## To configure a user policy for anonymous participation in meetings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Conferencing**, and then do one of the following:
    
    1.  To create a new user policy, click **New**, and then click **User policy**. Create a unique name in the **Name** field that indicates what the user policy covers (for example, **EnableAnonymous** for a user policy that enables communications with anonymous users).
    
    2.  To configure an existing user policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.

4.  In the **Conferencing Policies** dialog box, select the **Allow participants to invite anonymous users** check box.

5.  Click **Commit**.

6.  In the left navigation bar, click **Users**, search on the user account that you want to configure.

7.  In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.

8.  In **Edit Skype for Business Server User** under **Conferencing policy**, select the user policy with the anonymous user access configuration that you want to apply to this user.  

    > [!NOTE]  
    > The <STRONG>&lt;Automatic&gt;</STRONG> settings apply the default server installation settings and are applied automatically by the server.


To enable users to invite anonymous users to conferences, you must also enable support for anonymous users in your organization. For details, see [Configure policies to control public user access in Skype for Business Server](../external-access-policies/configure-policies-to-control-public-user-access.md).

