---
title: "Assign policies in Lync Server 2013 to a common area phone"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f0554fd1-b237-49b3-9eb4-26f4b91f5604
description: "After you create your policy for common area phones (for details, see Create a voice policy and configure PSTN usage records in Lync Server 2013), you can assign the policy to a common area phone by using Windows PowerShell and the appropriate Grant-Cs cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog articleQuick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShellat https://go.microsoft.com/fwlink/p/?linkId=255876."
---

# Assign policies in Lync Server 2013 to a common area phone
[]
After you create your policy for common area phones (for details, see [Create a voice policy and configure PSTN usage records in Lync Server 2013](create-a-voice-policy-and-configure-pstn-usage-records.md)), you can assign the policy to a common area phone by using Windows PowerShell and the appropriate **Grant-Cs** cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
## 

### Assigning a Policy to a Single Common Area Phone

- The following command assigns the per-user voice policy RedmondVoice to the common area phone that has the Identity Building 14 Lobby.
    
  ```
  Grant-CsVoicePolicy -Identity "Building 14 Lobby" -PolicyName "RedmondVoicePolicy"
  ```

### Assigning a Policy to Multiple Common Area Phones

- In this example, the per-user voice policy RedmondVoice is assigned to all the common area phones configured for use in the organization.
    
  ```
  Get-CsCommonAreaPhone | Grant-CsVoicePolicy  -PolicyName "RedmondVoicePolicy"
  ```

For details, see the Help topics for the [Grant-CsVoicePolicy](grant-csvoicepolicy.md).
  
## See also

#### 

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)

