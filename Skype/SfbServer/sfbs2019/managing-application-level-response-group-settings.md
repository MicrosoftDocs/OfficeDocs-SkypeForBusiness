---
title: "Managing application-level Response Group settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aab749a1-fa2d-4ce8-a6c6-ebcfa37ce02a
description: "Application-level settings for Response Group application include the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration. You can define only one set of application-level settings per pool. To view application-level settings, use the Get-CsRgsConfiguration cmdlet. To modify the application-level settings, use the Set-CsRgsConfiguration cmdlet."
---

# Managing application-level Response Group settings in Lync Server 2013
[]
Application-level settings for Response Group application include the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration. You can define only one set of application-level settings per pool. To view application-level settings, use the **Get-CsRgsConfiguration** cmdlet. To modify the application-level settings, use the **Set-CsRgsConfiguration** cmdlet. 
  
The default music on hold is played when a call is placed on hold only if no custom music on hold is defined. Call context is available only for queues assigned to interactive workflows. If call context is enabled, an agent can see information such as caller wait time or workflow questions and answers when the call is received.
  
### To modify Response Group application-level settings

1. Log on as a member of the RTCUniversalServerAdmins group, or as a member of one of the predefined administrative roles that support Response Group.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. At the command line, run:
    
  ```
  Set-CsRgsConfiguration -Identity <name of service hosting Response Group> [-AgentRingbackGracePeriod <# seconds until call returns to agent after declined>] [-DefaultMusicOnHoldFile <audio file>] [-DisableCallContext <$true | $false>]
  ```

    For example:
    
  ```
  Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -AgentRingbackGracePeriod 30 -DisableCallContext $false
  ```

    To specify an audio file to use as the default music on hold, you need to import the audio file first. For example:
    
  ```
  $x = Import-CsRgsAudioFile -Identity "service:ApplicationServer:redmond.contoso.com" -FileName "MusicWhileYouWait.wav" -Content (Get-Content C:\Media\ MusicWhileYouWait.wav -Encoding byte -ReadCount 0)
  Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -DefaultMusicOnHoldFile <$x>
  ```

## See also

#### 

[Get-CsRgsConfiguration](get-csrgsconfiguration.md)
  
[Set-CsRgsConfiguration](set-csrgsconfiguration.md)
  
[Import-CsRgsAudioFile](import-csrgsaudiofile.md)

