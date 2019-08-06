---
title: "Configure the Video Interop Server in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 0fde142b-70b1-46c6-b1f9-f9d70115371d
description: "Summary: Configure the Video Interop Server (VIS) role in Skype for Business Server."
---

# Configure the Video Interop Server in Skype for Business Server
 
**Summary:** Configure the Video Interop Server (VIS) role in Skype for Business Server.
  
 Configure the settings that the VIS will associate with video trunks using Windows PowerShell. A video trunk configuration with global scope is created once the VIS service is installed. This video trunk configuration is applied by the VIS to all trunks which do not have video trunk configuration with a more specific scope. Note that the video trunk configuration is a collection of settings that is applicable to video trunks.
  
## Configure video trunk and dial plan

Use the following Windows PowerShell commands to specify the video trunk configuration and dial plan to be associated with the newly defined trunk(s) defined in the Topology Document between the VIS and all Video Gateways. All these settings can be set at the Global, Site, or service (Video Gateway) levels. 
  
A dial plan with global scope is created per Skype for Business Server deployment. This dial plan is applied by VIS to all trunks which do not have any dial plan with more specific scope. 
  
### Configure the VIS using Windows PowerShell

1. Create a new video trunk configuration (a collection of settings) to use on the trunk between the VIS and Cisco Unified Communications Manager (CallManager, or CUCM), using the following Windows PowerShell cmdlet:
    
   ```
   New-CsVideoTrunkConfiguration -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com" -GatewaySendsRtcpForActiveCalls $false -GatewaySendsRtcpForCallsOnHold $false -EnableMediaEncryptionForSipOverTls $true(or $false)
   ```

    If there is an existing video trunk that needs to be modified, use the following Windows PowerShell cmdlet:
    
   ```
   Set-CsVideoTrunkConfiguration -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com" -GatewaySendsRtcpForActiveCalls $false -GatewaySendsRtcpForCallsOnHold $false -EnableMediaEncryptionForSipOverTls  $true(or $false)
   ```

    To view the settings associated with a particular video trunk configuration, use the following Windows PowerShell cmdlet:
    
   ```
   Get-CsVideoTrunkConfiguration -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com"
   ```

    To remove a particular video trunk configuration, use the following Windows PowerShell cmdlet (note that the globally scoped video trunk configuration will be applied if there is not a more specifically scoped video trunk configuration for a particular trunk):
    
   ```
   Remove-CsVideoTrunkConfiguration -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com"
   ```

2. Establish a dial plan to associate with the trunk, using the following Windows PowerShell cmdlets:
    
   ```
   New-CsDialPlan -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com" -SimpleName "TrunkTestDialPlan" 
   New-CsVoiceNormalizationRule -Identity "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com/SevenDigitRule" -Pattern '^(\d{7})$' -Translation '+1425$1' 
   Get-CsDialPlan -Identity "Service:CUCMVIS1.CUCMInterop.contoso.com"
   Remove-CsVoiceNormalizationRule -Identity  "Service:VideoGateway:CUCMVIS1.CUCMInterop.contoso.com/Keep All"
   ```

The **Remove-CsVoiceNormalizationRule** command is needed to override a default rule that will interfere with the expected VIS and CUCM interaction.
> [!NOTE]
> [Remove-CsDialPlan](https://docs.microsoft.com/powershell/module/skype/remove-csdialplan?view=skype-ps) can be used to remove a dial plan.
  
For a video SIP Trunk call from a Video Gateway whose Request URI contains a non-E.164 number, VIS will read the name of the dial plan associated with the associated trunk, and will include the dial plan name in the phone context part of the Request URI in the Invite that VIS sends to the Front End. The Translation Application on the Front End then extracts and applies the normalization rules associated with the dial plan to the Request URI.
## Trunk configuration options

The Windows PowerShell cmdlets for video trunk configuration mentioned previously were new to Skype for Business Server 2015. The settings associated with video trunk configuration require a brief explanation.
  
 **GatewaySendsRtcpForActiveCalls** This parameter determines whether RTCP packets are sent from the VTC to the VIS for active calls. An active call in this context is a call where media is allowed to flow in at least one direction. If GatewaySendsRtcpForActiveCalls is set to True, VIS can terminate a call if it does not receive RTCP packets for a period exceeding 30 seconds. The default is **True**.
  
 **GatewaySendsRtcpForCallsOnHold** This parameter determines whether RTCP packets continue to be sent across the trunk for calls that have been placed on hold and no media packets are expected to flow in either direction. VIS can terminate the call, if there are no RTCP packets flowing from the VTC to VIS while the call is on Hold. The default is **True**. When the SIPTransport protocol is set to TCP, this setting is ignored.
  
 **EnableMediaEncryptionForSipOverTls** This parameter enables or disables SRTP for media when the SIPTransport protocol is set to TLS. The default is **True**. When the SIPTransport protocol is set to TCP, this setting is ignored.
  
 **EnableSessionTimer** This parameter enables or disables session timers on the VIS side for each SIP dialog associated with the video SIP trunk. The default is **False**.
  
 **ForwardErrorCorrectionType** This parameter is used to determine if Forward Error Correction (FEC) for video streams is to be applied on the leg between the Video Interop Server and a Video Gateway. Setting ForwardErrorCorrectionType to "None" turns off FEC between VIS and Video Gateway/VTC. Setting ForwardErrorCorrectionType to "Cisco" enables FEC compatible with Video Gateways by Cisco, such as Cisco Unified Communications Manager (CUCM). The default is **None**.
  
## See also

[Configure CUCM for Interoperation with Skype for Business Server](configure-cucm-for-interoperation.md)
