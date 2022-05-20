---
title: Manage emergency calling policies in Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-voice
f1.keywords:
- CSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage emergency calling policies in Microsoft Teams to define what happens when a Teams user in your organization makes an emergency call. 
ms.custom: 
- seo-marvel-apr2020
- ms.teamsadmincenter.voice.emergencycallingpolicies.overview
---

# Manage emergency calling policies in Microsoft Teams

If your organization uses Microsoft Calling Plans, Operator Connect, or Direct Routing as your [PSTN connectivity option](pstn-connectivity.md), you can use emergency calling policies in Microsoft Teams to define what happens when a Teams user in your organization makes an emergency call.

You can set who to notify and how they are notified when a user who is assigned the policy calls emergency services. For example, you can configure policy settings to automatically notify your organization's security desk and have them listen in emergency calls.  

You manage emergency calling policies by going to **Voice** > **Emergency policies** in the Microsoft Teams admin center or by using Windows PowerShell. The policies can be assigned to users and [network sites](cloud-voice-network-settings.md).

For users, you can use the global (Org-wide default) policy or create and assign custom policies. Users will automatically get the global policy unless you create and assign a custom policy. Keep in mind that you can edit the settings in the global policy but you can't rename or delete it. For network sites, you create and assign custom policies.

If you assigned an emergency calling policy to a network site and to a user and if that user is at that network site, the policy that's assigned to the network site overrides the policy that's assigned to the user.

## Create a custom emergency calling policy

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Calling policies** tab.
2. Click **Add**.
3. Enter a name and description for the policy.
4. Set the **External location lookup mode** to on to allow your end-users to configure their emergency address, when they are working from a network location outside the corporate network.
5. Set how you want to notify people in your organization, typically the security desk, when an emergency call is made. To do this, under **Notification mode**, select one of the following:
    - **Send notification only**: A Teams chat message is sent to the users and groups that you specify.
    - **Conferenced in muted and unable to unmute**: A Teams chat message is sent to the users and groups that you specify and they can listen (but not participate) in the conversation between the caller and the PSAP operator.
    - **Conferenced in muted but are able to unmute**: A Teams chat message is sent to the users and groups that you specify and they can unmute to listen and participate in the conversation between the caller and the PSAP operator.
5.  Set the **Emergency service disclaimer** to show a banner to remind your end-users to confirm their emergency location.
6.  If you selected either of the **Conference in muted** notification modes, in the **Numbers to dial for emergency calls notifications** box, you can enter a PSTN phone number of a user or group to call and join the emergency call. For example, enter the number of your organization's security desk, who will receive a call when an emergency call is made and can then listen in on the call. The PSTN phone cannot be unmuted even when the mode is set to **Conferenced in muted but are able to unmute**.
7. Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made.  The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.
8. Click **Apply**.

### Using PowerShell

See [New-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/new-csteamsemergencycallingpolicy).

## Edit an emergency calling policy

### Using the Microsoft Teams admin center

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Emergency policies**, and then click the **Calling policies** tab.
2. Select the policy by clicking to the left of the policy name, and then click **Edit**.
3. Make the changes that you want, and then click **Apply**.

### Using PowerShell

See [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy).

## Assign a custom emergency calling policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

See also [Grant-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/grant-csteamsemergencycallingpolicy).

## Assign a custom emergency calling policy to a network site

Use the [Set-CsTenantNetworkSite](/powershell/module/skype/set-cstenantnetworksite) cmdlet to assign an emergency calling policy to a network site.

The following example shows how to assign a policy called Contoso Emergency Calling Policy 1 to the Site1 site.

```powershell
Set-CsTenantNetworkSite -identity "site1" -EmergencyCallingPolicy "Contoso Emergency Calling Policy 1"
```

## Related topics

[Manage emergency call routing policies in Teams](manage-emergency-call-routing-policies.md)

[Teams PowerShell overview](teams-powershell-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)
