---
title: "Deployment process for Call Park in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 2000d672-a85f-4262-9d69-0bee9ae3709a
description: "Deployment process and steps for call park in Skype for Business Server Enterprise Voice."
---

# Deployment process for Call Park in Skype for Business
 
Deployment process and steps for call park in Skype for Business Server Enterprise Voice.
  
Call Park enables an Enterprise Voice user to put a call on hold from one telephone and then retrieve the call later by dialing an internal number (known as a Call Park orbit) from any telephone.
  
The components that Call Park uses are automatically installed and enabled on the Front End Server or Standard Edition server when you deploy Enterprise Voice. However, you must use the following steps to configure Call Park before it is available to users. 
  
**Call Park Deployment Process**

|**Phase**|**Steps**|**Required groups and roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure the call park orbit ranges in the orbit table  <br/> |Use Skype for Business Server Control Panel or the **New-CSCallParkOrbit** cmdlet to create the orbit ranges in the call park orbit table and associate them with the Application service that hosts the Call Park application. <br/> **Note:** For seamless integration with existing dial plans, orbit ranges are typically configured as a block of virtual extensions. Assigning Direct Inward Dialing (DID) numbers as orbit numbers in the call park orbit table is not supported. <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Create or modify a Call Park orbit range in Skype for Business](create-or-modify-a-call-park-orbit-range.md) <br/> |
|Configure Call Park settings  <br/> | Use the **Set-CsCpsConfiguration** cmdlet to configure Call Park settings. At a minimum, we recommend that you configure the **OnTimeoutURI** option to configure the fallback destination to use when a parked call times out. You can also configure the following settings: <br/>  (Optional) **EnableMusicOnHold** to enable or disable music on hold. <br/>  (Optional) **MaxCallPickupAttempts** to determine the number of times a parked call rings back to the answering phone before forwarding the call to the fallback Uniform Resource Identifier (URI). <br/>  (Optional) **CallPickupTimeoutThreshold** to determine the amount of time that elapses after a call has been parked before it rings back to the phone where the call was answered. <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Configure Call Park settings in Skype for Business](configure-call-park-settings.md) <br/> |
|Optionally, customize the music on hold  <br/> |Use the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet to customize and upload an audio file, if you don't want to use the default music on hold. <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Customize Call Park music on hold inSkype for Business](customize-call-park-music-on-hold.md) <br/> |
|Configure voice policy to enable Call Park for users  <br/> |Use Skype for Business Server Control Panel or the **Set-CSVoicePolicy** cmdlet with the **EnableCallPark** option to enable Call Park for users in voice policy. <br/> By default, Call Park is disabled for all users.  <br/> If you have multiple voice policies, make sure the EnableCallPark property is set for each voice policy, not just for the default policy.  <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsUserAdministrator  <br/> CsAdministrator  <br/> |[Enable Call Park for users in Skype for Business](enable-call-park-for-users.md) <br/> |
|Verify normalization rules for Call Park  <br/> |Call park orbits must not be normalized. Verify that your normalization rules do not include any of your orbit ranges. If necessary, create additional normalization rules to prevent orbits being normalized.  <br/> |RTCUniversalServerAdmins  <br/> CsVoiceAdministrator  <br/> CsServerAdministrator  <br/> CsAdministrator  <br/> |[Verify normalization rules for Call Park in Skype for Business](verify-normalization-rules-for-call-park.md) <br/> |
|Verify your Call Park deployment  <br/> |Test parking and retrieving calls to make sure that your configuration works as expected.  <br/> |-  <br/> |[(Optional) Verify Call Park deployment in Skype for Business](optional-verify-call-park-deployment.md) <br/> |
   

