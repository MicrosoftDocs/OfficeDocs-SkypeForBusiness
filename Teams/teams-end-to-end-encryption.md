---
title: End-to-end encryption for Microsoft Teams
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 10/23/2021
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

# Use end-to-end encryption for one-to-one Microsoft Teams calls (Public preview)

> [!IMPORTANT]
> The Teams service model, and its encryption support, is subject to change in order to improve customer experiences. For example, the service regularly deprecates cipher suites that are no longer considered secure. Any such changes would be made with the goal of keeping Teams secure and Trustworthy by Design. In addition, all customer content in Microsoft data centers is encrypted. For information about encryption layers in Microsoft 365, see [Encryption in Microsoft 365](/microsoft-365/compliance/encryption).

End-to-end encryption, or E2EE, is the encryption of information at its origin and decryption at its intended destination without permitting intermediate nodes or parties to decrypt the data. When both parties in a one-to-one VOIP call turn on E2EE, the communication between those two parties is encrypted from end to end. This means that no other party, including Microsoft, has access to the decrypted conversation.

With this public preview release, we're rolling out this preview of E2EE for unscheduled one-to-one calls. Only the real-time media flow, that is, video and voice data, for one-to-one Teams calls are end-to-end encrypted. Both parties must turn on this setting to enable end-to-end encryption. [Encryption in Microsoft 365](/microsoft-365/compliance/encryption) protects chat, file sharing, presence, and other content in the call.

If you don't enable end-to-end encryption, Teams still secures a call or meeting using encryption based on industry standards. Data exchanged during calls is always secure while in transit and at rest. For more information, see [Media encryption for Teams](teams-security-guide.md#media-encryption).

During an end-to-end encrypted call, Teams secures the following features:

- Audio

- Video

- Screen sharing

Advanced features, including those listed here, aren't available during an E2EE call:

- Live captions and transcription

- Call transfer

- Call merge

- Call park

- Consult then transfer

- Call companion and transfer to another device

- Adding a participant

- Recording

In addition, if your organization uses compliance recording, end-to-end encryption isn't available. For more info on how Teams supports compliance recording, see [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md).

## Configure end-to-end encryption for Microsoft Teams

Complete these tasks so your users can place end-to-end encrypted calls.

- Enable end-to-end encryption for your organization by creating a policy that defines who can use end-to-end encryption. Before you start, make sure that your work or school account has been assigned the Teams or global administrator role. For information, see [Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md). When you're ready, you can use the Teams admin center or Microsoft PowerShell.

- Switch on end-to-end encrypted calls in Teams settings on your device. Each user needs to complete this task, but they only need to do it on one device. Teams synchronizes this setting across supported end points for each user.

### Use the Teams admin center to configure end-to-end encryption

The global, organization-wide, default policy specifies that end-to-end encryption is disabled. To enable end-to-end encryption, create a new encryption policy or modify the global default policy. To enable end-to-end encryption using the Teams admin center, complete these steps.

1. Using a work or school account that has been assigned the Teams or global administrator role, sign in to the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

2. Go to **Other settings** > **Enhanced encryption policies**.

3. Either choose the default policy or choose **Add** to add a new policy and then name the new policy.

4. To enable end-to-end encryption for your users, for **End-to-end call encryption**, choose **users can turn it on**, and then choose **Save**.

   To disable end-to-end encryption, choose **Turn it off for everyone**.

Once you’ve finished setting up the policy, assign the policy to users, groups, or your entire tenant the same way you manage other Teams policies. For information about using policies in Teams, see [Manage Teams with policies](manage-teams-with-policies.md).

### Use Microsoft PowerShell to configure end-to-end encryption

You can manage end-to-end encryption policies via Microsoft PowerShell in addition to the Teams admin center. Several end-to-end encryption cmdlets are included in the Teams PowerShell module and documented in the Skype for Business cmdlet reference. This article includes a list of the cmdlets you can use and some example use scenarios. For more information about using Microsoft PowerShell with Teams, see [Manage policies via PowerShell](teams-powershell-managing-teams.md#manage-policies-via-powershell).

End-to-end encryption PowerShell cmdlets:

- [Get-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Get-CsTeamsEnhancedEncryptionPolicy)

- [Grant-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Grant-CsTeamsEnhancedEncryptionPolicy)

- [New-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/New-CsTeamsEnhancedEncryptionPolicy)

- [Remove-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Remove-CsTeamsEnhancedEncryptionPolicy)

- [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy)

#### PowerShell examples

Using a work or school account that has been assigned the Teams or global administrator role, 

To turn on end-to-end encryption for a single user:

Grant-CsTeamsEnhancedEncryptionPolicy -Identity "kenmeyer@contoso.onmicrosoft.com" -policyname Tag:UserControlled

To turn it on for entire tenant:
Set-CsTeamsEnhancedEncryptionPolicy -Identity Global -CallingEndtoEndEncryptionEnabledType DisabledUserOverride

To turn it off for a single user (this is true even if the user is a member of a group or the tenant)
Grant-CsTeamsEnhancedEncryptionPolicy -Identity "kenmeyer@contoso.onmicrosoft.com" CallingEndtoEndEncryptionEnabledType DisabledUserOverride

To turn it off for the entire tenant.
Grant-CsTeamsEnhancedEncryptionPolicy -Identity "kenmeyer@contoso.onmicrosoft.com" CallingEndtoEndEncryptionEnabledType Disabled

## Switch on end-to-end encryption on your device

For instructions, see [Use end-to-end encryption for Teams calls](https://support.microsoft.com/office/1274b4d2-b5c5-4b24-a376-606fa6728a90).

## Related topics

[Top 12 tasks for security teams to support working from home](/microsoft-365/security/top-security-tasks-for-remote-work)

[Manage meeting settings in Microsoft Teams](./meeting-settings-in-teams.md)
