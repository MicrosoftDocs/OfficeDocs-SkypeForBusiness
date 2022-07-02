---
title: Outbound call restrictions - Audio Conferencing & PSTN calls
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
  - CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: "Administrators can control the type of audio conferencing and end-user PSTN calls that can be made by users."
---

# Outbound calling restriction policies for Audio Conferencing and user PSTN calls

As an administrator, you can use outbound call controls to restrict the type of audio conferencing and end-user Public Switched Telephone Network (PSTN) calls that can be made by users in your organization.

Outbound call controls can be applied on a per-user basis or on a tenant basis and provide the following two controls to independently restrict each type of outbound calls. By default, both controls are set to allow international and domestic outbound calls.

|Control|Description|Control options|
|:-----|:-----|:-----|
|Audio Conferencing PSTN calls|Restricts the type of outbound </br>calls that are allowed from within </br>meetings organized by a user.|Any destination (default)</br>In the same country or region as the organizer </br> [Zone A countries or regions](audio-conferencing-zones.md) only </br>Don't allow|
|End-user PSTN calls|Restricts the type of calls </br>that can be made by a user.|International and Domestic (default)</br>Domestic</br>None|

To find out which countries and regions are considered Zone A, see [Country and region zones for Audio Conferencing](audio-conferencing-zones.md).

   > [!NOTE]
   > A call is considered domestic if the number dialed is in the same country where Microsoft 365 or Office 365 has been set up for the organizer of the meeting (in the case of audio conferencing), or the end user (in the case of end user PSTN calls).

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Restrict audio conferencing outbound calls

### Using the Microsoft Teams admin center

1. In the left navigation, select **Users**, and then select the display name of the user from the list of available users.

2. Next go to **Audio Conferencing**, select **Edit**.

3. Under **Dial-out from meetings**, select the dial-out restriction option you want.

4. Select **Save**.

### Using PowerShell

Outbound call restrictions are controlled by a single policy called OnlineDialOutPolicy, which has a restriction attribute for each. The policy cannot be customized, rather there are pre-defined policy instances for each combination of the settings.

You can use the Get-CSOnlineDialOutPolicy cmdlet to view the outbound calling policies and use the following command for the setup.

**Set the policy on a per-user level with the following cmdlet**. (The Grant cmdlet doesn't contain the word "Online" as the Get cmdlet does.)

```powershell
Grant-CsDialoutPolicy -Identity <username> -PolicyName <policy name>    
```

**Set the policy on the tenant level with the following cmdlet**.

```powershell
Grant-CsDialoutPolicy -PolicyName <policy name>  -Global 
```

All users of the tenant who don't have any dialout policy assigned will get this policy. Other users remain with their current policy.

**Check the current policy at the tenant level with the following cmdlet**.

```powershell
Get-CSOnlineDialOutPolicy -Identity Global
```

The following table provides an overview of each policy.

|PowerShell cmdlet|Description|
|:-----|:-----|
|Identity='tag:DialoutCPCandPSTNInternational'    |    User in the conference can dial out to   international and domestic numbers, and this user can also make outbound calls to international and domestic numbers.    |
|Identity='tag:DialoutCPCDomesticPSTNInternational'  |    User in the conference can only dial out to   domestic numbers, and this user can make outbound calls to international and domestic numbers.    |
|    Identity='tag:DialoutCPCDisabledPSTNInternational'    |    User in the conference can't dial out. This user can make outbound calls to international and domestic numbers.    |
|    Identity='tag:DialoutCPCInternationalPSTNDomestic'    |    User in the conference can dial out to   international and domestic numbers, and this user can only make outbound calls to domestic PSTN number.    |
|    Identity='tag:DialoutCPCInternationalPSTNDisabled'    |    User in the conference can dial out to   international and domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers.    |
|    Identity='tag:DialoutCPCandPSTNDomestic'    |    User in the conference can only dial out to   domestic numbers, and this user can only make outbound call to domestic PSTN numbers.    |
|    Identity='tag:DialoutCPCDomesticPSTNDisabled'    |    User in the conference can only dial out to   domestic numbers, and this user cannot make any outbound calls to PSTN number besides emergency numbers.    |
|    Identity='tag:DialoutCPCDisabledPSTNDomestic'    |    User in the conference can't dial out, and this user can only make outbound call to domestic PSTN numbers.    |
|    Identity='tag:DialoutCPCandPSTNDisabled'    |    User in the conference can't dial out, and this user can't make any outbound calls to PSTN number besides emergency numbers.    |
|    Identity='tag:DialoutCPCZoneAPSTNInternational'    |    User in the conference can only dial out to [Zone A countries and regions](audio-conferencing-zones.md), and this user can make outbound calls to international and domestic numbers.    |
|    Identity='tag:DialoutCPCZoneAPSTNDomestic'    |    User in the conference can only dial out to [Zone A countries and regions](audio-conferencing-zones.md), and this user can only make outbound calls to domestic PSTN number.    |
|    Identity='tag:DialoutCPCZoneAPSTNDisabled'    |    User in the conference can only dial out to [Zone A countries and regions](audio-conferencing-zones.md), and this user can't make any outbound calls to PSTN number besides emergency numbers.    |
