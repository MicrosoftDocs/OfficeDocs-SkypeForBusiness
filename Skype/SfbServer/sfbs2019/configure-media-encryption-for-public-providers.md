---
title: "Configure media encryption for public providers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/12/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a95814cf-c5a9-4652-8ffc-c469a2653153
description: "If you are implementing audio/video (A/V) federation with Windows Live Messenger, there are two parameters that you need to modify: the Lync Server encryption level and the EnablePublicCloudAccess policy. By default, the encryption level is set to Required. You must change this setting to Supported. If the EnablePublicCloudAccess policy is set to false, this needs to be set to True . You can do this from the Lync Server Management Shell."
---

# Configure media encryption for public providers in Lync Server 2013
[]
If you are implementing audio/video (A/V) federation with Windows Live Messenger, there are two parameters that you need to modify: the Lync Server encryption level and the EnablePublicCloudAccess policy. By default, the encryption level is set to Required. You must change this setting to Supported. If the EnablePublicCloudAccess policy is set to false, this needs to be set to **True**. You can do this from the Lync Server Management Shell. 
  
### Configure Federation for Windows Live

1. Start the Lync Server Management Shell on the Front End server: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. From the command prompt, type the following commands:
    
  ```
  Set-CsMediaConfiguration -EncryptionLevel SupportEncryption
  ```

  ```
  Set-CsExternalAccessPolicy Global -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
  ```

    > [!NOTE]
    > This is required step because Windows Live Messenger does not support encryption of audio/video. The command sets your global policy to a support encryption setting instead of requiring encryption of the audio/video data. Clients that support encryption will still use encryption, such as Lync 2013. 
  

