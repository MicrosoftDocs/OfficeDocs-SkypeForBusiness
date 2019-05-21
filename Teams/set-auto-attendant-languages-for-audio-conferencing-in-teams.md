---
title: "Set auto attendant languages for Audio Conferencing in Microsoft Teams"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 26d73dda-ab26-4af4-8aec-d17f3479ae50
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "See how to select the audio conferencing auto attendant languages for a audio conferencing number in Microsoft Teams."
---

# Set auto attendant languages for Audio Conferencing in Microsoft Teams

The Audio Conferencing auto attendant for Microsoft Teams can greet audio callers in a number of different languages when they join a meeting.
  
Choose one primary language and up to four secondary languages. The primary language that you set will be used first and the secondary languages will be used by the auto-attendant in order that you select. 
  
> [!NOTE]
>  You can only change the languages of audio conferencing numbers that are of the Dedicated category. The languages of Shared audio conferencing number can't be changed.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Set the conferencing auto attendant languages

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. Select a **Dedicated** audio conferencing phone number from the list, and at the top of the page, click **Edit**. It is only possible to change the languages of Dedicated audio conferencing numbers. The **Edit** option is only shown when a Dedicated audio conferencing number is selected.

3. In the pane on the right, choose the default language you want and any alternate languages. 
 
    > [!NOTE]
    > The default and alternate languages that are supported are listed. The order in which you select them in the lists will be the order of the languages presented to callers. 

4. Click **Save**.

    
## Want else should I know?

- To see the list of supported languages for Audio Conferencing, see [Audio Conferencing supported languages](https://docs.microsoft.com/SkypeForBusiness/audio-conferencing-in-office-365/audio-conferencing-supported-languages).
    
- Languages can be set for dedicated but not for shared phone numbers.
    
- To see a list of countries/regions in which Audio Conferencing in Office 365 using Microsoft as the provider is available, see [Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing-in-teams.md).
    
## Want to use Windows PowerShell?

See the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
  
## Related topics

[Try or purchase Audio Conferencing in Office 365](/SkypeForBusiness/audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365)

