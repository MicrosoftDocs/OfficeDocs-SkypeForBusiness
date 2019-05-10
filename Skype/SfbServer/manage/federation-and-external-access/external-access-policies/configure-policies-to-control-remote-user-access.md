---
title: 'Configure policies to control remote user access'
ms.reviewer: 
ms:assetid: 8f556849-692b-44a0-9514-4468fc9a39d0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398725(v=OCS.15)
ms:contentKeyID: 48184825
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You configure one or more external user access policies to control whether remote users can collaborate with internal Skype for Business Server users. To control remote user access, you can configure policies at the global, site, and user level."
---

# Configure policies to control remote user access in Skype for Business Server

You configure one or more external user access policies to control whether remote users can collaborate with internal Skype for Business Server users. To control remote user access, you can configure policies at the global, site, and user level. Site policies override the global policy, and user policies override site and global policies. For details about the types of policies that you can configure, see [Managing federation and external access to Skype for Business Server](../managing-federation-and-external-access.md). Skype for Business Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.

> [!NOTE]  
> You can configure policies to control remote user access, even if you have not enabled remote user access for your organization. However, the policies that you configure are in effect only when you have remote user access enabled for your organization. Additionally, if you specify a user policy to control remote user access, the policy applies only to users that are enabled for Skype for Business Server and configured to use the policy. For details about specifying users that can sign in to Skype for Business Server from remote locations, see [Assign an external user access policy](assign-an-external-user-access-policy.md).

Use the following procedure to configure each external access policy that you want to use to control remote user access.


> [!NOTE]  
> This procedure describes how to configure a policy only to enable communications with remote users, but each policy that you configure to support remote user access can also configure federated user access and public user access. For details about configuring policies to support federated users, see [Configure policies to control federated user access in Skype for Business Server](configure-policies-to-control-federated-user-access.md). For details about configuring policies to support public users, see [Manage SIP federated providers for your organization in Skype for Business Server](../sip-providers/manage-sip-federated-providers-for-your-organization.md).


## To configure an external access policy to support remote user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **External User Access**, and then click **External Access Policy**.

4.  On the **External Access Policy** page, do one of the following:
    
      - To configure the global policy to support remote user access, click the global policy, click **Edit**, and then click **Show details**.
    
      - To create a new site policy, click **New**, and then click **Site policy**. In **Select a Site**, click the appropriate site from the list and then click **OK**.
    
      - To create a new user policy, click **New**, and then click **User policy**. In **New External Access Policy**, create a unique name in the **Name** field that indicates what the user policy covers (for example, **EnableRemoteUsers** for a user policy that enables communications for remote users).
    
      - To change an existing policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.

5.  (Optional) If you want to add or edit a description, specify the information for the policy in **Description**.

6.  Do one of the following:
    
      - To enable remote user access for the policy, select the **Enable communications with remote users** check box.
    
      - To disable remote user access for the policy, clear the **Enable communications with remote users** check box.

7.  Click **Commit**.

To enable remote user access, you must also enable support for remote user access in your organization. For details, see [Enable or disable federation and public IM connectivity](../access-edge/enable-or-disable-federation-and-public-im-connectivity.md).

If this is a user policy, you must also apply the policy to users that you want to be able to connect remotely. For details, see [Assign an external user access policy](assign-an-external-user-access-policy.md).
