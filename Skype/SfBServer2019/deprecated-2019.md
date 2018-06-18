---
title: "Skype for Business Server 2019 deprecations"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 6/31/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: These features have been removed from Skype for Business Server 2019."
---

# Skype for Business Server 2019 deprecations

<!-- In addition to deprecations, this document reflects notes on what topic areas can and can't be evergreened to generically apply to 2019 and 2015 alike. It's not a doc plan in that it provides no schedule, but it is a general plan of attack to deal with legacy topics requiring minimal investment for 2019's release. -->

[!INCLUDE [disclaimer](disclaimer.md)]

The following features are found in Skype for Business Server 2015 but are no longer present in Skype for Business Server 2019: 

- Persistent chat (136 topics impacted, leave unevergreened deliberately? create new stub topic in 2019 toc explaining deprecation?)
    - [Plan for Persistent Chat Server in Skype for Business Server 2015](../SfbServer/plan-your-deployment/persistent-chat-server/persistent-chat-server.md)
    - [Deploy Persistent Chat Server in Skype for Business Server 2015](../SfbServer/deploy/deploy-persistent-chat-server/deploy-persistent-chat-server.md)
    - [Manage Persistent Chat Server in Skype for Business Server 2015](../SfbServer/manage/persistent-chat/persistent-chat.md)

There is no migration topic for Pchat, but there is one for XMPP. Reconcile w/ Ken.  

- SQL Mirroring (most HADR topics impacted, 49 topics)
    - [Deploy SQL mirroring for Back End Server high availability in Skype for Business Server](../SfbServer/deploy/deploy-high-availability-and-disaster-recovery/sql-mirroring-for-high-availability.md)\
    Can't omit entirely, as other methods are still supported. Likely candidates for alerts.
- XMPP Gateway (7 Edge topics impacted, so collaborate w/Heidi)   
    - Migration [Configure XMPP gateway access policies and certificates](migration/configure-xmpp-gateway-access-policies-and-certificates.md) \
     (what happened? check w/ Ken)
    - [Configure XMPP gateway access policies and certificates](migration/configure-xmpp-gateway-access-policies-and-certificates.md)
    - [XMPP Federated Partners](../SfbServer/help-topics/help-lscp/xmpp-federated-partners.md)
- In-place upgrades from previous versions (Ken working on installation and migration topics, need to sync)
    - [Plan to upgrade to Skype for Business Server 2015](../SfbServer/plan-your-deployment/upgrade.md)
- Support for TLS 1.0 and 1.1 (1 topic, see Heidi)
    -  [Encryption for Skype for Business Server 2015](../SfbServer/plan-your-deployment/security/encryption.md)


<!-- 
The file counts reflect file hits in searches, and in some cases refer to un-migrated 2013 topics we can link to once they are migrated. 

The following deprecation notes may be necessary. Or not. If 2019 has a seperate toc but single sources files from 2015 folders we can simply omit entire files and nodes from the 2019 toc and reffrain from evergreening them, so they self-identify as 2015 topics.

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019.

> [!NOTE]
> XMPP Gateways are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019.

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The Clustering and AlwaysOn methods are preferred with Skype for Business Server 2019.

> [!NOTE]
> In-place upgrades from previous versions are available in Skype for Business Server 2015 but are not available  in Skype for Business Server 2019. See *Migration link*

Add following to encryption.md:
> [!SECURITY NOTE]
> To ensure the strongest cryptographic protocol is used, Skype for Business Server 2019 will offer TLS encryption protocols in the following order to clients: **TLS 2.0, TLS 1.2**. TLS is a critical aspect of Skype for Business Server 2019 and thus it is required in order to maintain a supported environment. 
-->

### Online Help

Will the 2019 help for topology builder, control panel, planning tool, and other tools get evergreened too?


## Evergreen

Documentation for the following features (including all relevant plan/deploy/manage nodes) applies equally to Skype for Business Server 2015 and 2019:
- Requirements (Server, env, network)
- Monitoring (plan, deploy, manage)  &#x2714;
- Archiving (plan, deploy, manage)  &#x2714;
- Capacity planning
- Clients (plan, deploy, manage)
- Conferencing (plan, deploy, manage)
- Edge (unclear, verify w/ Heidi)
- Enterprise Voice (plan, deploy, manage)
- Exchange integration (plan, deploy, manage)
- HADR
- Modern Auth
- Security (plan, deploy, manage)
- IM and Presence (plan, deploy, manage)
- Mobility (plan, deploy, manage)
- VIS role (plan, deploy, manage)
- Topology management
- User account management

We can also evergreen: 
- Schema references
- Technical diagrams

## New items
New items we may need by RTM include: 
- What's new in 2019
- Deprecated (this document, after we massage out my chatter)
