---
title: 'Enable or disable remote user access'
ms.reviewer: 
ms:assetid: cd9d3ddc-4839-457a-86d9-b15413e74002
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182586(v=OCS.15)
ms:contentKeyID: 48185660
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "If you enable remote user access for remote users, supported remote users connect over the Internet and do not have to connect using a VPN in order to collaborate with internal users using Skype for Business Server."
---


# Enable or disable remote user access in Skype for Business Server

Remote users are users in your organization who have a persistent Active Directory identity within the organization. Remote users often sign in to Skype for Business Server from outside your network by using a virtual private network (VPN) when they are not connected to your organization’s network. Remote users include employees working at home or on the road and other remote workers, such as trusted vendors, who have been granted enterprise credentials. If you enable remote user access for remote users, supported remote users connect over the Internet and do not have to connect using a VPN in order to collaborate with internal users using Skype for Business Server.

To support remote user access, you must enable remote user access. When you enable remote user access, you enable it for your entire organization. If you later want to temporarily or permanently prevent remote user access, you can disable it for your organization. Use the procedure in this section to enable or disable remote user access for your organization.


> [!NOTE]  
> Enabling remote user access only specifies that your servers running the Access Edge service support communications with remote users, but remote users cannot participate in instant messaging (IM) or conferences in your organization until you also configure at least one policy to manage the use of remote user access. Skype for Business Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object. For details about configuring policies for the use of remote user access, see [Configure policies to control remote user access in Skype for Business Server](../external-access-policies/configure-policies-to-control-remote-user-access.md).


## To enable or disable remote user access for your organization

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Federation and External Access**, and then click **Access Edge Configuration**.

4.  On the **Access Edge Configuration** page, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Access Edge Configuration**, do one of the following:
    
      - To enable remote user access for your organization, select the **Enable remote user access** check box.
    
      - To disable remote user access for your organization, clear the **Enable remote user access** check box.

6.  Click **Commit**.

To enable remote users to sign in to your servers running Skype for Business Server, you must also configure at least one external access policy to support remote user access. For details, see [Configure policies to control remote user access in Skype for Business Server](../external-access-policies/configure-policies-to-control-remote-user-access.md).


## Enabling or disabling remote user access by using Windows PowerShell cmdlets

Remote user access can be managed by using Windows PowerShell and the Set-CsAccessEdgeConfiguration cmdlet. This cmdlet can be run either from the Skype for Business Server 2013 Management Shell or from a remote session of Windows PowerShell. 

## To enable remote user access

  - To enable remote user access, set the value of the **AllowOutsideUsers** property to True ($True):
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $True

## To disable remote user access

  - To disable remote user access, set the value of the **AllowOutsideUsers** property to False ($False):
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $False


