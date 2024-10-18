---
title: Set Audio Conferencing auto attendant languages
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 10/16/2024
ms.topic: article
ms.assetid: 26d73dda-ab26-4af4-8aec-d17f3479ae50
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: "Learn how to select the audio conferencing auto attendant languages for an audio conferencing number in Microsoft Teams."
---

# Set auto attendant languages for Audio Conferencing in Microsoft Teams

The Audio Conferencing auto attendant for Microsoft Teams can greet audio callers in different languages when they join a meeting.
  
As an admin, you can choose one default and up to four alternate languages. The auto attendant uses your chosen default language first, followed by the alternate languages in the order that you picked.
  
> [!NOTE]
> You only have the option to change the languages of Dedicated audio conferencing numbers. You can't change the languages for Shared audio conferencing numbers.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Set the conferencing auto attendant languages

Using the Microsoft Teams admin center:

1. Navigate to **Meetings** > **Conference Bridges**.

2. Select a **Dedicated** audio conferencing phone number from the list, and at the top of the page, select **Edit**. The **Edit** option is only shown when a Dedicated audio conferencing number is selected.

3. In the pane on the right, choose the default language you want and any alternate languages.

    > [!NOTE]
    > The supported default and alternate languages are listed. The order of alternate languages that you choose in the dropdowns is the order of the languages presented to callers.

4. Select **Save**.

## What else should I know?

- To see the list of supported languages for Audio Conferencing, see [Audio Conferencing supported languages](/SkypeForBusiness/audio-conferencing-in-office-365/audio-conferencing-supported-languages).

- Languages can be set for dedicated but not for shared phone numbers.

- To see a list of countries/regions in which Audio Conferencing in Microsoft 365 or Office 365 using Microsoft as the provider is available, see [Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing-in-teams.md).

## Manage auto attendant languages using PowerShell

To manage auto attendant languages with PowerShell, use the PowerShell [CsOnlineDialInConferencingServiceNumber](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings) cmdlet.

For examples, see [CsOnlineDialInConferencingServiceNumber](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings).
  
## Related topics

[Try or purchase Audio Conferencing in Microsoft 365 or Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)
