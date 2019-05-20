---
title: "Set auto attendant languages for Audio Conferencing in Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 26d73dda-ab26-4af4-8aec-d17f3479ae50
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "See how to select the audio conferencing auto attendant languages for a audio conferencing number in Skype for Business Online."
---

# Set auto attendant languages for Audio Conferencing in Skype for Business Online

> [!Note]
> For information about setting the auto attendant language in Microsoft Teams, see [Set auto attendant languages for Audio Conferencing in Microsoft Teams](/MicrosoftTeams/set-auto-attendant-languages-for-audio-conferencing-in-teams).

The Audio Conferencing auto attendant for Skype for Business can greet audio callers in a number of different languages when they join a meeting.
  
Choose one primary language and up to four secondary languages. The primary language that you set will be used first and the secondary languages will be used by the auto-attendant in order that you select. 
  
> [!NOTE]
>  You can only change the languages of audio conferencing numbers that are of the Dedicated category. The languages of Shared audio conferencing number can't be changed.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](../includes/updating-admin-interfaces.md)]
  
## Set the conferencing auto attendant languages

You must be an [Office 365 global admin](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) or [Skype for Business admin](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) to perform this step.
    
1. In the **Skype for Business admin center**, in the left navigation, go to **Legacy portal**. Once in the legacy portal, select **Audio conferencing**, and then click **Microsoft bridge**.
    
2. Select the audio conferencing phone number from the list, and in the Action pane, click **Set languages**. It is only possible to change the languages of Dedicated audio conferencing numbers.  
    
3. On the **Set languages** page, click the **Primary language** list to view the complete list of available languages. If you need to, click each of the **Secondary languages** lists to select secondary language.
    
    > [!NOTE]
    > The primary and secondary languages that are supported are listed. The order in which you select them in the lists will be the order of the languages presented to callers. 
  
4. Click **Save**.
    
## Want else should I know?

- To see the list of supported languages for Audio Conferencing, see [Audio Conferencing supported languages](/MicrosoftTeams/audio-conferencing-supported-languages).
    
- Languages can be set for dedicated but not for shared phone numbers.
    
- To see a list of countries/regions in which Audio Conferencing in Office 365 using Microsoft as the provider is available, see [Phone numbers for Audio Conferencing](phone-numbers-for-audio-conferencing.md).
    
## Want to use Windows PowerShell?

To automate this step, you can use the [Set-CsOnlineDialInConferencingServiceNumber ](https://go.microsoft.com/fwlink/?LinkId=617689) and [Get-CsOnlineDialInConferencingLanguagesSupported ](https://go.microsoft.com/fwlink/?LinkId=617684) cmdlets.
  
To learn more, see [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
  
## Related topics

[Try or purchase Audio Conferencing in Office 365](../audio-conferencing-in-office-365/try-or-purchase-audio-conferencing-in-office-365.md)
