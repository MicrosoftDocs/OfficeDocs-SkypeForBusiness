---
title: 'Configure policies to control public user access'
ms.reviewer: 
ms:assetid: 090aea0f-ef0b-49da-9c80-02d9279f2fa6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520946(v=OCS.15)
ms:contentKeyID: 48183343
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "ublic instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by public IM service providers."
---


# Configure policies to control public user access in Skype for Business Server

Public instant messaging (IM) connectivity enables users in your organization to use IM to communicate with users of IM services provided by public IM service providers. You configure one or more external user access policies to control whether public users can collaborate with internal Skype for Business Server users. Public instant messaging connectivity is an added feature that relies on configuration of your deployment and users. It also depends on the provisioning of the service at the public IM provider. 

To control public user access, you can configure policies at the global, site, and user level. Skype for Business Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.

In the case of IM invitations, the response depends on the client software. The request is accepted unless external senders are explicitly blocked by a user-configured rule (that is, the settings in the user’s client **Allow** and **Block** lists). Additionally, IM invitations can be blocked if a user elects to block all IM from users who are not on his or her **Allow** list.



> [!NOTE]  
> You can configure policies to control public user access, even if you have not enabled federation for your organization. However, the policies that you configure are in effect only when you have federation enabled for your organization. For details about enabling federation, see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md). Additionally, if you specify a user policy to control public user access, the policy applies only to users that are enabled for Skype for Business Server and configured to use the policy. For details about specifying public users that can sign in to Skype for Business Server, see [Assign an external user access policy](assign-an-external-user-access-policy.md).


Use the following procedure to configure a policy to support access by users of one or more public IM providers.

## To configure an external access policy to support public user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **External User Access**, and then click **External Access Policy**.

4.  On the **External Access Policy** page, do one of the following:
    
      - To configure the global policy to support public user access, click the global policy, click **Edit**, and then click **Show details**.
    
      - To create a new site policy, click **New**, and then click **Site policy**. In **Select a Site**, click the appropriate site from the list and then click **OK**.
    
      - To create a new user policy, click **New**, and then click **User policy**. In **New External Access Policy**, create a unique name in the **Name** field that indicates what the user policy covers (for example, **EnablePublicUsers** for a user policy that enables communications for public users).
    
      - To change an existing policy, click the appropriate policy listed in the table, click **Edit**, and then click **Show details**.

5.  (Optional) If you want to add or edit a description, specify the information for the policy in **Description**.

6.  Do one of the following:
    
      - To enable public user access for the policy, select the **Enable communications with public users** check box.
    
      - To disable public user access for the policy, clear the **Enable communications with public users** check box.

7.  Click **Commit**.

To enable public user access, you must also enable support for federation in your organization. For details, see [Configure policies to control federated user access in Skype for Business Server](configure-policies-to-control-federated-user-access.md).

If this is a user policy, you must also apply the policy to public users that you want to be able to collaborate with public users. 


## See Also

[Manage SIP federated providers for your organization](../sip-providers/manage-sip-federated-providers-for-your-organization.md)
