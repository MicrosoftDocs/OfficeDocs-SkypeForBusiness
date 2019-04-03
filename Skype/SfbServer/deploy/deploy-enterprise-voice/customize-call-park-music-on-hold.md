---
title: "Customize Call Park music on hold inSkype for Business"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 3d78e6f9-a4ae-49f4-a89f-4515acb49dac
description: "Customize the Call Park music on hold in Skype for Business Server Enterprise Voice."
---

# Customize Call Park music on hold inSkype for Business
 
Customize the Call Park music on hold in Skype for Business Server Enterprise Voice.
  
You can specify your own music file to use for music on hold, instead of the default music file that ships with Skype for Business Server. To customize music on hold, use the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet.
  
> [!NOTE]
> If you customize music on hold and want the same music for multiple sites, you must configure the music file for each site that runs the Call Park application. 
  
### To customize the music file

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run:
    
   ```
   Set-CsCallParkServiceMusicOnHoldFile -Service <ServiceID where the Call Park application resides> -Content <Byte >
   ```

    > [!TIP]
    > Use the **Get-CsService** cmdlet to identify the service. For details, see [Get-CsService](https://docs.microsoft.com/powershell/module/skype/get-csservice?view=skype-ps). 
  
    The following example shows how to obtain the contents of a file, soothingmusic.wma, as a byte array and assign it to a variable. Then the audio file is assigned as the music-on-hold file for Call Park. For details, see [Set-CsCallParkServiceMusicOnHoldFile](https://docs.microsoft.com/powershell/module/skype/set-cscallparkservicemusiconholdfile?view=skype-ps).
    
   ```
   $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
   Set-CsCallParkServiceMusicOnHoldFile -Service Redmond1-applicationserver-1 -Content $a
   ```

## See also

[Set-CsCallParkServiceMusicOnHoldFile](https://docs.microsoft.com/powershell/module/skype/set-cscallparkservicemusiconholdfile?view=skype-ps)
  
[Get-CsService](https://docs.microsoft.com/powershell/module/skype/get-csservice?view=skype-ps)
