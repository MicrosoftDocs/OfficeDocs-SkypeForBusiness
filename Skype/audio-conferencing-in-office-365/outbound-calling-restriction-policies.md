---
title: "Outbound calling restriction policies for Audio Conferencing and user PSTN calls"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.date: 1/23/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
ms.appliesto: Skype for Business
localization_priority: Normal
ROBOTS: None
f1keywords: None
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing
description: "Administrators can control the type of dial-outs allowed from within a meeting."
---

# Outbound calling restriction policies for Audio Conferencing and user PSTN calls

As an administrator, you can use outbound call controls to restrict the type of audio conferencing and end user PSTN calls that can be made by users in your organization. 

Outbound call controls can be applied on a per-user basis and provide the following two controls to independently restrict each type of outbound calls. By default, both controls are set to allow international and domestic outbound calls. 

|Control|Description|Control options|
|:-----|:-----|:-----|
|Audio Conferencing PSTN calls|Restricts the type of outbound calls that are allo</br>wed from within meetings organized by a user.|International and Domestic (default)</br>Domestic</br>None|
|End user PSTN calls|Restricts the type of calls that can be made by a user.|International and Domestic (default)</br>Domestic</br>None|

   > [!NOTE]
   > A call is determined to be domestic if the called phone number is in the same country as the country that has been set in Office 365 for the organizer of the meeting (in the case of audio conferencing) or the end user (in the case of end user PSTN calls). 


## Restrict audio conferencing outbound calls using the Skype for Business admin center 


1.	Go to the **Office 365 admin center** > **Skype for Business**.
2.	In the Skype for Business admin center, in the left navigation, go to **Audio conferencing** > **Users**, and then select the user from the list of available users.
3.	In the Action pane, click **Edit**.
4.	Under **Restrictions to dial-outs from meetings of this user**, select the dial-out restriction option you want.

    ![The Restrictions to dial-outs options](../images/restrictions-to-dial-outs.png)

5. Click **Save**.

## Restrict audio conferencing and end user outbound calls using PowerShell

Outbound call restrictions are controlled by a single policy called OnlineDialOutPolicy which has a restriction attribute for each. The policy cannot be customized, rather there are pre-defined policy instances for each combination of the settings. 

You can use the Get-CSOnlineDialOutPolicy cmdlet to view the outbound calling policies and assign them to users by using the Grant-CSOnlineDialOutPolicy cmdlet.  

The following table provides an overview of each policy.

|||
|:-----|:-----|
|Identity='tag:DialoutCPCandPSTNInternational'    |    User in the conference can dial out to   international and domestic numbers, and this user can also make outbound calls to international and domestic numbers.    |
|Identity='tag:DialoutCPCDomesticPSTNInternational'  |    User in the conference can only dial out to   domestic numbers, and this user can make outbound calls to international and domestic numbers.    |
|    Identity='tag:DialoutCPCDisabledPSTNInternational'    |    User in the conference cannot make any dial out. This user can make outbound calls to international and domestic numbers.    |
|    Identity='tag:DialoutCPCInternationalPSTNDomestic'    |    User in the conference can dial out to   international and domestic numbers, and this user can only make outbound calls to domestic PSTN number.    |
|    Identity='tag:DialoutCPCInternationalPSTNDisabled'    |    User in the conference can dial out to   international and domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers.    |
|    Identity='tag:DialoutCPCandPSTNDomestic'    |    User in the conference can only dial out to   domestic numbers, and this user can only make outbound call to domestic PSTN numbers.    |
|    Identity='tag:DialoutCPCDomesticPSTNDisabled'    |    User in the conference can only dial out to   domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers.    |
|    Identity='tag:DialoutCPCDisabledPSTNDomestic'    |    User in the conference cannot make any dial   out, and this user can only make outbound call to domestic PSTN numbers.    |
|    Identity='tag:DialoutCPCandPSTNDisabled'    |    User in the conference cannot make any dial   out, and this user cannot make any outbound calls to PSTN number besides emergency numbers.    |
