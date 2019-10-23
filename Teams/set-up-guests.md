---
title: Turn on or turn off guest access to Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 03/06/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
ms.reviewer: sbhatta
search.appverid: MET150
description: Turn on or turn off the guest access feature in Microsoft Teams.
ms.custom: 
  - NewAdminCenter_Update
f1keywords: ms.teamsadmincenter.orgwidesettings.guestaccess.turnonguestaccessarticle
appliesto: 
  - Microsoft Teams
---

Turn on or turn off guest access to Microsoft Teams
===================================================

By default, guest access is turned off. As the Office 365 admin, you must turn on guest access for Teams before the admin or team owners can add guests. To turn on guest access, use the [Guest access checklist](guest-access-checklist.md). 

After you turn on guest access, it takes 2-24 hours for the changes to take effect. If a user sees the message "Contact your administrator" when they try to add a guest to their team, it's likely that either guest access hasn't been turned on or the settings aren't effective yet.

> [!IMPORTANT]
> Turning on guest access depends on settings in Azure Active Directory, Office 365, SharePoint Online, and Teams. For more information, see [Authorize guest access in Teams](Teams-dependencies.md).



## Configure guest access in the Teams admin center

1.	Sign in to the Microsoft Teams admin center.

2.	Select **Org-wide settings** > **Guest access**.

3. Set **Allow guest access in Microsoft Teams** to **On**.

    ![Allow guest access switch set to On ](media/set-up-guests-image1.png)

4.	Under **Calling**, **Meeting**, and **Messaging**, select **On** or **Off** for each capability, depending on what you want to allow for guest users.

    - **Make private calls** – Turn this setting **On** to allow guests to make peer-to-peer calls.
    - **Allow IP video** - Turn this setting **On** to allow guests to use video in their calls and meetings.
    - **Screen sharing mode** – This setting controls the availability of screen sharing for guest users. 
       - Turn this setting to **Disabled** to remove the ability for guests to share their screens in Teams. 
       - Turn this setting to **Single application** to allow sharing of individual applications. 
       - Turn this setting to **Entire screen** to allow complete screen sharing.
    - **Allow Meet Now** – Turn this setting **On** to allow guests to use the Meet Now feature in Microsoft Teams.
    - **Edit sent messages** - Turn this setting **On** to allow guests to edit messages they previously sent.
    - **Guests can delete sent messages** – Turn this setting **On** to allow guests to delete messages they previously sent.
    - **Chat** – Turn this setting **On** to give guests the ability to use chat in Teams.
    - **Use Giphys in conversations** – Turn this setting **On** to allow guests to use Giphys in conversations. Giphy is an online database and search engine that allows users to search for and share animated GIF files. Each Giphy is assigned a content rating.
    - **Giphy content rating** –  Select a rating from the drop-down list:
       - **Allow all content** - Guests will be able to insert all Giphys in chats, regardless of the content rating.
       - **Moderate** - Guests will be able to insert Giphys in chats, but will be moderately restricted from adult content.
       - **Strict** – Guests will be able to insert Giphys in chats, but will be restricted from inserting adult content.
    - **Use memes in conversations** - Turn this setting **On** to allow guests to use Memes in conversations.
    - **Use Stickers in conversations** – Turn this setting **On** to allow guests to use stickers in conversations. 


5.	Click **Save**.

## Use PowerShell to turn guest access on or off
Read [Use PowerShell to turn guest access on or off](guest-access-PowerShell.md#use-powershell-to-turn-guest-access-on-or-off)


## Video: Adding guests in Teams

|  |  |
|---------|---------|
| Adding Guests in Microsoft Teams   | <iframe width="350" height="200" src="https://www.youtube.com/embed/1daMBDyBLZc" frameborder="0" allowfullscreen></iframe>   | 


## External access (federation) vs. guest access

[!INCLUDE [guest-vs-external-access](includes/guest-vs-external-access.md)]