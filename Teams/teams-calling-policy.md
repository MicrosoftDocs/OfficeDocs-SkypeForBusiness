---
title: Calling policies in Microsoft Teams
author: LolaJacobsen
ms.author: tonysmit
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jastark
audience: admin
search.appverid: MET150
description: Learn how to create, modify, and add users to custom calling policies in Microsoft Teams, as well as various calling policy settings.
localization_priority: Normal
ms.custom: 
  - NewAdminCenter_Update
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.callingpolicies.overview
  - seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

Calling policies in Microsoft Teams
===================================

In Microsoft Teams, calling policies control which calling and call forwarding features are available to users. Calling policies determine whether a user can make private calls, use call forwarding or  simultaneous ringing to other users or external phone numbers, route calls to voicemail, send calls to Call Groups, use delegation for inbound and outbound calls, and so on. A default global policy is created automatically, but admins can also create and assign custom calling policies.

## Create a custom calling policy

Follow these steps to create a custom calling policy.

1. In the Microsoft Teams admin center, go to **Voice** > **Calling policies**.
2. Select **Add**.
3. Turn on the features that you want to use in your calling policy.
4. To control whether users can route inbound calls to voicemail, select **Enabled** or **User controlled**. To prevent routing to voicemail, select **Disabled**.
5. Select **Save**.

## Modify an existing calling policy

Follow these steps to modify an existing calling policy.

1. In the left navigation of the Microsoft Teams admin center, select **Voice** > **Calling policies**.
2. Click next to the policy that you want to modify, and then select **Edit**.
3. Make the changes that you want, adn then click **Save**.

### Assign a custom calling policy to users

To assign a policy to one user:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Under **App setup policy**, select the app setup policy you want to assign, and then click **Apply**.

To assign a policy to multiple users at a time:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then search for the users or filter the view to show the users you want.
2. In the **&#x2713;** (check mark) column, select the users. To select all users, click the &#x2713; (check mark) at the top of the table.
3. Click **Edit settings**, make the changes that you want, and then click **Apply**.  

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. After you finish adding users, select **Save**.

## Calling policy settings

Use the following settings to create a custom calling policy.

### Make private calls

This setting controls all calling capabilities in Teams. Turn this off to turn off all calling functionality in Teams.

### Call forwarding and simultaneous ringing to people in your organization

This setting controls whether incoming calls can be forwarded to other users or can ring another person at the same time. 

### Call forwarding and simultaneous ringing to external phone numbers

This setting controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.

### Voicemail is available for routing inbound calls

This setting enables inbound calls to be sent to voicemail. Valid options are:

  - **Enabled** Voicemail is always available for inbound calls. 
  - **Disabled**  Voicemail is not available for inbound calls. 
  - **User controlled** Users can determine whether they want voicemail to be available.

### Inbound calls can be routed to call groups 

> [!Include [feature preview](includes/preview-feature.md)]

This setting controls whether incoming calls can be forwarded to a call group.

### Allow delegation for inbound and outbound calls

> [!Include [feature preview](includes/preview-feature.md)]

This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions. For more information, see [Share a phone line with a delegate](https://support.office.com/article/share-a-phone-line-with-a-delegate-16307929-a51f-43fc-8323-3b1bf115e5a8).

### Prevent toll bypass and send calls through the PSTN 

Setting this to **On** will send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.

### Busy on Busy is available while in a call

Busy on Busy (Busy Options) is a new setting that lets you configure how incoming calls are handled when a user is already in a call or conference or has a call placed on hold. New or incoming calls can be rejected with a busy signal. You can enable busy options at the tenant level or at the user level. Regardless of how their busy options are configured, users in a call or conference or those with a call on hold are not prevented from initiating new calls or conferences. This setting is disabled by default.

### Allow web PSTN calling



### Allow music on hold

This settings allows you to turn on or turn off music on hold when a PSTN caller is placed on hold. It is turned on by default. This setting does not apply to call park and boss delegate features, and is only available via powershell currently. 

## See also

[Set-CSTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy?view=skype-ps)
