---
title: Creating a stream in Microsoft Teams
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
description: This article will walk through creating a stream for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Create a live event in Microsoft Teams

> [!IMPORTANT]
> **China**: Currently, users located in China will not be able to set up or attend Microsoft Teams or Yammer live events or view videos on-demand without their IT administrator's help.
>
> Before you start, check with your admin to see whether they need to set up a VPN to connect your corporate network so that these apps can work seamlessly in your organization.

> [!IMPORTANT]
> When setting up a live event, we recommend that you configure your video, community, and user permissions at least 24 hours before the event for the best experience. This includes such settings as adding users, updating video permissions, and changing a community from private to public. It can take up to two (2) hours for certain changes to propagate across Microsoft Stream, Microsoft Teams, and Microsoft Yammer. Allowing 24 hours or more can provide time for testing and making adjustments if needed.

## Schedule the live event

1. In Teams, go to the calendar
2. Use the **New meeting** dropdown.
3. Select the **Live event** option.
4. Enter your event details and save.

## Stream the live event

1. When you save your live event, you'll get the RTMP server ingest URL located in the encoder setup tab. Select an encoder from the drop down list, or choose to configure manually. Check out the list of [encoders](teams-encoder-setup.md) for easy setup instructions.
2. To set up your encoder, select **Start setup** on the producer controls. It may take some time to start the setup process.
3. When the setup is ready, copy the server ingest URL into your encoder to start sending the live encoder feed to Teams. [Using an encoder for live streaming in Microsoft Teams](teams-encoder-setup.md) has more information.

> [!NOTE]
> It's important to set up your encoder with the correct configuration, and specify both audio and video for playback. Check out the [configuration requirements](teams-encoder-configuration.md) to make sure you set up the encoder correctly.

4. When you start pushing from the encoder to the server ingest point, you should see the producer preview update.

> [!NOTE]
> Audience members won't see this until you start the live event, they will see the automatically-generated slate.

5. After you are satisfied with your setup and can see the preview, select **Start event**. If you didn't previously publish your event, Teams will do so automatically when you start the event. After the event starts, audience members can see the event.

> [!NOTE]
> You can also choose to disconnect at this point, which will take you back to step #2 if your intent was to test before the event.

6. When you're finished with your event, select **End event** on the producer controls. This ends the event and makes the content immediately available for video-on-demand.

  > [!IMPORTANT]
  > Make sure to end the event in Teams before stopping your encoder. If you do this in reverse order, audience members will see an error.
