---
title: "Create location policies in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f1878194-c756-4794-8fa1-15dd2118b4b3
description: "Lync Server uses a location policy to enable Lync clients for E9-1-1 during client registration. A location policy contains the settings that define how E9-1-1 will be implemented."
---

# Create location policies in Lync Server 2013
[]
Lync Server uses a location policy to enable Lync clients for E9-1-1 during client registration. A location policy contains the settings that define how E9-1-1 will be implemented.
  
You can edit the global location policy and create new tagged location policies. A client obtains a global policy when it is not located within a subnet with an associated location policy, or when the client has not been directly assigned a location policy. Tagged policies are assigned to subnets or users. 
  
To create a location policy, you must use an account that is a member of the RTCUniversalServerAdmins group, or is a member of the CsVoiceAdministrator administrative role, or has equivalent administrator rights and permissions.
  
For a complete description of Location policies, see [Defining the location policy for Lync Server 2013](defining-the-location-policy.md). Cmdlets in this procedure use a location policy defined using the following values:
  
|**Element**|**Value**|
|:-----|:-----|
|EnhancedEmergencyServicesEnabled  <br/> |**True** <br/> |
|LocationRequired  <br/> |**Disclaimer** <br/> |
|EnhancedEmergencyServiceDisclaimer  <br/> |Your company policy requires you to set a location. If you do not set a location, emergency services will not be able to locate you in an emergency. Please set a location.  <br/> |
|UseLocationForE911Only  <br/> |**False** <br/> |
|PstnUsage  <br/> |**EmergencyUsage** <br/> |
|EmergencyDialString  <br/> |**911** <br/> |
|EmergencyDialMask  <br/> |**112** <br/> |
|NotificationUri  <br/> |**sip:security@litwareinc.com** <br/> |
|ConferenceUri  <br/> |**sip:+14255550123@litwareinc.com** <br/> |
|ConferenceMode  <br/> |**twoway** <br/> |
|LocationRefreshInterval  <br/> |**2** <br/> |
   
For details about working with location policies, see the Lync Server Management Shell documentation for the following cmdlets:
  
- New-CsLocationPolicy
    
- Get-CsLocationPolicy
    
- Set-CsLocationPolicy
    
- Remove-CsLocationPolicy
    
- Grant-CsLocationPolicy
    
### To create location policies

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
    > [!NOTE]
    > CsLocationPolicy will fail if the setting for **PstnUsage** is not already in the Global list of PstnUsages. 
  
2. Optionally, run the following cmdlet to edit the global Location Policy:
    
  ```
  Set-CsLocationPolicy -Identity Global -EnhancedEmergencyServicesEnabled $true -LocationRequired "disclaimer" -EnhancedEmergencyServiceDisclaimer "Your company policy requires you to set a location. If you do not set a location emergency services will not be able to locate you in an emergency. Please set a location." -PstnUsage "emergencyUsage" -EmergencyDialString "911" -ConferenceMode "twoway" -ConferenceUri "sip:+14255550123@litwareinc.com" -EmergencyDialMask "112" NotificationUri "sip:security@litwareinc.com" -UseLocationForE911Only $true -LocationRefreshInterval 2
  
  ```

3. Run the following to create a tagged Location Policy.
    
  ```
  New-CsLocationPolicy -Identity Tag:Redmond - EnhancedEmergencyServicesEnabled $true -LocationRequired "disclaimer" -EnhancedEmergencyServiceDisclaimer "Your company policy requires you to set a location. If you do not set a location emergency services will not be able to locate you in an emergency. Please set a location." -UseLocationForE911Only $false -PstnUsage "EmergencyUsage" -EmergencyDialString "911" -EmergencyDialMask "112" -NotificationUri "sip:security@litwareinc.com" -ConferenceUri "sip:+14255550123@litwareinc.com" -ConferenceMode "twoway" -LocationRefreshInterval 2
  
  ```

4. Run the following cmdlet to apply the tagged Location Policy created in step 3 to a user policy.
    
  ```
  (Get-CsUser | where { $_.Name -match "UserName" }) | Grant-CsLocationPolicy -PolicyName Redmond
  ```


