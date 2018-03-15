---
title: "Configure Call Park settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3bed9d09-8363-4fff-a220-f0f6d3a81241
description: "If you don't want to use default Call Park settings, you can customize them. When you install the Call Park application, global settings are configured by default. You can modify the global settings, and you can also specify site-specific settings. Use the New-CsCpsConfiguration cmdlet to create new site-specific settings. Use the Set-CsCpsConfiguration cmdlet to modify existing settings."
---

# Configure Call Park settings in Lync Server 2013
[]
If you don't want to use default Call Park settings, you can customize them. When you install the Call Park application, global settings are configured by default. You can modify the global settings, and you can also specify site-specific settings. Use the **New-CsCpsConfiguration** cmdlet to create new site-specific settings. Use the **Set-CsCpsConfiguration** cmdlet to modify existing settings. 
  
> [!NOTE]
> At a minimum, we recommend that you configure the **OnTimeoutURI** option for the fallback destination to use when a parked call times out and ringback fails. 
  
Use **New-CsCpsConfiguration** cmdlet or the **Set-CsCpsConfiguration** cmdlet to configure any of the following settings: 
  
|**This option:**|**Specifies this:**|
|:-----|:-----|
|**CallPickupTimeoutThreshold** <br/> |The amount of time that elapses after a call has been parked before it rings back to the phone where the call was answered.  <br/> The value must be entered in the format hh:mm:ss to specify the hours, minutes, and seconds. The minimum value is 10 seconds, and the maximum value is 10 minutes. The default is 00:01:30.  <br/> |
|**EnableMusicOnHold** <br/> |Whether music plays for a caller while a call is parked.  <br/> Values are True or False. The default is True.  <br/> |
|**MaxCallPickupAttempts** <br/> |The number of times a parked call rings back to the answering phone before it is forwarded to the fallback Uniform Resource Identifier (URI) that is specified for **OnTimeoutURI**. The default is 1.  <br/> |
|**OnTimeoutURI** <br/> |The SIP address of the user or response group to which an unanswered parked call is routed when **MaxCallPickupAttempts** is exceeded.  <br/> Value must be a SIP URI beginning with the string sip:. For example, sip:bob@contoso.com. The default is no forwarding address.  <br/> |
   
### To configure Call Park settings

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  New-CsCpsConfiguration -Identity site:<sitename to apply settings> [-CallPickupTimeoutThreshold <hh:mm:ss>] -[EnableMusicOnHold <$true | $false>] [-MaxCallPickupAttempts <number of rings>] [-OnTimeoutURI sip:<sip URI for routing unanswered call>]
  ```

    > [!TIP]
    > Use the **Get-CsSite** cmdlet to identify the site. For details, see Lync Server Management Shell documentation. 
  
    For example:
    
  ```
  New-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:01:00 -EnableMusicOnHold $false -MaxCallPickupAttempts 2 -OnTimeoutURI sip:bob@contoso.com
  ```

## See also

#### 

[Customize Call Park music on hold in Lync Server 2013](customize-call-park-music-on-hold.md)
#### 

[New-CsCpsConfiguration](new-cscpsconfiguration.md)
  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)
  
[Get-CsSite](get-cssite.md)

