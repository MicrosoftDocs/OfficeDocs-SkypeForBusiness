---
title: "Plan location policies for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: da3cca7f-f6e5-4b6f-90a1-2008e3dd1ebd
description: "Read this topic to learn how to plan location policies for an enhanced emergency services (E9-1-1) deployment in Skype for Business Server Enterprise Voice."
---

# Plan location policies for Skype for Business Server
 
Read this topic to learn how to plan location policies for an enhanced emergency services (E9-1-1) deployment in Skype for Business Server Enterprise Voice. 
  
> [!NOTE]
> Skype for Business Server now supports the configuration of multiple emergency numbers for a client. If you want to configure multiple emergency numbers, you must follow the information in [Plan for multiple emergency numbers in Skype for Business Server](multiple-emergency-numbers.md) and [Configure multiple emergency numbers in Skype for Business](../../deploy/deploy-enterprise-voice/configure-multiple-emergency-numbers.md). 
  
You create location policies by using the Skype for Business Control Panel or by using the [New-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/new-cslocationpolicy?view=skype-ps) cmdlet. For more information, see [Create location policies in Skype for Business Server](../../deploy/deploy-enterprise-voice/create-location-policies.md).
  
Each location policy contains the following information:
  
 **Enable Enhanced 9-1-1**
  
When this value is enabled, the client is enabled for enhanced emergency services (E9-1-1). When a client registers, it attempts to acquire a location from the Location Information service and will include the location information as part of an emergency call.
  
 **Location**
  
This setting is used only when **Enable Enhanced 9-1-1** is enabled.
  
You can configure the **Location** setting to define the client behavior as follows:
  
- Setting the value to **No** means that the user will not be prompted for a location.
    
- Setting the value to **Yes** means that the user will be prompted for a location, but can dismiss the prompt.
    
- Setting the value to **Disclaimer** means that the user will be prompted for a location and also will be shown a disclaimer if they try to dismiss the prompt. In all cases, the user can continue to use the client.
    
> [!NOTE]
> The disclaimer text will not appear if a user manually entered a location before being enabled for E9-1-1. Updates to the disclaimer text will not be viewed by users that have already viewed the disclaimer. 
  
 **Enhanced Emergency Service Disclaimer**
  
This setting specifies the disclaimer that users see if they dismiss the prompt for a location. In Skype for Business Server, you can use location policy to set different disclaimers for different locales or different sets of users.
  
 **Emergency Dial String (E9-1-1 dial number)**
  
This dial string (less the leading "+", but including any normalization done by the user's Dial Plan) signifies that a call is an emergency call. The **Emergency Dial String** causes the client to include location and callback information with the call.
  
> [!NOTE]
> If your organization does not use an external line access prefix, you do not need to create a corresponding Dial Plan normalization rule that adds a "+" to the 911 string prior to sending the call to Outbound Routing on a server running Skype for Business Server; the "+" will be automatically prepended by the Skype for Business client as a result of the location policy. However, if your site uses an external access prefix, you need to add a normalization rule to the applicable Dial Plan policy that strips the external access prefix and adds the "+". For example, if your location uses an external access prefix of 9 and a user dials 9 911 to place an emergency call, the client will use its Dial Plan policy to normalize this to +911 before the dialed number is evaluated by the routes in the caller's location profile. 
  
 **Emergency Dial String Masks (E9-1-1 dial mask)**
  
A semicolon-separated list of dial strings that is translated into the specified **Emergency Dial String**. For example, you may want to add 112, which is the emergency service number for most of Europe. A visiting Skype for Business user from Europe may not know that 911 is the U.S. emergency number, but they can dial 112 and get the same result. As with the Emergency Dial String, do not include a "+" before each number, and if you use external line access codes, be sure there are normalization rules in the user's Dial Plan policy to strip off the access code digit.
  
 **PSTN usage**
  
The name of the PSTN Usage that contains the routing paths that determine which SIP trunk, PSTN gateway, or ELIN gateway emergency calls will go to.
  
> [!NOTE]
> Only one usage can be assigned to a location policy. This PSTN Usage overrides the PSTN Usages assigned to the user's voice policy, but applies only to calls placed to the Emergency Dial String or to one of the Emergency Dial String Masks. 
  
 **Notification URI**
  
Specifies one or more SIP URIs of the security personnel who receive an instant messaging (IM) notification when an emergency call is placed. Distribution groups are supported.
  
 **Conference URI**
  
Specifies a direct inward dialing (DID) number (typically, a security desk number) that should be conferenced in when an emergency call is placed. 
  
 **Conference Mode**
  
Specifies if the conference URI will be conferenced into the emergency call by using one-way or two-way communication. 
  
 **Location Refresh Interval**
  
Specifies the amount of time (in hours) between client requests for a location update from the Location Information service. The value can be set to any value between 1 and 12. The default value is 4.
  

