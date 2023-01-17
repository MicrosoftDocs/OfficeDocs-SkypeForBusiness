---
title: Set up auto answer for Teams Android devices
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: kponnus
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to set up the auto answer feature for Microsoft Teams Rooms on Android and Teams video phone devices with PowerShell.
---

# Set up auto answer for Microsoft Teams Rooms on Android and Teams video phone devices

This article will help you set up the auto answer feature on Microsoft Teams Rooms on Android and Teams video phone devices. Auto answer allows people in your organization with administrative privileges to change their device settings to automatically accept incoming meeting invites and automatically accept calls with video.

## Enable auto answer with PowerShell

Use the following attributes to enable auto answer on Microsoft Teams Rooms on Android and Teams video phone devices:

- **Set-CsTeamsCallingPolicy -AutoAnswerEnabledType**
- **Set-CsTeamsIPPhonePolicy -SignInMode**

### 1. Turn on auto answer for incoming meeting invites

You use **Set-CsTeamsCallingPolicy -AutoAnswerEnabledType** to turn on auto answer for incoming meeting invites. Auto answer is **turned off** by default. This policy only applies to incoming meeting invites and doesn't support other call types. Read [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy) for more information on the cmdlet.

```powershell
Set-CsTeamsCallingPolicy -AutoAnswerEnabledType Enabled
```

### 2. Set the device sign-in mode

You use **Set-CsTeamsIPPhonePolicy -SignInMode** to set the sign-in mode for the device to determine the behavior when signing into Teams. Read [Set-CsTeamsIPPhonePolicy](/powershell/module/skype/set-csteamsipphonepolicy) for more information on the cmdlet.

There are three options for sign-in mode:

- **UserSignIn:** Enables an individual user Teams experience on the phone.
- **CommonAreaPhoneSignIn:** Enables a common area phone experience on the phone.
- **MeetingSignIn:** Enables a meeting room experience on the phone.

For example, the following policy sets the sign-in mode to a meeting room experience.

```powershell
Set-CsTeamsIPPhonePolicy -Identity Device -SignInMode MeetingSignIn
```

### Configure device settings

After enabling auto answer, users with administrative permissions can turn on the feature in their device settings. To enable the feature at the device level, you need to turn on **Auto accept incoming meeting invites**. You can also turn on **Auto accept with video**. Both settings are off by default.

## Related topics

[Microsoft Support: Calls and devices](https://support.microsoft.com/office/calls-and-devices-4d96653e-6176-4978-98ab-2c19df137e43#ID0EBBD=Devices)

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

[Set-CsTeamsIPPhonePolicy](/powershell/module/skype/set-csteamsipphonepolicy)
