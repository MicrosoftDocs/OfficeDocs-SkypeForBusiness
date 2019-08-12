---
title: "Configuring trunks in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "As part of Enterprise Voice deployment, you can configure a trunk between a Mediation Server and one or more peers to provide public switched telephone network (PSTN) connectivity for Enterprise Voice clients and devices in your organization."
---

# Configuring trunks in Skype for Business Server

As part of Enterprise Voice deployment, you can configure a trunk between a Mediation Server and one or more of the following peers to provide public switched telephone network (PSTN) connectivity for Enterprise Voice clients and devices in your organization:

- SIP trunk connection to an Internet telephony service provider (ITSP)
- PSTN gateway
- Private branch exchange (PBX)

For details, see [Plan for PSTN connectivity in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/pstn-connectivity-0.md).

> [!IMPORTANT]
> Before you begin trunk configuration, verify that the topology has been created and that the Mediation Server and its peer have been configured and associated with one another. For details, see [Define a gateway in Topology Builder in Skype for Business Server](../../deploy/deploy-enterprise-voice/define-a-gateway.md).

> [!NOTE]
> As a part of trunk configuration, you can enable the Skype for Business Server media bypass feature, which enables media to bypass the Mediation Server. Trunks can be configured either with or without media bypass enabled, but we strongly recommend that you enable it. For details, see [Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md).
