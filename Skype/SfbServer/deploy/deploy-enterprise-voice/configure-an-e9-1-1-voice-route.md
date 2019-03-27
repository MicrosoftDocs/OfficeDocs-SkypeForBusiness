---
title: "Configure an E9-1-1 voice route in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 6933b840-0e7b-4509-ae43-bc9065677547
description: "Configure E9-1-1 voice routes in Skype for Business Server Enterprise Voice."
---

# Configure an E9-1-1 voice route in Skype for Business Server
 
Configure E9-1-1 voice routes in Skype for Business Server Enterprise Voice. 
  
To deploy E9-1-1, you first need to configure an emergency call voice route. For details about creating voice routes, see [Create or modify a voice route in Skype for Business](create-or-modify-a-voice-route.md). You may define more than one route if, for example, your deployment includes a primary SIP trunk and a secondary SIP trunk. 
  
> [!NOTE]
> To include location information in an E9-1-1 INVITE, you need to configure the SIP trunk that connects to the E9-1-1 service provider to route emergency calls through the gateway. To do this, set the EnablePIDFLOSupport flag on the **Set-CsTrunkConfiguration** cmdlet to True. The default value for EnablePIDFLOSupport is False. For example: `Set-CsTrunkConfiguration Service:PstnGateway:192.168.0.241 -EnablePIDFLOSupport $true.` It is not necessary to enable receiving locations for fallback public switched telephone network (PSTN) gateways and Emergency Location Identification Number (ELIN) gateways.
  
### To configure an E9-1-1 voice route

1. Log on to the computer with an account that is a member of the RTCUniversalServerAdmins groups, or a member of the CsVoiceAdministrator administrative role.
    
2.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run the following cmdlet to create a new PSTN usage record. 
    
    This must be the same name that you will use for the **PSTN** setting in the location policy. Although your deployment will have multiple phone usage records, the following example adds "Emergency Usage" to the current list of available PSTN usages. For details, see [Configure voice policies, PSTN usage records, and voice routes in Skype for Business](voice-and-pstn.md).
    
   ```
   Set-CsPstnUsage -Usage @{add='EmergencyUsage'}
   ```

4. Run the following cmdlet to create a new voice route by using the PSTN usage record that you created in the previous step.
    
    The number pattern must be the same number pattern that is used in the **Emergency Dial String** setting in the location policy. A "+" sign is needed because Skype for Business adds "+" to emergency calls. "Co1-pstngateway-1" is the SIP trunk service ID for the E9-1-1 service provider or for the ELIN gateway service ID. The following example uses "EmergencyRoute" as the name of the voice route.
    
   ```
   New-CsVoiceRoute -Name "EmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="EmergencyUsage"} -PstnGatewayList @{add="co1-pstngateway-1"}
   ```

5. Optionally, for SIP trunk connections, we recommend that you run the following cmdlet to create a local route for calls that are not handled by the E9-1-1 service provider's SIP trunk. This route will be used if the connection to the E9-1-1 service provider is not available. 
    
    The following example assumes that user has "Local" usage in their voice policy.
    
   ```
   New-CsVoiceRoute -Name "LocalEmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="Local"} -PstnGatewayList @{add="co1-pstngateway-2"}
   ```


