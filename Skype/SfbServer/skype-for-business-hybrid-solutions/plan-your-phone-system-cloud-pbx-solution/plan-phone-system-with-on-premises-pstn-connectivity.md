---
title: "Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/26/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 021a4c0b-d5de-4155-a506-650d758624aa
description: "Learn about the planning considerations for Phone System in Office 365 (Cloud PBX) with on-premises PSTN connectivity."
---

# Plan Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server

Learn about the planning considerations for Phone System in Office 365 (Cloud PBX) with on-premises PSTN connectivity.

This content is relevant if you already have Skype for Business Server or Lync Server 2013 deployed on-premises. For other scenarios, see [Microsoft telephony solutions](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/msft-telephony-solutions).

 Phone System in Office 365 with on-premises PSTN connectivity enables you to leverage Phone System (Cloud PBX) capabilities for your users. This can help with the following scenarios:

- You have some of your Skype for Business users homed on-premises and others homed in Skype for Business Online. You can now enable Phone System in Office 365 capabilities and features for your users homed in Skype for Business Online, but continue to use on-premises PSTN connectivity.

- You have an on-premises deployment and you want to move some or all of your users to Skype for Business Online but continue to use on-premises PSTN connectivity.

    > [!IMPORTANT]
    > To successfully enable users for Phone System in Office 365 with on-premises PSTN connectivity, their SIP address must be in your own domain. The use of the default domain for Office 365, onmicrosoft.com, is not supported. 

To learn more about Phone System in Office 365 including licensing and plans, see [PSTN Calling plans for Skype for Business](https://support.office.com/article/PSTN-Calling-plans-for-Skype-for-Business-f47c6a97-bc8b-42e6-b5d4-ce6b41ed1918).

## Feature comparison

Cloud PBX with on-premises PSTN Connectivity does not offer the same feature set as a fully on-premises Enterprise Voice solution. To help you decide whether Cloud PBX with on-premises PSTN Connectivity will provide the right feature set for your organization, see [Here's what you get with Cloud PBX](https://go.microsoft.com/fwlink/?LinkId=715517).

## Benefits and planning considerations

> [!CAUTION]
> Lync Phone Edition devices MUST be updated to minimum required firmware in your on premises environment PRIOR to moving to Skype for Business Online.
If you move your users from on-premises to online prior to updating the firmware, users will be unable to connect using their phones. To correct this problem, users must be moved back to the on premises environment to have their phones updated to the minimum firmware. DO NOT ATTEMPT TO UPDATE TO MINIMUM FIRMWARE OR HARD RESET THE PHONE PRIOR TO MOVING THE USER BACK TO YOUR ON PREMISES ENVIRONMENT.
 If a hard reset is performed while the device is not at minimum firmware it will default to using PIN Authentication, which is not supported in Skype for Business Online. For more information, please refer to [Getting phones for Skype for Business Online](https://support.office.com/en-us/article/Getting-phones-for-Skype-for-Business-Online-91f2d947-45fc-4fab-bd8b-2e313531c477?ui=en-US&amp;rs=en-US&amp;ad=US).

By deploying Phone System in Office 365 with on-premises PSTN connectivity, you can move your users to the cloud via Skype for Business Online at your own pace, while retaining their on-premises PSTN connectivity. If you have a PBX, you continue to use it to provide PSTN connectivity for the users you move to the cloud. Once a user is moved to Skype for Business Online and Phone System in Office 365, their legacy PBX phone will no longer work, but their phone number will route to any of the Skype for Business clients for PCs or Smart phones as well as Skype for Business-compliant desk phones. Once ported, Phone System in Office 365 users and legacy PBX users can call each other normally as well as make/receive PSTN calls using their normal phone number.

You may have a custom feature or a major add-on to your legacy PBX, such as a call center. If the custom feature is not currently available on Phone System in Office 365, you should leave those users that require that custom feature on-premises with the legacy PBX, and just port the users who do not need to access the custom feature to Phone System in Office 365 with on-premises PSTN connectivity.

For a list of legacy PBXs that interoperate directly with Skype for Business Server 2015 see  [Infrastructure Qualified for Microsoft Lync](https://docs.microsoft.com/SkypeForBusiness/lync-cert/qualified-ip-pbx-gateway). If your PBX is not on this list, you can use a Session Border Controller to connect your PBX with Phone System in Office 365 in Skype for Business Online.

### Network considerations for quality and performance

When deploying a cloud-hosted service like Phone System in Office 365 with on-premises PSTN connectivity, you must keep the following in mind. In a purely on-premise Skype for Business Server 2015 Enterprise Voice deployment, all the infrastructure and clients are on the enterprise's own network. The quality and performance of this network, which is critical for high-quality audio and video, are under the direct control of the enterprise staff. With Phone System in Office 365 with on-premises PSTN connectivity, there are three networks involved, two of which the customer is responsible for but only one of which the enterprise staff has direct control over:

- **Microsoft's Global Media Delivery Network** Microsoft's global cloud network and infrastructure. Office 365 and Phone System in Office 365 servers and traffic traverse this network.

- **Enterprise/Cloud PSTN Interconnect** This is the network that connects your enterprise to the Office 365 cloud. This is not necessarily the same as your generic Internet connection.

- **Your enterprise's own network** The quality of the real-time media is heavily dependent on your own network: especially the WiFi network and the quality of the interconnect used to reach the Office 365 cloud.

> [!NOTE]
> For more information on tuning performance in Skype for Business Online, see [Tune Skype for Business Online performance](https://support.office.com/en-us/article/Tune-Skype-for-Business-Online-performance-beec23c2-c5d6-4e84-a8af-e82aefca7802?ui=en-US&amp;rs=en-US&amp;ad=US). 

## Prerequisites for using Phone System in Office 365 with on-premises PSTN connectivity

Before you can configure Phone System in Office 365 with on-premises PSTN connectivity and move users to Skype for Business Online, you must confirm that you have the following prerequisites in place:

 **On-premises server versions.** The versions of the servers in your on-premises deployment must be listed in the following table to support Phone System in Office 365 with on-premises PSTN connectivity.


| **Server role**                                       | **Supported versions\\**\*                                                                                         |
|:------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| Federation Edge\*\*  <br/>                            | Skype for Business Server 2015  <br/>                                                                              |
| Next Hop Federation Route Internal Pool Server  <br/> | Skype for Business Server 2015, March 2016 Cumulative Update 6.0.9319.235 or higher (Front End or Director)  <br/> |
| Front End User Server  <br/>                          | Skype for Business Server 2015  <br/> Lync Server 2013  <br/>                                                      |
| Edge Server  <br/>                                    | Skype for Business Server 2015  <br/>                                                                              |
| Mediation Server  <br/>                               | Skype for Business Server 2015  <br/> Lync Server 2013  <br/>                                                      |

\*Minimum supported versions are:

- Skype for Business Server 2015, March 2016 Cumulative Update 6.0.9319.235

- Lync Server 2013 July 2015 Cumulative Update 5.0.8308.920

\*\*The federation route for all supported SIP domains must route through the Skype for Business Server 2015 Edge Server running the March 2016 or higher Cumulative Update. If the user pool is on Lync Server 2013, that external pool traffic remains on Lync Server 2013 Edge Server. 

In addition you must ensure the following:

- **On-premises Enterprise Voice is configured and tested for on-premises users** This includes PSTN connectivity components. For more information, see the following topics if you are using Skype for Business Server 2015, see [Plan for Enterprise Voice in Skype for Business Server 2015](../../plan-your-deployment/enterprise-voice-solution/enterprise-voice.md) and [Deploy Enterprise Voice in Skype for Business Server 2015](../../deploy/deploy-enterprise-voice/deploy-enterprise-voice.md).

    If you are using Lync Server 2013, see [Planning for Enterprise Voice in Lync Server 2013](https://technet.microsoft.com/library/gg413081%28v=ocs.15%29.aspx) and [Deploying Enterprise Voice in Lync Server 2013](https://technet.microsoft.com/EN-US/library/gg412876%28v=ocs.15%29.aspx).

- **Active Directory synchronization** You must configure Active Directory synchronization using Azure AD Connect. For more information, see [Managing Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-whats-next/).

    > [!NOTE]
    > The version of AAD Connect you use must be version 1.0.9125.0 or later. If you are using an earlier version of AAD Connect tools or DirSync, please upgrade to the supported version. You can upgrade your current installation and maintain any custom rules you have defined in your environment. 

- **Configure your hybrid deployment** Whether all your Skype for Business users are currently homed either online or on-premises, or if you currently have a mix, you must complete the steps to configure a hybrid deployment of Skype for Business Server or Lync Server 2013, as outlined in [Deploy hybrid connectivity between Skype for Business Server and Office 365](../../skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity.md). For more background information on hybrid deployments, see [Plan hybrid connectivity between Skype for Business Server and Office 365](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md?toc=/SkypeForBusiness/sfbhybridtoc/toc.json). 

    If you are using Lync Server 2013, see [Lync Server 2013 hybrid](https://technet.microsoft.com/EN-US/library/jj204805%28v=ocs.15%29.aspx).

- **(Recommended) Active Directory Federation Services (AD FS).** We recommend deploying AD FS to support Single Sign-on. For more information, see [Active Directory Federation Services (AD FS)](https://technet.microsoft.com/en-us/library/cc736690%28v=ws.10%29.aspx).

For information about deploying Phone System in Office 365, see [Enable users for Phone System in Office 365 with on-premises PSTN connectivity in Skype for Business Server](enable-users-for-phone-system.md).


