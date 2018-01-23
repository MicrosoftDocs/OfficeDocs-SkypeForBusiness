---
title: "Outbound calling restriction policies for Audio Conferencing and Calling Plans"
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

# Outbound calling restriction policies for Audio Conferencing and Calling Plans

As an administrator, you can control the type of dial-outs you will allow from within a meeting, including restrictions on dial-outs at an organizer level. You can choose to allow domestic and international dial-outs, or only domestic dial-outs. You can also prevent dial-outs entirely.

## Restrict outbound calling for a user

1.	Go to the **Office 365 admin center** > **Skype for Business**.
2.	In the Skype for Business admin center, in the left navigation, go to **Audio conferencing** > **Users**, and then select the user from the list of available users.
3.	In the Action pane, click **Edit**.
4.	Under **Restrictions to dial-outs from meetings of this user**, select the dial-out restriction option you want.

    ![The Restrictions to dial-outs options](../images/restrictions-to-dial-outs.png)

5. Click **Save**.

## Use Windows PowerShell to set outbound calling restriction policies

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
