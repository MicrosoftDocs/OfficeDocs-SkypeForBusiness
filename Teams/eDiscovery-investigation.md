---
title: Conduct an eDiscovery investigation of content in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/12/2018
ms.topic: article
ms.service: msteams
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: anach
search.appverid: MET150
description: Learn what to do when you need to preform an eDiscovery such as when you need to submit all Electronically Stored Information for legal proceedings.
appliesto: 
- Microsoft Teams
---

Conduct an eDiscovery investigation of content in Microsoft Teams
============================

Large Enterprises are often exposed to high penalty legal proceedings that demand submission of all Electronically Stored Information (ESI).

All Teams 1:1 or group chats are journaled through to the respective users’ mailboxes, and all channel messages are journaled through to the group mailbox representing the team. Files uploaded are covered under the eDiscovery functionality for SharePoint Online and OneDrive for Business.

1.  To conduct an eDiscovery investigation with Microsoft Teams content, review step 1 in [this](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) link.

2.  Microsoft Teams data will appear as IM or Conversations in the Excel eDiscovery export output, and you can mount the .PST in Outlook to view those messages post export.

    When mounting the .PST for the Team, note that all conversations are kept in the Team Chat folder under Conversation History. The title of the message aligns to Team and Channel. From reviewing the image below, you can see this message from Bob who messaged the Project 7 channel of the Manufacturing Specs team.

    ![Screenshot of a Team Chat folder in a user's mailbox in Outlook](media/Conduct_an_eDiscovery_investigation_of_content_in_Microsoft_Teams_image1.png)

3.  To see private chats in a user’s Mailbox, they are also located inside the Team Chat folder under Conversation History.

## eDiscovery of guest-to-guest chats

Without a mailbox, guest-to-guest chats (1xN chats in which there are no home tenant users) would not be indexed, and as a result, would not be included in eDiscovery. To facilitate eDiscovery for guest-to-guest chats, a cloud-based mailbox (or phantom mailbox) is created to store the 1xN data. After the Teams chat data is stored in the cloud-based mailbox, it is indexed for eDiscovery and compliance content search.

The following illustration shows how eDiscovery works for guest-to-guest chats in which there isn’t a mailbox.

![guest-to-guest-chats-with-no-mailbox](media/conduct-an-ediscovery-investigation-of-content-in-microsoft-teams-image2.png)
