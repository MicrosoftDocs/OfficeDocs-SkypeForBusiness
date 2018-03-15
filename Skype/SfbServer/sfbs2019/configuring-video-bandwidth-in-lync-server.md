---
title: "Configuring video bandwidth in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 446bed91-b26f-4ab2-b2f5-36e6810b405b
description: "Lync Server 2013 includes several settings for managing video for two-party calls and multiparty conferences. When you deploy Lync Server 2013, you should evaluate whether the default settings are appropriate for your organization, and modify them as necessary."
---

# Configuring video bandwidth in Lync Server 2013
[]
 Lync Server 2013 includes several settings for managing video for two-party calls and multiparty conferences. When you deploy Lync Server 2013, you should evaluate whether the default settings are appropriate for your organization, and modify them as necessary. 
  
The parameters described in this section apply to both two-party calls and multiparty conferencing. View or modify these settings by using one of the following cmdlets: 
  
- **Get-CsConferencingPolicy**
    
- **Set-CsConferencingPolicy**
    
- **New-CsConferencingPolicy**
    
Verify the following settings in your conferencing policy:
  
- **VideoBitRateKb** This setting specifies the maximum video bit rate in kilobits per second (kbps) used for video sent by a user. The default value is 50000 kbps. Valid values are 0 to 50000. 
    
    This setting applies separately to main video and panoramic video. 
    
    Example: if you specify 2000 kbps, then Lync Server can send 2000 kbps for the main video stream and 2000 kbps for the panoramic video stream.
    
    > [!NOTE]
    > The maximum video network bandwidth for a Lync 2013 endpoint is 8000 kbps for the main video and 2500 kbps for panoramic video. These maximum values are reached only if multiple videos are received or sent. For details, see the "Media Traffic Network Usage" section in [Network bandwidth requirements for media traffic in Lync Server 2013](network-bandwidth-requirements-for-media-traffic.md). This section lists the maximum and typical video stream bandwidth for all supported resolutions. 
  
- **TotalReceiveVideoBitRateKb** This setting, which is new in Lync Server 2013, specifies the maximum allowed bitrate (in kilobits per second) for all the video streams received by a client. That is, it specifies the combined total for all the video streams, except for panoramic video streams, that a client can receive. For example, if you specify 1500 kbps, then a client can receive up to 1500 kbps of video, which may consist of multiple video streams or a single video stream. This setting applies only to Lync Server 2013 clients. 
    
    The default value for **TotalReceiveVideoBitRateKb** is 50000 kbps. If the **EnableMultiviewJoin** setting for Gallery View is set to True, **TotalReceiveVideoBitRateKb** must not be set below 420 kbps. If the **EnableMultiviewJoin** setting for Gallery View is set to False, **TotalReceiveVideoBitRateKb** must not be set below 100 kbps. If **EnableMultiviewJoin** is set to True and you set the value below 420 kbps, the values will default to the threshold value. This threshold helps prevent accidental misconfiguration that might result in poor user experience. 
    
    > [!NOTE]
    > For details about the **EnableMultiviewJoin** setting, see [Configuring Gallery View in Lync Server 2013](configuring-gallery-view.md). 
  
- **MaxVideoConferencingResolution** This parameter is no longer used for Lync Server 2013 clients in Lync Server 2013 conferences. Lync Server 2013 conferences use the bit rate controls described earlier in this section. This setting is still used for legacy clients joining a Lync Server 2013 conference. This parameter determines the maximum resolution allowed for legacy clients in conferences organized by users who are homed on Lync Server 2013. That is, legacy clients are treated the same as they were in previous versions of Lync Server or Office Communications Server. 
    
In addition to conferencing policy settings that apply to users, evaluate media configuration settings. View or modify these settings by using one of the following cmdlets:
  
- **Get-CsMediaConfiguration**
    
- **Set- CsMediaConfiguration**
    
- **New- CsMediaConfiguration**
    
Verify the following setting:
  
- **MaxVideoRateAllowed** This per-pool setting specifies the maximum rate at which video signals will be transferred at the client endpoints. It applies only to previous versions of Lync Server clients. 
    
    > [!NOTE]
    > Lync Server 2013 clients ignore this setting and use the TotalReceiveVideoBitRateKb setting in conferencing policy instead. 
  
    The default value is HD720P. Valid values are HD720p15M, VGA600K, and CIF250K.
    
    Example: If you specify 1500 kbps, then all the legacy clients in the pool can receive up to 1500 kbps of video in two-party or multiparty conferences.
    
The following procedures are examples of using Lync Server Management Shell to modify the settings described in this section.
  
### To modify conferencing policy for video settings

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. At the command line, run the following cmdlet to edit conferencing policy:
    
  ```
  Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -VideoBitRateKb 2000 -TotalReceiveVideoBitRateKb 2000 
  ```

### To modify media configuration for legacy clients

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. At the command line, run the following cmdlet to edit the media configuration:
    
  ```
  Set-CsMediaConfiguration -Identity site:Redmond01 -MaxVideoRateAllowed CIF250K
  
  ```


