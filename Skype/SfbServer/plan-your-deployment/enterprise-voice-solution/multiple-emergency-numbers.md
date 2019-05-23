---
title: "Plan for multiple emergency numbers in Skype for Business Server"
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
ms.assetid: 5ed45a22-ddf0-419f-84da-895a73df855f
description: "Read this topic to learn how to plan for multiple emergency numbers in Skype for Business Server."
---

# Plan for multiple emergency numbers in Skype for Business Server
 
Read this topic to learn how to plan for multiple emergency numbers in Skype for Business Server.
  
Skype for Business Server now supports the configuration of multiple emergency numbers for a client. Multiple emergency numbers is a new feature introduced in the June 2016 Cumulative Update. While the United States has a single emergency number, 911, many countries support multiple emergency numbers. The United Kingdom, for example, supports both 999, the emergency number specific to the United Kingdom, and 112, the emergency number for the European Union. 
  
This feature is also useful for health care providers within the United States who want to have roaming support for multiple code blue emergency numbers.
  
## Multiple emergency numbers and location policies

You configure emergency calling by creating location policies that define how emergency calling will be implemented. You use the location policy to define what number constitutes an emergency call—for example, 911 in the United States; 999 and 112 in the United Kingdom. The location policy determines whether a user is enabled for emergency calling, and if so what the behavior is of an emergency call. You can also define whether corporate security should be automatically notified, and how the call should be routed.
  
For more information about defining and modifying a location policy, see [Plan location policies for Skype for Business Server](location-policies.md) and [Create location policies in Skype for Business Server](../../deploy/deploy-enterprise-voice/create-location-policies.md). These topics describe concepts about location policies; however, you must follow the instructions in [Configure multiple emergency numbers in Skype for Business](../../deploy/deploy-enterprise-voice/configure-multiple-emergency-numbers.md) to configure multiple emergency numbers.
  
When planning for multiple emergency numbers, keep the following in mind:
  
- With the June 2016 Cumulative Update, you can define up to 5 emergency numbers for a given location policy. With the November 2016 Cumulative Update, this number increases to 100.
    
    > [!NOTE]
    > If you have not yet upgraded to the November 2016 Cumulative Update, see [Updates to Skype for Business Server 2015](https://support.microsoft.com/en-us/help/3061064/updates-for-skype-for-business-server-2015). 
  
- For each emergency number, you can specify zero or more emergency dial masks, which are unique to a given location policy.
    
    A dial mask is a number that you want to translate into the value of the emergency dial number value when it is dialed. For example, assume you enter a value of 212 in this field and the emergency dial number field has a value of 911. When a user dials 212, the number will be translated to 911. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services (for example, if someone from a country or region with a different emergency number attempts to dial that country or region's number rather than the number for the country or region they are currently in). You can define multiple emergency dial masks by separating the values with semicolons. For example, 212;414. The string limit for a dial mask is 100 characters. Each character must be a digit 0 through 9.
    
- Each location policy has a single public switched telephone network (PSTN) usage that is used to determine which voice route is used to route emergency calls from clients using this policy. The usage can have a unique route per emergency number.
    
- If a location policy has both the EmergencyNumbers and DialString parameters defined, and the client supports multiple emergency numbers, then the emergency number takes precedence. If the client does not support multiple emergency numbers, then the emergency dial string is used.
    
- For information about which Skype for Business and Lync clients support receiving multiple emergency numbers, dial masks, and public switched telephone network (PSTN) usages, see [Client support](multiple-emergency-numbers.md#BKMK_Clients).
    
> [!NOTE]
> You cannot configure multiple emergency numbers by using the Skype for Business Control Panel. You must use PowerShell to configure multiple emergency numbers. 
  
Before you configure multiple emergency numbers, keep the following in mind:
  
- To configure multiple emergency numbers, you must use the New-CsEmergencyNumber cmdlet, and you must define location policies that support more than one emergency number by specifying the EmergencyNumbers parameter with the [New-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/new-cslocationpolicy?view=skype-ps) and [Set-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/set-cslocationpolicy?view=skype-ps) cmdlets.
    
- If you have existing numbers defined using the Set-CsLocationPolicy or New-CsLocationPolicy cmdlet with the EmergencyDialString and EmergencyDialMask parameters, the values specified with the EmergencyNumbers parameter will take precedence over the old values. That is, the values for the EmergencyDialString and EmergencyDialMask parameters will be ignored.
    
- If you have existing numbers defined using the Set-CsLocationPolicy or New-CsLocationPolicy cmdlet with the EmergencyDialString and EmergencyDialMask parameters,  *and you do not configure new emergency numbers*  , the existing numbers will continue to be used.
    
- For the multiple emergency numbers feature to work, the client versions you are running must be able to support the new feature. Older clients will continue to use the old values specified by the Set-CsLocationPolicy or New-CsLocationPolicy cmdlets with the EmergencyDialString and EmergencyDialMask parameters. 
    
- If the users will be dialing a number that matches the dial string, then no dial mask is required. For example, if the number a user dials is 911, then the dial string is 911 and no mask is required. 
    
For more information about configuring multiple emergency numbers, see [Configure multiple emergency numbers in Skype for Business](../../deploy/deploy-enterprise-voice/configure-multiple-emergency-numbers.md).
  
The following table shows example location policies (for purposes of the example, not all attributes are shown):
  

|**Location policy name**|**E911 enabled**|**Emergency dial string**|**Dial mask**|**Emergency numbers**|**PSTN usage**|**Location required**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|United States  <br/> |Yes  <br/> |911  <br/> | 112;999 <br/> ||USEmergency  <br/> |Yes  <br/> |
|US-Hospital  <br/> |Yes  <br/> |911  <br/> |450  <br/> |911  <br/> 450  <br/> |SeattleEmergency  <br/> |Yes  <br/> |
|London  <br/> |Yes  <br/> |999  <br/> |144  <br/> |999-144  <br/> 112-911;117;118  <br/> |GBEmergency  <br/> |No  <br/> |
|India  <br/> |Yes  <br/> |||100-911  <br/> 101  <br/> 102  <br/> |IndiaEmergency  <br/> |No  <br/> |
   
 **United States** —There is no requirement for multiple emergency numbers. In the United States, you use the old Emergency Dial String and Dial Mask configurations.
  
 **US-Hospital** —There is a requirement not to mask "450". For clients that do not yet support multiple emergency numbers, you can use the old Emergency Dial String and Dial Mask configurations. For clients that support multiple emergency numbers, you can define an emergency number for both "911" and "450" instead of masking 450.
  
 **London** —For clients that do not yet support multiple emergency numbers, you can use the old Emergency Dial String and Dial Mask configurations. For clients that support multiple emergency numbers, you can define an emergency number for both "999" and "112" with masks for each.
  
 **India** —All deployed clients support multiple emergency numbers. In India, you only need to configure multiple emergency numbers.
  
## Client support
<a name="BKMK_Clients"> </a>

The following table shows client support for multiple emergency numbers. Microsoft will continue to test and release support for additional clients. Please check back often.

|**Windows**|**Version**|
|:-----|:-----|
|**Click-to-Run** <br/> |CC (Current Channel) released on May 10, 2016 - Version 1604 (Build 6868.2062)  <br/> |
||FRDC (First Release Current Channel) released on June 14, 2016 - Version 1605 (Build 6965.2058)  <br/> |
||DC (Deferred Channel) released on October 11, 2016 - Version 1605 (Build 6965.2092)  <br/> |
|**MSI** <br/> |June 7 update - [https://support.microsoft.com/en-us/kb/3115087](https://support.microsoft.com/en-us/kb/3115087) <br/> |
|**Mac and iOS** <br/> |**Version** <br/> |
||Skype for Business Mac client version 16.9  <br/> Skype for Business iOS client version 6.16  <br/> |
|**Android** <br/> |**Version** <br/> |
||Skype for Business Android client version 6.17  <br/> |
|**Lync Phone Edition** <br/> |**Version** <br/> |
|| Aastra 6721ip and Aastra 6725ip telephones - September 2016 cumulative update (Build 7577.4512) -[https://support.microsoft.com/en-us/kb/3194831](https://support.microsoft.com/en-us/kb/3194831) <br/> |
|| HP 4110 and HP 4120 telephones - September 2016 cumulative update (Build 7577.4512) -[https://support.microsoft.com/en-us/kb/3194832](https://support.microsoft.com/en-us/kb/3194832) <br/> |
||Polycom CX500, Polycom CX600, and Polycom CX3000 telephones - September 2016 cumulative update (Build 7577.4512) - [https://support.microsoft.com/en-us/kb/3194833](https://support.microsoft.com/en-us/kb/3194833) <br/> |
   

