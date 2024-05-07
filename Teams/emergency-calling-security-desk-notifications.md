---
title: Configure security desk notifications
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 05/03/2024
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
description: Learn how to configure security desk notifications for emergency calling.
---

# Security desk notifications

This article is for administrators and IT professionals who are configuring security desk notifications for emergency calling. Before reading this article, be sure to read [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

Security desk notifications are available with Microsoft Calling Plans, Operator Connect, and Direct Routing.

You can configure who's notified during an emergency call, and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute. You can specify an external PSTN number to call and join the emergency call. Note that the PSTN party is not allowed to unmute.

During an emergency call, a security desk is conferenced into the call, and the security desk user experience is determined by the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification. If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

You can also configure extended notification settings per emergency number. For example, you can specify how a call to the emergency test number 933 is handled without notifying the security desk.

## Configure security desk notifications

You configure security desk notifications by using emergency calling policies, which you can set by using the Teams admin center or by using PowerShell.

You can grant an emergency calling policy to a Teams user account, assign to a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.

- If the Teams client is unable to obtain an emergency calling policy, then the user isn't enabled for security desk notification.


### Use Teams admin center

To configure security desk notifications by using the Teams admin center, go to **Voice > Emergency policies**, select the **Calling policies** tab, and then select **Add**.  

For complete information on using the Teams admin center, see [Manage emergency calling policies](manage-emergency-calling-policies.md).  

### Use PowerShell

To configure security desk notifications by using PowerShell, use the  [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/teams/set-csteamsemergencycallingpolicy) cmdlet. 

The following example modifies an existing policy instance with identity TestECP and specifies the notification groups 123@contoso.com and 567@contoso.com:

``` PowerShell
Set-CsTeamsEmergencyCallingPolicy -Identity "TestECP" -NotificationGroup "123@contoso.com;567@contoso.com"
```

## Configure extended notifications

Extended notifications allow you to specify additional emergency numbers. For example, you can specify settings for the emergency number 911 and for the test emergency number 933. With this functionality, you can avoid notifying your security desk for test emergency calls. 

You can add extended notification settings to the policy per defined emergency number. For example, you might:

1. Create the extended notification for the test emergency number 933. If you are using Calling Plan or Operator Connect, this emergency number is predefined. If you are using Direct Routing, you need to define the number in the emergency call routing policy. 

2. Create a second emergency calling policy called Default911. This policy specifies that the alert@contoso.com group is notified of an emergency call through a conference call. The external PSTN number +14255551234 is brought into the conference call and the extended notification is added.  

When an emergency call is made to any defined emergency number except 933, the group is notified via a conference call with the external PSTN participant. When an emergency call is made to the test emergency number 933, no notifications are generated. 

For example:

123@contoso.com;567@contoso.com 

| Emergency dial string | Notification groups | Number to dial | Notification mode |
| :------------| :-------| :-------| :-------|
| 933 | 123@contoso.com;567@contoso.com | 14255551234 | Conference in but are muted|
| 911 |   alert@contoso.com  |  | Send notifiction only |

### Use the Teams admin center

To configure the extended notifications example by using the Teams admin center, go to **Voice > Emergency policies**, select the **Calling policies** tab, and then select **Add**.  

For each emergency number, specify the **Emergency dial string**, the associated **Notification Groups**, the **Number to dial for emergency notifications**, and the **Notification mode**.

- You can have more than one notification group per number.

- You can only enter a number to dial when the notification mode is NOT "Send notification only".  



### Use Powershell

To configure the extended notifications example 
by using the [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/teams/set-csteamsemergencycallingpolicy) cmdlet:

```powershell
$en1 = New-CsTeamsEmergencyCallingExtendedNotification -EmergencyDialString "933"  

New-CsTeamsEmergencyCallingPolicy -Identity Default911 -Description "Default Emergency notification" -NotificationGroup "alert@contoso.com" -NotificationDialOutNumber "+14255551234" -NotificationMode ConferenceMuted -ExtendedNotifications @{add=$en1} 
```

## Related topics

- [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)

