---
title: "Integration with Exchange and SharePoint"
ms.reviewer: 
ms.author: v-cichur
author: cichur
manager: serdars
ms.date: 2/13/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
- SPO_Content
ms.custom:
ms.assetid: 5d456d6c-ad71-420c-b6d8-4d9cd0324f86
description: "Summary: Learn about Skype for Business Server 2015 integration with Exchange and SharePoint."
---

# Integration with Exchange and SharePoint

**Summary:** Learn about Skype for Business Server 2015 integration with Exchange and SharePoint.

You can configure Skype for Business Server 2015 deployments for integration with Microsoft Exchange Server 2016, Microsoft Exchange Server 2013, Microsoft Exchange Server 2010, and SharePoint Server, both on-premises and online. The features listed in the following table are supported with all clients unless otherwise specified. For more information about client support, see [Desktop client feature comparison for Skype for Business](../plan-your-deployment/clients-and-devices/desktop-feature-comparison.md) and Skype for Business Online client comparison tables at [Clients for Skype for Business Online](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

[!INCLUDE [sfbo-retirement-skype](../../Hub/includes/sfbo-retirement.md)]

## Integration with Exchange Server

The following tables list the features supported in a hybrid deployment when integrated with Microsoft Exchange Server.

 **Skype for Business Server on premises and Exchange on premises**


| Feature | Notes |
|:-----|:-----|
|IM/Presence in Outlook  |For more information, see [IM and Presence](/previous-versions/office/lync-server-2013/lync-server-2013-im-and-presence).  |
|Schedule and join online meeting through Outlook  |For more information, see [Integrate Skype for Business Server 2015 with Exchange Server](../deploy/integrate-with-exchange-server/integrate-with-exchange-server.md).  |
|IM/Presence in Outlook Web App  |For more information, see [Configure a hybrid environment in Skype for Business Server 2015](../manage/authentication/configure-a-hybrid-environment.md).  |
|Schedule and join online meeting through Outlook Web App  ||
|IM/Presence in Mobile clients  ||
|Join online meetings in Mobile clients  |For more information, see [Deploying Mobility](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-mobility).  |
|Publish status based on Outlook calendar free/busy information  ||
|Contact List (via Unified Contact Store)  |Requires Exchange 2016 or Exchange 2013.  <br/> A Lync 2013 or Skype for Business desktop client is required.  <br/>  For more information, see [Configure Skype for Business Server 2015 to use the unified contact store](../deploy/integrate-with-exchange-server/use-the-unified-contact-store.md).  |
|High-resolution Contact Photo in Lync 2013 client, Skype for Business client, and Lync Web App.  |Requires Exchange 2016 or Exchange 2013.  <br/> For more information, see [Configure the use of high-resolution photos in Skype for Business Server 2015](../deploy/integrate-with-exchange-server/high-resolution-photos.md).  <br/> For photos on the Skype for Business app for MAC and Mobile, integration between Skype for Business Server 2015 and Exchange Server must be set up as described in [Configure partner applications in Skype for Business Server and Exchange Server](../deploy/integrate-with-exchange-server/configure-partner-applications.md). |
|Meeting delegation  |Supported only when both users are homed online in the same forest, or both are homed on-premises. For more information, see [Skype for Business hybrid solutions](/skypeforbusiness/skype-for-business-hybrid-solutions/skype-for-business-hybrid-solutions). |
|Missed Conversations history and Call Logs are written to user's exchange mailbox  ||
|Archiving Content (IM and Meeting) in Exchange  |Requires Exchange 2016 or Exchange 2013.  <br/> For more information, see [Deployment Checklist for Archiving](/previous-versions/office/lync-server-2013/lync-server-2013-deployment-checklist-for-archiving).  |
|Search archived content  |Requires Exchange 2016 or Exchange 2013.  |
|Voice mail  |For more information, see [Deploying On-Premises Exchange UM to Provide Lync Server 2013 Voice Mail](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail).  |

 **Skype for Business Server on premises and Exchange Online**


| Feature | Notes |
|:-----|:-----|
|IM/Presence in Outlook  |For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](../deploy/integrate-with-exchange-server/outlook-web-app.md) |
|Schedule and join online meeting through Outlook  ||
|IM/Presence in Outlook Web App  |For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](../deploy/integrate-with-exchange-server/outlook-web-app.md) |
|Schedule and join online meeting from Outlook Web App  |For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](../deploy/integrate-with-exchange-server/outlook-web-app.md) |
|IM/Presence in Mobile Clients  ||
|Join online meeting in Mobile clients  ||
|Publish status based on Outlook calendar free/busy information  ||
|Contact List (via Unified Contact Store).  |Lync Server 2013 only. A Lync 2013 or Skype for Business desktop client is required.  <br/> For more information, see [Configure Skype for Business Server 2015 to use the unified contact store](../deploy/integrate-with-exchange-server/use-the-unified-contact-store.md) |
|High-resolution Contact Photo in Lync 2013 client, Skype for Business client, and Lync Web App.  |For more information, see [Configure the use of high-resolution photos in Skype for Business Server 2015](../deploy/integrate-with-exchange-server/high-resolution-photos.md).  <br/> For photos on the Skype for Business app for MAC and Mobile, integration between Skype for Business Server 2015 and Exchange Server must be set up as described in [Configure integration between on-premises Skype for Business Server and Outlook Web App](../deploy/integrate-with-exchange-server/outlook-web-app.md). |
|Meeting delegation  |Supported only when both users are homed online in the same forest, or both are homed on-premises. For more information, see [Skype for Business hybrid solutions](/skypeforbusiness/skype-for-business-hybrid-solutions/skype-for-business-hybrid-solutions). |
|Missed Conversations history and Call Logs are written to user's Exchange mailbox  ||
|Archiving Content (IM and Meeting) in Exchange  |For more information, see [Deployment Checklist for Archiving](/previous-versions/office/lync-server-2013/lync-server-2013-deployment-checklist-for-archiving).  |
|Search archived content  |For more information, see at [Configure Exchange for SharePoint eDiscovery Center](/exchange/configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help) |
|Voice mail  |For more information, see [Providing Lync Server 2013 Users Voice Mail on Hosted Exchange UM](/previous-versions/office/lync-server-2013/lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um).  |

 **Skype for Business Online and Exchange on premises**


| Feature | Notes |
|:-----|:-----|
|Presence in Outlook  ||
|Respond via IM, PSTN Call, Skype Call or Video Call from an Outlook email  ||
|Schedule and join online meetings through Outlook  ||
|IM/Presence in Mobile clients  ||
|Join online meetings in Mobile clients  ||
|Publish status based on Outlook calendar free/busy information  ||
|Missed Conversations history and Call Logs are written to user's exchange mailbox  ||
|High-resolution Contact Photo in Lync 2013 or Skype for Business client.  |Requires Exchange 2016 or Exchange 2013. This is not supported in Lync Web App when users are homed on Skype for Business Online.  |
|Meeting delegation  |Supported only when both users are homed online in the same forest, or both are homed on-premises. For more information, see [Skype for Business hybrid solutions](/skypeforbusiness/skype-for-business-hybrid-solutions/skype-for-business-hybrid-solutions). |
|Missed Conversations history and Call Logs are written to user's Exchange mailbox  ||
|Server Side Conversation History  ||

 **Skype for Business Online and Exchange Online**


| Feature | Notes |
|:-----|:-----|
|IM/Presence in Outlook  ||
|Schedule and join online meetings through Outlook  ||
|IM/Presence in Outlook Web App  ||
|Schedule and join online meeting from Outlook Web App  ||
|IM/Presence in Mobile Clients  ||
|Join online meeting in Mobile clients  ||
|Publish status based on Outlook calendar free/busy information  ||
|Missed Conversations history and Call Logs are written to user's exchange mailbox  ||
|Contact List (via Unified Contact Store)  |Lync Server 2013 or Skype for Business client required  |
|High-resolution Contact Photo in Lync 2013, Skype for Business client, and Lync Web App  ||
|Meeting delegation  |Supported only when both users are homed online in the same forest, or both are homed on-premises. For more information, see [Skype for Business hybrid solutions](/skypeforbusiness/skype-for-business-hybrid-solutions/skype-for-business-hybrid-solutions). |
|Archiving Content (IM and Meeting) in Exchange  ||
|Search archived content  ||
|Voicemail  ||

## Integration with SharePoint

The following table lists the features supported in a hybrid deployment when integrated with SharePoint.

|| SharePoint on-premises | SharePoint Online |
|:-----|:-----|:-----|
|**Skype for Business Server 2015 on-premises** | Skills search <br/>  Presence in SharePoint | Presence in SharePoint |
|**Skype for Business Online** | Presence in SharePoint | Presence in SharePoint |