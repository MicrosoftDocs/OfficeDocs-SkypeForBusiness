---
title: "Configure Call Park settings in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 3bed9d09-8363-4fff-a220-f0f6d3a81241
description: "Modify Call Park settings in Skype for Business Server Enterprise Voice."
---

# Configure Call Park settings in Skype for Business

Modify Call Park settings in Skype for Business Server Enterprise Voice.

If you don't want to use default Call Park settings, you can customize them. When you install the Call Park application, global settings are configured by default. You can modify the global settings, and you can also specify site-specific settings. Use the **New-CsCpsConfiguration** cmdlet to create new site-specific settings. Use the **Set-CsCpsConfiguration** cmdlet to modify existing settings.

> [!NOTE]
> At a minimum, we recommend that you configure the **OnTimeoutURI** option for the fallback destination to use when a parked call times out and ringback fails.

Use **New-CsCpsConfiguration** cmdlet or the **Set-CsCpsConfiguration** cmdlet to configure any of the following settings:


| **This option:**                     | **Specifies this:**                                                                                                                                                                                                                                                                                                                   |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **CallPickupTimeoutThreshold** <br/> | The amount of time that elapses after a call has been parked before it rings back to the phone where the call was answered.  <br/> The value must be entered in the format hh:mm:ss to specify the hours, minutes, and seconds. The minimum value is 10 seconds, and the maximum value is 10 minutes. The default is 00:01:30.  <br/> |
| **EnableMusicOnHold** <br/>          | Whether music plays for a caller while a call is parked.  <br/> Values are True or False. The default is True.  <br/>                                                                                                                                                                                                                 |
| **MaxCallPickupAttempts** <br/>      | The number of times a parked call rings back to the answering phone before it is forwarded to the fallback Uniform Resource Identifier (URI) that is specified for **OnTimeoutURI**. The default is 1.  <br/>                                                                                                                         |
| **OnTimeoutURI** <br/>               | The SIP address of the user or response group to which an unanswered parked call is routed when **MaxCallPickupAttempts** is exceeded. <br/> Value must be a SIP URI beginning with the string sip:. For example, sip:bob@contoso.com. The default is no forwarding address.  <br/>                                                   |

### To configure Call Park settings

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run:

   ```
   New-CsCpsConfiguration -Identity site:<sitename to apply settings> [-CallPickupTimeoutThreshold <hh:mm:ss>] -[EnableMusicOnHold <$true | $false>] [-MaxCallPickupAttempts <number of rings>] [-OnTimeoutURI sip:<sip URI for routing unanswered call>]
   ```

   > [!TIP]
   > Use the **Get-CsSite** cmdlet to identify the site. For details, see Skype for Business Server Management Shell documentation.

    For example:

   ```
   New-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:01:00 -EnableMusicOnHold $false -MaxCallPickupAttempts 2 -OnTimeoutURI sip:bob@contoso.com
   ```

## See also

[Customize Call Park music on hold inSkype for Business 2015](customize-call-park-music-on-hold.md)

[New-CsCpsConfiguration](https://docs.microsoft.com/powershell/module/skype/new-cscpsconfiguration?view=skype-ps)

[Set-CsCpsConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscpsconfiguration?view=skype-ps)

[Get-CsSite](https://docs.microsoft.com/powershell/module/skype/get-cssite?view=skype-ps)
