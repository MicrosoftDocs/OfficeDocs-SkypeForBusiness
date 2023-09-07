---
title: Creating a stream in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: asteele
ms.date: 10/03/2022
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will walk through creating a stream for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Create a live event in Microsoft Teams

> [!IMPORTANT]
> **China**: Currently, users located in China will not be able to set up or attend Microsoft Teams or Viva Engage live events or view videos on-demand without their IT administrator's help.
>
> Before you start, check with your admin to see whether they need to set up a VPN to connect your corporate network so that these apps can work seamlessly in your organization.

> [!IMPORTANT]
> When setting up a live event, we recommend that you configure your video, community, and user permissions at least 24 hours before the event for the best experience. This includes such settings as adding users, updating video permissions, and changing a community from private to public. It can take up to two (2) hours for certain changes to propagate across Microsoft Stream, Microsoft Teams, and Microsoft Viva Engage. Allowing 24 hours or more can provide time for testing and making adjustments if needed.

## Schedule the live event

1. Open Microsoft Teams client and go to the calendar.
1. Use the **New meeting** dropdown.
1. Select the **Live event** option.
1. On the **New live event** pop-up window, enter your event details to the left (**Title**, **Location**, **Start**, **End**, **Time Zone**, and **Details**).
1. On the same page, to the right, **Invite presenters** to add presenters and producers, either individually or via groups.
1. When everything's entered, select **Next**.
1. Select **People and groups**, **Org-wide**, or **Public** under **Live event permissions** to specify who can watch the live event.
1. Select **Teams Encoder (Preview)** under **How will you produce your live event**?
1. Configure required options like **Q&A**, **Captions**, and others under **Event options**.
1. Select **Schedule** to complete the scheduling for your live event.

## Stream the live event

1. Once you schedule your live event, you can retrieve the **RTMP server ingest URL** and **RTMP Key** under the **RTMP In details** section of the calendar invite, which you can use to push the content from Encoder through RTMP Ingest.
1. To set up your encoder, copy the RTMP ingest URL and the RTMP Key into your encoder to start sending the live encoder feed to Team. Using an encoder for live streaming in Microsoft Teams has more information.
1. Using a Microsoft Teams client, join the live event as a Producer. You can also find RTMP In details from more -> Meeting options.
1. When you start pushing content from the encoder to the server ingest point, you should see the producer preview update.
1. After you're satisfied with your setup and can see the preview in the Producer UI, select the **RTMP feed** from sources and **Send Live**.
1. Select **Start event** to start the live event, post which audience members can see the event.
1. When you're finished with your event, select **End event** on the producer UI. This ends the event and makes the content immediately available for video-on-demand.

For more information on streaming the live event, review [Produce a live event using Teams encoder](https://support.microsoft.com/office/produce-a-teams-live-event-using-teams-encoder-b0026c9d-fd37-4bb3-bffc-6961f221fbe9).
