---
title: "Configuring voice mail escape in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a1d19e6c-82ff-4768-8ae5-da981368ce40
description: "When a user configures simultaneous ringing to a mobile phone, a caller will typically be routed to the user's personal voice mail if the mobile phone is turned off, out of battery power, or out of range. With Lync Server 2013, users can opt to have business-related calls routed to their corporate voice mail system. Specifically, a timer can be configured, and if the call is answered by the carrier's voice mail within the range of time defined, Lync Server will disconnect from the carrier's voice mail system (and the user's personal voice mail), while the user's remaining endpoints in the corporate system continue to ring. This way, the caller is automatically routed to the user's corporate voice mail."
---

# Configuring voice mail escape in Lync Server 2013
[]
When a user configures simultaneous ringing to a mobile phone, a caller will typically be routed to the user's personal voice mail if the mobile phone is turned off, out of battery power, or out of range. With Lync Server 2013, users can opt to have business-related calls routed to their corporate voice mail system. Specifically, a timer can be configured, and if the call is answered by the carrier's voice mail within the range of time defined, Lync Server will disconnect from the carrier's voice mail system (and the user's personal voice mail), while the user's remaining endpoints in the corporate system continue to ring. This way, the caller is automatically routed to the user's corporate voice mail.
  
This configuration is performed using the Lync Server Management Shell cmdlet, **Set-CsVoicePolicy**, at the voice policy level, with the following parameters. 
  
### To configure voice mail escape

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Specify the following parameters to **Set-CsVoicePolicy**:
    
  - **EnableVoicemailEscapeTimer** - Enables or disables the escape timer. 
    
  - **PSTNVoicemailEscapeTimer** - Specifies the timeout value in milliseconds. The default value is 1500 milliseconds, and the value can range from 0 milliseconds to 8000 milliseconds. 
    
## Example

```
Set-CsVoicePolicy UserVoicePolicy -EnableVoiceMailEscapeTimer $true - PSTNVoicemailEscapeTimer 2000
Set-CsVoicePolicy -Identity site:SitePolicy -EnableVoiceMailEscapeTimer $true -PSTNVoicemailEscapeTimer 1500

```

## See also

#### 

[Configuring voice policies and PSTN usage records to authorize calling features and privileges in Lync Server 2013](configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features.md)

