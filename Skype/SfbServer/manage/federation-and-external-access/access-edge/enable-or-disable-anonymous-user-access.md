---
title: 'Enable or disable anonymous user access'
ms.reviewer: 
ms:assetid: f10c19e6-b6f9-4d26-9923-0165f36e4af8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619192(v=OCS.15)
ms:contentKeyID: 49733872
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: ""
---

# Enable or disable anonymous user access in Skype for Business Server

Anonymous users are users who do not have a user account in your organization's Active Directory Domain Services or in a supported federated domain, but can be invited to participate remotely in an on-premises conference. By allowing anonymous participation in meetings you enable anonymous users (that is, users whose identity is verified through the meeting or conference key only) to join meetings. Allowing anonymous participation requires enabling it for your organization.

If you later want to temporarily or permanently prevent access by anonymous users, you can disable it for your organization. Use the procedure in this section to enable or disable anonymous user access for your organization.

> [!NOTE]  
> By enabling anonymous user access for your organization you are only specifying that your servers running the Access Edge service support access by anonymous users. Anonymous users cannot participate in any meetings in your organization until you also configure at least one conferencing policy and apply it to one or more users or user groups. The only users that can invite anonymous users to meetings are those users that are assigned a conferencing policy that is configured to support anonymous users. For details about configuring conferencing policies to support inviting anonymous users, see [Manage conferencing policies](../../conferencing/conferencing-policies.md).

## To enable or disable anonymous user access for your organization

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **External User Access**, and then click **Access Edge Configuration**.

4.  On the **Access Edge Configuration** page, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Access Edge Configuration**, do one of the following:
    
      - To enable anonymous user access for your organization, select the **Enable communications with anonymous users** check box.
    
      - To disable anonymous user access for your organization, clear the **Enable communications with anonymous users** check box.

6.  Click **Commit**.


## Enabling or disabling anonymous user access by using Windows PowerShell cmdlets

You can manage anonymous user access by using Windows PowerShell and the **Set-CsAccessEdgeConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

## To enable anonymous user access

  - To enable anonymous user access, set the value of the **AllowAnonymousUsers** property to True ($True):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True

## To disable anonymous user access

  - To disable anonymous user access, set the value of the **AllowAnonymousUsers** property to False ($False):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $False


## See Also

[Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy?view=skype-ps)  
  
