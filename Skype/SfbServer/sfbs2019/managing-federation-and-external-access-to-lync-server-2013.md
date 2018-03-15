---
title: "Managing federation and external access to Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26f806c1-f284-4637-b06b-06270336c540

description: "Deploying an Edge Server or Edge pool is the first step to supporting external users. For details about deploying Edge Servers, see Deploying external user access in Lync Server 2013 in the Deployment documentation."
---

# Managing federation and external access to Lync Server 2013
[]
Deploying an Edge Server or Edge pool is the first step to supporting external users. For details about deploying Edge Servers, see [Deploying external user access in Lync Server 2013](deploying-external-user-access.md) in the Deployment documentation. 
  
After installing and configuring your internal deployment of Lync Server 2013, internal users in your organization can collaborate with other internal users who have SIP accounts in your Active Directory Domain Services (AD DS). Collaboration can include sending and receiving instant messages, and update of presence status and participating in conferences (also known as "meetings"). You enable and configure external user access to control whether supported external users can collaborate with internal Lync Server users. External users can include remote users of your deployment, federated users (including supported users of public instant messaging (IM) service providers), XMPP federation and anonymous participants in conferences.
  
If your deployment included the installation of a Lync Server 2013 Edge Server or an Edge pool, the scope of possible communication types is greatly expanded with a number of options for external user access, communication with members of other SIP federated domains, SIP federated providers, and XMPP federated users. After setting up the Edge Server or Edge pool, you enable the types of external user access that you want to provide, and configure the policies to control for the external access. In Lync Server 2013, you enable and configure external user access and policies using the Lync Server Control Panel, the Lync Server Management Shell or both, based on the task requirements. For details about these management tools, see [Lync Server 2013 administrative tools](lync-server-administrative-tools.md) in the Operations documentation, [Lync Server 2013 Management Shell](lync-server-management-shell.md) in the Operations documentation, and [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md) in the Operations documentation. 
  
> [!IMPORTANT]
> When you design your configuration and policies for external user access, you must understand the precedence of policies and how the policies are applied. Lync Server policy settings that are applied at one policy level can override settings that are applied at another policy level. Lync Server policy precedence is: User policy (most influence) overrides a Site policy, and then a Site policy overrides a Global policy (least influence). This means that the closer the policy setting is to the object that the policy is affecting, the more influence it has on the object. 
  
By default, no policies are configured to support external user access, including remote user access, federated user access, even if you have already enabled external user access support for your organization. To control the use of external user access, you must configure one or more policies, specifying the type of external user access supported for each policy. This includes the following external access policies:
  
- **Global policy** The global policy is created when you deploy your Edge Servers. By default, no external user access options are enabled in the global policy. To support external user access at the global level, you configure the global policy to support one or more types of external user access options. The global policy applies to all users in your organization, but site policies and user policies override the global policy. If you delete the global policy, you do not remove it. Instead, you reset it to the default setting. 
    
- **Site policy** You can create and configure one or more site policies to limit support for external user access to specific sites. The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy. For example, if you enable remote user access in the global policy, you might specify a site policy that disables remote user access for a specific site. By default, a site policy is applied to all users of that site, but you can assign a user policy to a user to override the site policy setting. 
    
- **User policy** You can create and configure one or more user policies to limit support for remote user access to specific users. The configuration in the user policy overrides the global and site policy, but only for the specific users to whom the user policy is assigned. For example, if you enable remote user access in the global policy and site policy, you might specify a user policy that disables remote user access and then assign that user policy to specific users. If you create a user policy, you must apply it to one or more users before it takes effect. 
    
To determine which configuration settings and which policies you need to create or edit, refer to the following decision points:
  
 **Do you want to allow internal and external users of your domain to be able to collaborate using instant messaging, Web conferencing, and Audio/Video?**
  
Configure the settings as detailed in the topics [Configure policies to control remote user access in Lync Server 2013](configure-policies-to-control-remote-user-access.md), and [Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md)
  
 **Do you want to allow anonymous users to attend and be invited to conferences hosted by users in your deployment?**
  
Configure the settings as detailed in the topic [Assign conferencing policies to support anonymous users in Lync Server 2013](assign-conferencing-policies-to-support-anonymous-users.md), [Create or modify a conferencing policy in Lync Server 2013](create-or-modify-a-conferencing-policy.md) and [Conferencing policy settings reference for Lync Server 2013](conferencing-policy-settings-reference.md)
  
 **Do you want to allow users to communicate with SIP Federated Domain contacts?**
  
Configure the settings as detailed in the topics [Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md), [Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md), and [Manage SIP federated domains for your organization in Lync Server 2013](manage-sip-federated-domains-for-your-organization.md)
  
 **If you have enabled communication with SIP Federation Domains, do you want to enable communications with XMPP Federated Partner contacts?**
  
Configure the settings as detailed in the topic [Configure policies to control XMPP federated user access in Lync Server 2013](configure-policies-to-control-xmpp-federated-user-access.md) and [Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md).
  
 **If you have enabled communication with SIP Federated Domains, do you want to enable SIP Federation automatic discovery?**
  
Configure the settings as detailed in the topic [Enable or disable discovery of federation partners in Lync Server 2013](enable-or-disable-discovery-of-federation-partners.md).
  
 **If you have enabled communication with SIP Federation Domains, do you want to enable sending a disclaimer to Federated contacts notifying them that you use archiving and that communications may be archived?**
  
Configure the settings as detailed in the topic [Enable or disable sending an Archiving disclaimer to federated partners in Lync Server 2013](enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md).
  
 **Do you want to allow users to communicate with SIP Federated Providers that enable communication with public providers, such as Windows Live Messenger, AOL, and Yahoo!?**
  
Configure the settings as detailed in the topics [Configure policies to control public user access in Lync Server 2013](configure-policies-to-control-public-user-access.md)[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md), and [Create or edit public SIP federated providers in Lync Server 2013](create-or-edit-public-sip-federated-providers.md).
  
> [!IMPORTANT]
>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License ("PIC USL") is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md). >  The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice. 
  
 **Do you want to allow users to communicate with SIP Federated Providers that are hosted providers running Microsoft Office 365, Skype for Business Online and Microsoft Lync Online 2010?**
  
Configure the settings as detailed in the topics [Create or edit public SIP federated providers in Lync Server 2013](create-or-edit-public-sip-federated-providers.md), [Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) and [Create or edit hosted SIP federated providers Lync Server 2013](create-or-edit-hosted-sip-federated-providers.md)
  
 **Is your deployment configured in a split (also known as a hybrid) domain, where some users have their home server in an on-premise deployment, and other users are configured with a home server in an online environment?**
  
Configure the settings as detailed in the topics [Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md), [Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) and [Create or edit hosted SIP federated providers Lync Server 2013](create-or-edit-hosted-sip-federated-providers.md)
  
If you prefer a table that lists the requirements:
  
|**Tab in Federation and External Access (Across)  <br/> Federation or External Access Type (Down)**|**External Access Policy**|**Access Edge Config**|**SIP Federated Domains**|**SIP Federated Providers**|**XMPP Federated Partner**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Remote Users  <br/> |[Configure policies to control remote user access in Lync Server 2013](configure-policies-to-control-remote-user-access.md) <br/> |[Enable or disable remote user access in Lync Server 2013](enable-or-disable-remote-user-access.md) <br/> ||||
|SIP Federated Contacts  <br/> |[Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md) <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> [Enable or disable discovery of federation partners in Lync Server 2013](enable-or-disable-discovery-of-federation-partners.md) <br/> [Enable or disable sending an Archiving disclaimer to federated partners in Lync Server 2013](enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md) <br/> |[Manage SIP federated domains for your organization in Lync Server 2013](manage-sip-federated-domains-for-your-organization.md) <br/> |||
|XMPP Federated Contacts  <br/> |[Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md) <br/> [Configure policies to control XMPP federated user access in Lync Server 2013](configure-policies-to-control-xmpp-federated-user-access.md) <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> |||[Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md) <br/> |
|Split Domain / Hybrid Users  <br/> |[Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md) <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> ||[Create or edit hosted SIP federated providers Lync Server 2013](create-or-edit-hosted-sip-federated-providers.md) <br/> ||
|Public IM Service Contacts  <br/> |[Configure policies to control public user access in Lync Server 2013](configure-policies-to-control-public-user-access.md) <br/> |[Enable or disable federation and public IM connectivity in Lync Server 2013](enable-or-disable-federation-and-public-im-connectivity.md) <br/> ||[Create or edit public SIP federated providers in Lync Server 2013](create-or-edit-public-sip-federated-providers.md) <br/> ||
|Anonymous user access to meetings and conferences  <br/> ||[Assign conferencing policies to support anonymous users in Lync Server 2013](assign-conferencing-policies-to-support-anonymous-users.md) <br/> > [!NOTE]> You must also consider the following configuration settings under Conferencing policies: [Create or modify a conferencing policy in Lync Server 2013](create-or-modify-a-conferencing-policy.md) and [Conferencing policy settings reference for Lync Server 2013](conferencing-policy-settings-reference.md)          ||||
   
You can configure external user access settings, including any policies that you want to use to control external user access, even if you have not enabled external user access for your organization. However, the policies and other settings that you configure are in effect only when you have external user access enabled for your organization. External users cannot communicate with users of your organization when external user access is disabled or if no external user access policies are configured to support it.
  
Your edge deployment authenticates the types of external users (except for anonymous users, who are authenticated by the conference ID and a passkey that is sent to the anonymous participant when you create the conference and invite participants) and controls access based on how you configure your edge support. In order to control communications, you can configure one or more policies and configure settings that define how users inside and outside your deployment communicate with each other. The policies and settings include the default global policy for external user access, in addition to site and user policies that you can create and configure to enable one or more types of external user access for specific sites or users.
  
## In this section

- [Manage external access policy in Lync Server 2013](manage-external-access-policy-for-your-organization.md)
    
- [Manage Access Edge Configuration for your organization in Lync Server 2013](manage-access-edge-configuration-for-your-organization.md)
    
- [Manage SIP federated domains for your organization in Lync Server 2013](manage-sip-federated-domains-for-your-organization.md)
    
- [Manage SIP federated providers for your organization in Lync Server 2013](manage-sip-federated-providers-for-your-organization.md)
    
- [Manage XMPP federated partners in Lync Server 2013](manage-xmpp-federated-partners-for-your-organization.md)
    
- [Configuring federation support for a Lync Online customer in Lync Server 2013](configuring-federation-support-for-a-lync-online-customer.md)
    

