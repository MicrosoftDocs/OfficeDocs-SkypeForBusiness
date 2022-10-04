---
title: Administration options for streaming in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: asteele
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will discuss administration options for encoder-based RTMP streaming events in Microsoft Teams.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Administration controls for Microsoft Teams live events

As a Teams admin, you can restrict who can create events, see all events, as well as start, stop, modify, or delete an event. By default, everyone in your organization can create a live event.

> [!NOTE]
> **China**: Users located in China will not be able to set up or attend Teams or Yammer live events or view videos on-demand because currently, Azure CDN, which these apps rely on, might not be accessible in China.
>
> As an administrator, you might need to set up a VPN to connect your corporate network for these apps to work seamlessly. Once that's complete, people in your organization can schedule and attend live events.

## Restrict who can create events

This control is only for the creation and production of a live event; everyone who has been granted view permissions to an event will be able to see it, regardless of this setting.

In addition to this setting, a user must also have a valid and enabled license to create live events. See [Live streaming events in Microsoft Teams](teams-encoder-overview.md) for more details.

> [!NOTE]
> You need to be a Teams admin to change this setting.

1. In the Teams admin center, go to XXX.
1. In the XXX page, select Live events.
1. In the Live events page, select **Settings**.
1. Add users or security groups that you want to have permissions to be able to create live events, or leave the toggle set to **Off** to allow everyone in your organization to be able to create live events.
1. Select **Save**.

## Manage a live event

Events shown in the Live now section are in the pre-live or live state and count towards the maximum number of concurrent active events that you can have running in your organization at a given period of time. As the administrator, you can disconnect events (if not started), or stop them to allow for new events to start. For more information, see [Live streaming events in Microsoft Teams](teams-encoder-overview.md).

1. Go to XXX.
1. Select the **Live now** tab or the **Upcoming** tab.
1. To start, stop, modify or delete the event, select the **Edit** icon.
