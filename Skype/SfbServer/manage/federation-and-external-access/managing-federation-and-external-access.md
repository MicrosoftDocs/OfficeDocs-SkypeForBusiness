---
title: 'Lync Server 2013: Managing federation and external access to Skype for Business Server'
ms.reviewer: 
ms:assetid: 26f806c1-f284-4637-b06b-06270336c540
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520966(v=OCS.15)
ms:contentKeyID: 48183665
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You enable and configure external user access to control whether supported external users can collaborate with internal Skype for Business Server users."
---


# Managing federation and external access to Skype for Business Server

Deploying an Edge Server or Edge pool is the first step to supporting external users. For details about deploying Edge Servers, see [Deploy Edge Server in Skype for Business Server](../../deploy/deploy-edge-server/deploy-edge-server.md).

After installing and configuring your internal deployment of Skype for Business Server, internal users in your organization can collaborate with other internal users who have SIP accounts in your Active Directory Domain Services (AD DS). Collaboration can include sending and receiving instant messages, and update of presence status and participating in conferences (also known as "meetings"). You enable and configure external user access to control whether supported external users can collaborate with internal Skype for Business Server users. External users can include remote users of your deployment, federated users (including supported users of public instant messaging (IM) service providers), and anonymous participants in conferences.

If your deployment included the installation of a Skype for Business Server Edge Server or an Edge pool, the scope of possible communication types is greatly expanded with a number of options for external user access, communication with members of other SIP federated domains and SIP federated providers. After setting up the Edge Server or Edge pool, you enable the types of external user access that you want to provide, and configure the policies to control for the external access. In Skype for Business Server, you enable and configure external user access and policies using the Skype for Business Server Control Panel, the [Skype for Business Server Management Shell](../management-shell.md), or both, based on the task requirements. 



> [!IMPORTANT]  
> When you design your configuration and policies for external user access, you must understand the precedence of policies and how the policies are applied. Skype for Business Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Skype for Business Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object.


By default, no policies are configured to support external user access, including remote user access, federated user access, even if you have already enabled external user access support for your organization. To control the use of external user access, you must configure one or more policies, specifying the type of external user access supported for each policy. This includes the following external access policies:

  - **Global policy**   The global policy is created when you deploy your Edge Servers. By default, no external user access options are enabled in the global policy. To support external user access at the global level, you configure the global policy to support one or more types of external user access options. The global policy applies to all users in your organization, but site policies and user policies override the global policy. If you delete the global policy, you do not remove it. Instead, you reset it to the default setting.

  - **Site policy**   You can create and configure one or more site policies to limit support for external user access to specific sites. The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy. For example, if you enable remote user access in the global policy, you might specify a site policy that disables remote user access for a specific site. By default, a site policy is applied to all users of that site, but you can assign a user policy to a user to override the site policy setting.

  - **User policy**   You can create and configure one or more user policies to limit support for remote user access to specific users. The configuration in the user policy overrides the global and site policy, but only for the specific users to whom the user policy is assigned. For example, if you enable remote user access in the global policy and site policy, you might specify a user policy that disables remote user access and then assign that user policy to specific users. If you create a user policy, you must apply it to one or more users before it takes effect.

To determine which configuration settings and which policies you need to create or edit, refer to the following decision points:

**Do you want to allow internal and external users of your domain to be able to collaborate using instant messaging, Web conferencing, and Audio/Video?**

Configure the settings as detailed in the topics [Configure policies to control remote user acces](external-access-policies/configure-policies-to-control-remote-user-access.md), and [Enable or disable federation and public IM connectivity](access-edge/enable-or-disable-federation-and-public-im-connectivity.md).

**Do you want to allow anonymous users to attend and be invited to conferences hosted by users in your deployment?**

Configure the settings as detailed in the topic [Assign conferencing policies to support anonymous users](access-edge/assign-conferencing-policies-to-support-anonymous-users.md) and [Create conferencing policies](../conferencing/create-policies.md).

**Do you want to allow users to communicate with SIP Federated Domain contacts?**

Configure the settings as detailed in the topics [Configure policies to control federated user access](external-access-policies/configure-policies-to-control-federated-user-access.md), [Enable or disable federation and public IM connectivity](access-edge/enable-or-disable-federation-and-public-im-connectivity.md), and [Manage SIP federated domains for your organization](sip-domains/manage-sip-federated-domains-for-your-organization.md).


**If you have enabled communication with SIP Federated Domains, do you want to enable SIP Federation automatic discovery?**

Configure the settings as detailed in the topic [Enable or disable discovery of federation partners](access-edge/enable-or-disable-discovery-of-federation-partners.md).

**If you have enabled communication with SIP Federation Domains, do you want to enable sending a disclaimer to Federated contacts notifying them that you use archiving and that communications may be archived?**

Configure the settings as detailed in the topic [Enable or disable sending an Archiving disclaimer to federated partners in](access-edge/enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md).

**Do you want to allow users to communicate with SIP Federated Providers that enable communication with public providers?**

Configure the settings as detailed in the topics [Configure policies to control public user access](external-access-policies/configure-policies-to-control-public-user-access.md), [Enable or disable federation and public IM connectivity](access-edge/enable-or-disable-federation-and-public-im-connectivity.md), and [Create or edit public SIP federated providers](sip-providers/manage-sip-federated-providers-for-your-organization.md#create-or-edit-public-sip-federated-providers-in-skype-for-business-server)


**Do you want to allow users to communicate with SIP Federated Providers that are hosted providers running Microsoft Office 365 and Skype for Business Online?**

Configure the settings as detailed in the topics [Enable or disable federation and public IM connectivity](access-edge/enable-or-disable-federation-and-public-im-connectivity.md) and [Create or edit hosted SIP federated providers](sip-providers/manage-sip-federated-providers-for-your-organization.md#create-or-edit-hosted-sip-federated-providers-in-skype-for-business-server).

**Is your deployment configured in a split (also known as a hybrid) domain, where some users have their home server in an on-premise deployment, and other users are configured with a home server in an online environment?**

Configure the settings as detailed in the topics [Configure policies to control federated user access](external-access-policies/configure-policies-to-control-federated-user-access.md), [Enable or disable federation and public IM connectivity](access-edge/enable-or-disable-federation-and-public-im-connectivity.md), and [Create or edit hosted SIP federated providers](sip-providers/manage-sip-federated-providers-for-your-organization.md#create-or-edit-hosted-sip-federated-providers-in-skype-for-business-server).


You can configure external user access settings, including any policies that you want to use to control external user access, even if you have not enabled external user access for your organization. However, the policies and other settings that you configure are in effect only when you have external user access enabled for your organization. External users cannot communicate with users of your organization when external user access is disabled or if no external user access policies are configured to support it.

Your edge deployment authenticates the types of external users (except for anonymous users, who are authenticated by the conference ID and a passkey that is sent to the anonymous participant when you create the conference and invite participants) and controls access based on how you configure your edge support. In order to control communications, you can configure one or more policies and configure settings that define how users inside and outside your deployment communicate with each other. The policies and settings include the default global policy for external user access, in addition to site and user policies that you can create and configure to enable one or more types of external user access for specific sites or users.

