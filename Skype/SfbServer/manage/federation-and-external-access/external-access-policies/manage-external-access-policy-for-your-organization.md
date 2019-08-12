---
title: 'Manage external access policy for your organization'
ms.reviewer: 
ms:assetid: 5571811e-34c8-443a-b94c-1ab5d4275581
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520995(v=OCS.15)
ms:contentKeyID: 48184160
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After deploying one or more Edge Servers, you must enable the types of external access that will be supported for your organization."
---


# Manage external access policy for your organization

After deploying one or more Edge Servers, you must enable the types of external access that will be supported for your organization.

By default, there are no policies configured to support external user access, including remote user access, federated user access, even if you have already enabled external user access support for your organization. To control the use of external user access, you must configure one or more policies, specifying the type of external user access supported for each policy. The following policy scopes are available for creation and configuration. By default, the Global policy is created, but cannot be deleted.

  - **Global policy**   The global policy is created when you deploy your Edge Servers. By default, no external user access options are enabled in the global policy. To support external user access at the global level, you configure the global policy to support one or more types of external user access options. The global policy applies to all users in your organization, but site policies and user policies override the global policy. If you delete the global policy, you do not remove it. Instead, you reset it to the default setting.

  - **Site policy**   You can create and configure one or more site policies to limit support for external user access to specific sites. The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy. For example, if you enable remote user access in the global policy, you might specify a site policy that disables remote user access for a specific site. By default, a site policy is applied to all users of that site, but you can assign a user policy to a user to override the site policy setting.

  - **User policy**   You can create and configure one or more user policies to limit support for remote user access to specific users. The configuration in the user policy overrides the global and site policy, but only for the specific users to whom the user policy is assigned. For example, if you enable remote user access in the global policy and site policy, you might specify a user policy that disables remote user access and then assign that user policy to specific users. If you create a user policy, you must apply it to one or more users before it takes effect.


> [!IMPORTANT]  
> Policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.


These options include the following types of external access:

  - **Enable communications with federated users**   Enable this if you want to support user access to federated partner domains. This setting configures the ability for users to communicate with other SIP federated domains, as well as Hosted providers like Microsoft Office 365. 


  - **Enable communications with remote users**   Enable this option if you want users in your organization who are outside your firewall, such as telecommuters and users who are traveling, to be able to connect to Skype for Business Server over the Internet.

  - **Enable communications with public users**   Enable this option if you want internal users to be able to communicate with public IM provider contacts.
   

> [!NOTE]  
> In addition to enabling external user access support, you must also configure policies to control the use of external user access in your organization before any type of external user access is available to users. For details about creating, configuring, and applying policies for external user access see [Enable or disable remote user access](../access-edge/enable-or-disable-remote-user-access.md).



**To view external access policies by using Windows PowerShell cmdlets**

  - You can view external access policies by using Skype for Business Server Management Shell and the **Get-CsExternalAccessPolicy** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 
    
    To view information about all your external access policies, type the following command in the Lync Server Management Shell and then press ENTER:
    
    `Get-CsExternalAccessPolicy`
    
    This command returns information similar to the following:
    
    ```
    Identity                          : Global
    Description                       :
    EnableFederationAccess            : False
    EnableXmppAccess                  : False
    EnablePublicCloudAccess           : False
    EnablePublicCloudAudioVideoAccess : False
    EnableOutsideAccess               : False
    ```
