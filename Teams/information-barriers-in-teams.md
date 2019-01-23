---
title: Information barriers in Microsoft Teams (coming soon)
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/23/2019
ms.topic: article
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
ms.reviewer: vikramju
description: Learn about information barriers and how they affect Teams.
appliesto: 
- Microsoft Teams
---

# Information barriers in Microsoft Teams

Information barriers are policies that an admin can configure to prevent individuals or groups from communicating with each other. This is useful if, for example, one department is handling information that shouldn’t be shared with other departments or a group needs to be prevented from communicating with any outside contacts.

## Background

The primary driver for Information Barriers comes from the financial services industry.  The Financial Industry Regulatory Authority ([FINRA]( http://www.finra.org/)) reviews information barriers and conflicts of interest within member firms and provides guidance as to how to manage such conflicts (FINRA 2241, [Debt Research Regulatory Notice 15-31](http://www.finra.org/sites/default/files/Regulatory-Notice-15-31_0.pdf).  

## When should I use information barriers?

You might want to use information barriers in situations like these:

- A team must be prevented from communicating or sharing data with a specific other team.
- A team must not communicate or share data with anyone outside of the team.

The Information Barrier Policy Evaluation Service determines whether a communication complies with information barrier policies. 

## Managing information barrier policies

Information barrier policies are managed with the following Security & Compliance Center (SCC) PowerShell cmdlets:

- **[New-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/New-InformationBarrierPolicy.md)** - Use the New-InformationBarrierPolicy cmdlet to create a new information barrier policy. 
- **[Test-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Test-InformationBarrierPolicy.md)** - Use the Test-InformationBarrierPolicy cmdlet to test a new or modified information barrier policy.
- **[Start-InformationBarrierPoliciesApplication](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Start-InformationBarrierPoliciesApplication.md)** - Use the Start-InformationBarrierPoliciesApplication cmdlet to activate information barrier policies.
- **[Stop-InformationBarrierPoliciesApplication](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Stop-InformationBarrierPoliciesApplication.md)** - Use the StopInformationBarrierPoliciesApplication cmdlet to deactivate information barrier policies.
- **[Get-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Get-InformationBarrierPolicy.md)** - Use the Get-InformationBarrierPolicy cmdlet to view information barrier policies.
- **[Set-informationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Set-InformationBarrierPolicy.md)** - Use the Set-InformationBarrierPolicy cmdlet to modify information barrier policies.
- **[Remove-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Remove-InformationBarrierPolicy.md)** – Use the Remove-InformationBarrierPolicy cmdlet to delete information barrier policies.

> [!IMPORTANT]
> Before you set up or define policies, **you must enable scoped directory search in Microsoft Teams**. Wait at least 24 hours after enabling scoped directory search before you set up or define policies for information barriers.


## Information barriers administrator role

The information barriers administrator role is responsible for managing information barrier policies. For more information about this role, see [Information barriers (coming soon to Microsoft Teams!)](https://review.docs.microsoft.com/en-us/Office365/SecurityCompliance/information-barriers?branch=infobarriers-working).

## When are information barrier policies checked?

Information barrier policies are checked when the following Teams events take place:

- **Members are added to a team** - Whenever you add a user to a team, the user’s policies must be evaluated against the information barrier policy. After the user is successfully added, the user can perform all functions in the team without further checks.
- **A new chat is requested** - Each time a new chat is requested between two or more users, the chat is evaluated to make sure that it isn’t violating any Information barrier policies. If the conversation violates an information barrier policy, then the conversation isn’t initiated, and an error message appears.
- **A user is invited to join a meeting** - When a user is invited to join a meeting, the user is evaluated against the information barrier policy, and if there’s a violation, the user will not be allowed to join the meeting and will see an error message.
- **A screen is shared between two or more users** - Any time a screen is shared between two or more users, the screen share must be evaluated to make sure that it doesn’t violate any information barrier policies. If any information barrier policies are violated, the screen share won’t be allowed, and an error message will appear.
- **A user places a phone call (VOIP) in Teams** - Any time a voice call is initiated by a user to another user or group of users, the call is evaluated to make sure that it doesn’t violate any information barrier policies. If there is any violation, the voice call is blocked.

## What happens to existing chat threads when a policy is changed?

If there is an existing chat or other communication between users, and a new policy is set or an existing policy is modified, existing communications are evaluated to make sure that they aren’t “poisoned” (no longer allowed). 

- **1:1 chat** - If communication between the two users is no longer allowed (if a policy blocking communication is applied to one or both users), further communication is blocked and the chat conversation will become read-only.
- **Group chat** - If communication from one user to the group is no longer allowed (for example, if a user changes jobs), the user will be removed from group chat and further communication with the group will be blocked. The user can still see old conversations (which will be read-only), but will not be able to see or participate in any new conversations with the group. If the new or changed policy preventing communication is applied to more than one user, the users who are affected by the policy will be removed from group chat. They can still see old conversations. 
- **Team** - Any users who have been removed from the group are removed from the team and will not be able to see or participate in existing or new conversations.

When the information  barrier policy admin makes changes to the policy or a policy change kicks into effect because of a user’s job changing or a similar reason, a search needs to be performed on the members to ensure the members in the Team are not violating any policies. 

## More information

For more information about the information barriers admin role and to set or remove information barrier policies, see [Information barriers](https://docs.microsoft.com/en-us/Office365/SecurityCompliance/information-barriers.md).

For more information about the Security and Compliance Center PowerShell cmdlets that control information barrier policies, see:

- [New-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/New-InformationBarrierPolicy.md) 
- [Test-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Test-InformationBarrierPolicy.md)
- [Start-InformationBarrierPoliciesApplication](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Start-InformationBarrierPoliciesApplication.md)
- [Stop-InformationBarrierPoliciesApplication](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Stop-InformationBarrierPoliciesApplication.md)
- [Get-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Get-InformationBarrierPolicy.md)
- [Set-informationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Set-InformationBarrierPolicy.md)
- [Remove-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Remove-InformationBarrierPolicy.md)
