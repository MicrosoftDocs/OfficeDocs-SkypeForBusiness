---
title: End-to-end encryption for Microsoft Teams
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 03/08/2022
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: ashgupt
description:  Learn about enhanced encryption capabilities in Microsoft Teams, manage end-to-end encryption using the Teams admin center and Microsoft PowerShell.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Use end-to-end encryption for one-to-one Microsoft Teams calls

> [!IMPORTANT]
> The Teams service model, and its encryption support, is subject to change in order to improve customer experiences. For example, the service regularly deprecates cipher suites that are no longer considered secure. Any such changes would be made with the goal of keeping Teams secure and Trustworthy by Design. In addition, all customer content in Microsoft data centers is encrypted. For information about encryption layers in Microsoft 365, see [Encryption in Microsoft 365](/microsoft-365/compliance/encryption).

End-to-end encryption, or E2EE, happens when content is encrypted before it's sent and decrypted only by the intended recipient. With end-to-end encryption, only the two endpoint systems are involved in encrypting and decrypting the call data. No other party, including Microsoft, has access to the decrypted conversation.

With E2EE for unscheduled one-to-one calls, only the real-time media flow, that is, video and voice data, for one-to-one Teams calls are end-to-end encrypted. Both parties must turn on this setting to enable end-to-end encryption. [Encryption in Microsoft 365](/microsoft-365/compliance/encryption) protects chat, file sharing, presence, and other content in the call.

End-to-end encrypted calls can be made between two parties when: the parties are using the latest version of the Teams desktop client for Windows or Mac, they are on a mobile device with the latest update for iOS and Android, or they are on a Teams Rooms on Windows device using the latest update.

If you don't enable end-to-end encryption, Teams still secures a call or meeting using encryption based on industry standards. Data exchanged during calls is always secure while in transit and at rest. For more information, see [Media encryption for Teams](teams-security-guide.md#media-encryption).

During an end-to-end encrypted call, Teams secures the following features:

- Audio

- Video

- Screen sharing

The following advanced features aren't available during an E2EE call:

- Live captions and transcription

- Call transfer

- Call merge

- Call park

- Consult then transfer

- Call companion and transfer to another device

- Adding a participant

- Recording

- Forward to Voicemail

- Simultaneanous ring

Also, if your organization uses compliance recording, end-to-end encryption isn't available. For more info on how Teams supports compliance recording, see [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md).

## Configure end-to-end encryption for Microsoft Teams

Complete these tasks so your users can place end-to-end encrypted calls.

- Enable end-to-end encryption for your organization by creating one or more policies that define who can use end-to-end encryption. Before you start, make sure that your work or school account has been assigned the Teams or global administrator role. For information, see [Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md). When you're ready to set up E2EE, you can use the Teams admin center or Microsoft PowerShell.

- Switch on end-to-end encrypted calls in Teams settings on your device. Each user needs to complete this task, but they only need to do it on one device. Teams synchronizes this setting across supported end points for each user. For instructions, see [Use end-to-end encryption for Teams calls](https://support.microsoft.com/office/1274b4d2-b5c5-4b24-a376-606fa6728a90).

### Use the Teams admin center to configure end-to-end encryption

The global, organization-wide, default policy specifies that end-to-end encryption is disabled. Users in your organization will automatically get the global policy unless you create and assign a custom policy. To enable end-to-end encryption, create a new encryption policy or modify the global default policy. To enable end-to-end encryption using the Teams admin center, complete these steps.

1. Using a work or school account that has been assigned the Teams or global administrator role, sign in to the [Teams admin center](https://admin.teams.microsoft.com/).

2. Go to **Enhanced encryption policies**.

3. Either choose the default policy or choose **Add** to add a new policy and then name the new policy.

4. To enable end-to-end encryption for your users, for **End-to-end call encryption**, choose **Disabled user override**, and then choose **Save**.

   To disable end-to-end encryption, choose **Disabled**.

Once you’ve finished setting up the policy, assign the policy to users, groups, or your entire tenant the same way you manage other Teams policies. For information about using policies in Teams, see [Manage Teams with policies](manage-teams-with-policies.md).

### Use Microsoft PowerShell to configure end-to-end encryption

You can manage end-to-end encryption policies using Microsoft PowerShell and the Teams admin center. Several end-to-end encryption cmdlets are included in the Teams PowerShell module and documented in the [Microsoft Teams cmdlet reference](/powershell/teams/?view=teams-ps&preserve-view=true). This article lists the cmdlets you can use and provides simple example configurations. These configurations use the default, global policy. Your organization might require more complex policy configuration. Complete information about these cmdlets is provided in the cmdlet reference.

End-to-end encryption PowerShell cmdlets:

- [Get-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Get-CsTeamsEnhancedEncryptionPolicy) returns information about the Teams enhanced encryption policies in your organization.

- [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy) assigns and unassigns existing enhanced encryption policies to a user. Use `$NULL` to unassign all policies from a user.

- [New-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/New-CsTeamsEnhancedEncryptionPolicy) creates a new Teams enhanced encryption policy.

- [Remove-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Remove-CsTeamsEnhancedEncryptionPolicy) deletes an enhanced encryption policy from your organization. You can't delete the global, default policy.

- [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy) updates values in an existing Teams enhanced encryption policy.

Your work or school account needs the Teams or global administrator role to configure end-to-end encryption.

#### To enable end-to-end encryption for your entire tenant using the global policy

By default, end-to-end encryption is disabled. To enable end-to-end encryption for the entire tenant by setting the default global policy, run the [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy) cmdlet as follows.

```powershell
Set-CsTeamsEnhancedEncryptionPolicy -Identity Global -CallingEndtoEndEncryptionEnabledType DisabledUserOverride
```

Where:

- `Global` means that you're setting this configuration on the global, organization-wide default policy.

- `DisabledUserOverride` means that E2EE is disabled in Teams by default, but users can override the default and turn on E2EE in their Teams settings.

#### To disable end-to-end encryption for your entire tenant using the global policy

By default, end-to-end encryption is disabled. If you've made changes to the global policy, you can change the setting back by running the [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy) cmdlet as follows.

```powershell
Grant-CsTeamsEnhancedEncryptionPolicy -Identity Global -CallingEndtoEndEncryptionEnabledType Disabled
```

Where:

- `Global` means that you're setting this configuration on the global, organization-wide default policy.

- `Disabled` means that you're disabling E2EE for everyone and users can't turn it on in their Teams settings.

#### To enable end-to-end encryption for a single user

To enable end-to-end encryption for a user, run the [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy) cmdlet as follows.

```powershell
Grant-CsTeamsEnhancedEncryptionPolicy -Identity "username" -PolicyName "policyname"
```

Where:

- *`username`* is the name of the user.

- *`policyname`* is the name you want to use for the policy. Policy names can't contain spaces, for example, ContosoE2EEUserPolicy.

Users still need to switch on end-to-end encrypted calling in their Teams settings before they can make an end-to-end encrypted call. For instructions, see [Use end-to-end encryption for Teams calls](https://support.microsoft.com/office/1274b4d2-b5c5-4b24-a376-606fa6728a90).

For example:

```powershell
Grant-CsTeamsEnhancedEncryptionPolicy -Identity "kenmeyer@contoso.onmicrosoft.com" -PolicyName "ContosoE2EEUserPolicy"
```

#### To unassign an end-to-end encryption policy from a single user

Users can have one and only one encryption policy assigned to them at a time. When you unassign a policy from a user, the user is then assigned the global, organization-wide, default policy. You can't unassign the default policy. To unassign an end-to-end encryption policy from a user, run the [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy) cmdlet as follows.

```powershell
Grant-CsTeamsEnhancedEncryptionPolicy -Identity "kenmeyer@contoso.onmicrosoft.com" -PolicyName $NULL
```

## Switch on end-to-end encryption on your device

For instructions, see [Use end-to-end encryption for Teams calls](https://support.microsoft.com/office/1274b4d2-b5c5-4b24-a376-606fa6728a90).

## Related topics

[Top 12 tasks for security teams to support working from home](/microsoft-365/security/top-security-tasks-for-remote-work)

[Manage meeting settings in Microsoft Teams](./meeting-settings-in-teams.md)
