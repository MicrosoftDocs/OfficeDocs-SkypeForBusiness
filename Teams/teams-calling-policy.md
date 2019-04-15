---
title: Calling policies in Microsoft Teams
author: LolaJacobsen
ms.author: tonysmit
manager: serdars
ms.date: 04/15/2019
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jastark
search.appverid: MET150
description: Learn about calling policy settings in Microsoft Teams.
localization_priority: Normal
ms.custom:
- NewAdminCenter_Update
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Calling policies in Microsoft Teams
==========================================

In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can make private calls, use call forwarding or  simultaneous ringing to other users or external phone numbers, route calls to voicemail, send calls to Call Groups, use delegation for inbound and outbound calls, and so on. A default global policy is created automatically, but admins can also create and assign custom calling policies.

## Calling policy settings

|Calling policy setting | Description |
|-----------------------|-------------|
|User can make private calls | Controls all calling capabilities in Teams. Turning this off will turn off all calling functionality in Teams.|
|Call forwarding and simultaneous ringing to other users | Controls whether incoming calls can be forwarded to other users or can ring another person at the same time. |
|Call forwarding and simultaneous ringing to external phone numbers | Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail is available for routing inbound calls to users | Enables inbound calls to be sent to voicemail. Valid options are **Always enabled**, **Always disabled**, or **User controlled**. |
|Inbound calls can be routed to call groups | Controls whether incoming calls can be forwarded to a call group.  |
|Allow delegation for inbound and outbound calls | Enables inbound calls to be routed to delegates; allows delegates to make outbound calls on behalf of the users for whom they have delegated permissions. |
|Prevent toll bypass and send calls through the PSTN | Setting this to **On** will send calls through PSTN and incur charges rather than going through the network and bypassing the tolls. |
|Busy on Busy is available while in a call.| Configures how incoming calls are handled when a user is already in a call or conference. New or incoming calls can be rejected with a busy signal. |

### Busy options (Busy on Busy setting)

Busy options is a new setting in the Teams calling policies that allows you to configure how incoming calls are handled when a user is already in a call or conference or has a call placed on hold. New or incoming calls can be rejected with a busy signal. You can enable busy options at a tenant level or at a user level. 

Regardless of how their busy options are configured, users in a call or conference or those with a call on hold are not prevented from initiating new calls or conferences.

You can use the Busy on busy setting in Calling policy settings to configure busy options or you can use the **EnableBusyOnBusy** setting in the Set-CsTeamsCallingPolicy PowerShell cmdlet. This setting is disabled by default. For more information, go to [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy?view=skype-ps
).

## Create a custom calling policy

Follow these steps to create a new custom calling policy.

1. In the Microsoft Teams admin center, select **Voice** > **Calling policy**.
2. Select **New policy**.
3. Turn on the features that you want to use in your calling policy. All selections are **Off** by default.
4. To control whether users can route inbound calls to voicemail, select **Always enabled** or **User controlled**. To prevent routing to voicemail, select **Always disabled**.
5. Select **Save**.

## Modify an existing calling policy

Follow these steps to modify an existing calling policy.

1. In the Microsoft Teams admin center, select **Voice** > **Calling policy**.
2. Click next to the policy that you want to modify, and then select **Edit**.
3. Turn on the features that you want to use in your calling policy. All selections are **Off** by default.
4. To control whether users can route inbound calls to voicemail, select **Always enabled** or **User controlled**. To prevent routing to voicemail, select **Always disabled**.
5. Select **Save**.

## Assign a calling policy to a user

Follow these steps to assign a custom calling policy to a user.

1. In the Microsoft Teams admin center, select **Voice** > **Calling policy**.
2. Click next to the policy name to select it, and then select **Manage users**.
3. In the **Manage users** pane, search for the user’s name. (You must enter at least three characters.)
4. Select the user’s name, and then select **Add**.
5. Select **Save**.
