---
title: Use Office 365 and custom connectors in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: lucarras
search.appverid: MET150
description: Connectors keep your team current by delivering content and updates from services you frequently use directly into a channel.
appliesto: 
  - Microsoft Teams
---

Use Office 365 and custom connectors in Microsoft Teams
=======================================================

Connectors keep your team current by delivering frequently used content and service updates directly into a channel. With connectors, your Microsoft Teams users can receive updates from popular services such as Twitter, Trello, Wunderlist, GitHub, and Azure DevOps Services within the chat stream in their team.

Any member of a team can connect their team to popular cloud services with the connectors if the team permissions allow, and all team members are notified of activities from that service. Connectors will continue to function even after the member who has initially setup the connector has left. Any team member with the permissions to add\remove can modify connectors setup by other members.

Office 365 connectors can be used with both Microsoft Teams and Office 365 groups, making it easier for all members stay in sync and receive relevant information quickly. Both Microsoft Teams and Exchange use the same connector model, which allows you to use the same connectors within both platforms. It is worth noting, however, that disabling connectors for the Office 365 Group that a team is dependent upon will disable the ability to create connectors for that team as well.

Add a connector to a channel
----------------------------

Currently, you can add connectors by using Microsoft Teams desktop and web clients. However, information posted by these connectors can be viewed in **all clients** including mobile.

1. To add a connector to a channel, click the **ellipses (…),** on the right of a channel name, then click **Connectors**.

    ![Screenshot of the Teams interface with the Connectors option selected.](media/Use_Office_365_and_custom_connectors_in_Microsoft_Teams_image1.png)

2. You can select from a variety of available connectors, and then click **Add**.

    ![Screenshot of the Connectors dialog showing available the connectors.](media/Use_Office_365_and_custom_connectors_in_Microsoft_Teams_image2.png)

3. Fill in the required information of the selected connector and click **Save**. Each connector requires a diverse set of information to function properly, and some may require you to sign in to the service using the links provided on the connector configuration page.

    ![Screenshot of the configuration page for the RSS connector.](media/Use_Office_365_and_custom_connectors_in_Microsoft_Teams_image3.png)

4. Data provided by the connector is automatically posted to the channel.

    ![Screenshot of the Teams interface showing a conversation in a channel.](media/Use_Office_365_and_custom_connectors_in_Microsoft_Teams_image4.png)

Develop custom connectors
----------------------------

You can also build custom connectors, as well as incoming and outgoing webhooks. See our [developer documentation](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors) for more information.
