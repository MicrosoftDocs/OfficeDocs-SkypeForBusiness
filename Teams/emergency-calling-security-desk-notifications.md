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

You configure security desk notifications by using emergency calling policies, which you set by using the Teams admin center or by using PowerShell.

You can grant an emergency calling policy to a Teams user account, assign to a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.

- If the Teams client is unable to obtain an emergency calling policy, then the user isn't enabled for security desk notification.


### Use Teams admin center

To configure security desk notifications by using the Teams admin center, go to **Voice > Emergency policies**, select the **Calling policies** tab, and then select **Add**.  

For each emergency number, specify the **Emergency dial string**, the associated **Notification Groups**, the **Number to dial for emergency notifications**, and the **Notification mode**.

For more information about using the Teams admin center, see [Manage emergency calling policies](manage-emergency-calling-policies.md).  

### Use PowerShell

To configure security desk notifications by using PowerShell, use the  [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/teams/set-csteamsemergencycallingpolicy) cmdlet. 

The following example modifies an existing policy instance with identity TestECP and specifies the notification groups 123@contoso.com and 567@contoso.com:

``` PowerShell
Set-CsTeamsEmergencyCallingPolicy -Identity "TestECP" -NotificationGroup "123@contoso.com;567@contoso.com"
```

## Configure extended notifications

With extended notifications, you can configure specific notification settings for each emergency number. For example, you can specify settings for the emergency number 911 and for the test emergency number 933. With this functionality, you can avoid notifying your security desk for test emergency calls.  

- For each emergency number, you'll set values for **Emergency dial string**, **Notification groups**, **Number to dial for emergency notification**, and **Notification mode**.    

- You can define an extended notification for the test emergency number 933. Because this is a test emergency number, no notifications are sent to the security desk.  

- You can have more than one notification group per number.

- You can only enter a number to dial when the notification mode is NOT "Send notification only". 

**Emergency calling policy Example** In the following example you configure the emergency calling policy with full security desk configuration. Extended notifications for the test emergency number, 933, are set to null.  


- Notification group: alert@contoso.com
- Notification Dial Out Number - 14255551234
- Notification Mode - Conferenced in and are unmuted
- External Lookup Mode - On

The settings are: 

| Emergency dial string | Notification groups | Number to dial for emergency notifications | Notification mode |
| :------------| :-------| :-------| :-------|
| default | alert@contoso.com | 14255551234 | Conferenced in and are unmuted |
| 933 |   |  | None |

<br>


> [!NOTE] 
> If you configure any extended notifications with a Notification Mode of Conferenced in, muted or unmuted, then a default emergency number, no dial string specified, must be set with at least one user, group, or PSTN number and a Notification Mode of Conferenced in. See the example above. 
> 
> If you're using Calling Plan or Operator Connect, the emergency numbers are predefined (in our example, 911 and 933). If you're using Direct Routing, you need to define the numbers in an emergency call routing policy for Direct Routing. For more information, see [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md).


### Use the Teams admin center

To configure the extended notifications example by using the Teams admin center, go to **Voice > Emergency policies**, select the **Calling policies** tab, and then select **Add**.  

For each emergency number, specify the **Emergency dial string**, the associated **Notification Groups**, the **Number to dial for emergency notifications**, and the **Notification mode**.

For more information about using the Teams admin center, see [Manage emergency calling policies](manage-emergency-calling-policies.md).  


### Use Powershell

To configure the extended notifications
by using the [New-CsTeamsEmergencyCallingPolicy](/powershell/module/teams/new-csteamsemergencycallingpolicy) cmdlet, see the following examples:

**Emergency Calling Policy example**

```powershell
$en1 = New-CsTeamsEmergencyCallingExtendedNotification -EmergencyDialString "933"
New-CsTeamsEmergencyCallingPolicy -Identity ECP1 -Description "Test ECP1" -NotificationGroup "alert@contoso.com" -NotificationDialOutNumber "+14255551234" -NotificationMode ConferenceUnMuted -ExternalLocationLookupMode Enabled -ExtendedNotifications @{add=$en1}
```


## Related topics

- [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)

