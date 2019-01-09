---
title: Information barriers in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/09/2019
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

Information barrier policies are managed with the following Security and Compliance Center (SCC) PowerShell cmdlets:

- **[Get-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Get-InformationBarrierPolicy.md)** - Use the Get-InformationBarrierPolicy cmdlet to view information barrier policies in the Office 365 Security & Compliance Center.
- **[Set-informationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Set-InformationBarrierPolicy.md)** - Use the Set-InformationBarrierPolicy cmdlet to modify information barrier policies in the Office 365 Security & Compliance Center.
- **[Remove-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Remove-InformationBarrierPolicy.md)** – Use the Remove-InformationBarrierPolicy cmdlet to remove information barrier policies from the Office 365 Security & Compliance Center.

## Information barriers administrator role

The information barriers administrator role is responsible for managing information barrier policies. For more information about this role, see <link to SCC doc>.

## When are information barrier policies checked?

Information barrier policies are checked when the following Teams events take place:

- **Members are added to a team** - Whenever you add a user to a team, the user’s policies must be evaluated against the information barrier policy. After the user is successfully added, the user can perform all functions in the team without further checks.
- **A new chat is requested** - Each time a new chat is requested between two or more users, the chat is evaluated to make sure that it isn’t violating any Information barrier policies. If the conversation violates an information barrier policy, then the conversation isn’t initiated, and an error message appears.
- **A user is invited to join a meeting** - When a user is invited to join a meeting, the user is evaluated against the information barrier policy, and if there’s a violation, the user will not be allowed to join the meeting and will see an error message.
- **A screen is shared between two or more users** - Any time a screen is shared between two or more users, the screen share must be evaluated to make sure that it doesn’t violate any information barrier policies. If any information barrier policies are violated, the screen share won’t be allowed, and an error message will appear.
- **A user places a phone call (VOIP) in Teams** - Any time a voice call is initiated by a user to another user or group of users, the call is evaluated to make sure that it doesn’t violate any information barrier policies. If there is any violation, the voice call is blocked.

## What happens to existing chat threads when a policy is changed?

If there is an existing chat or other communication between users, and a new policy is set or an existing policy is modified, existing communications are evaluated to make sure that they aren’t “poisoned” (no longer allowed). If a communication is poisoned, further communication is blocked, and the user’s contribution is deleted from existing threads.

When the information  barrier policy admin makes changes to the policy or a policy change kicks into effect because of a user’s job changing or a similar reason, a search needs to be performed on the members to ensure the members in the Team are not violating any policies. Any members who have been removed from the group are removed from the team.  

## More information

For more information about the information barriers admin role and to set or remove information barrier policies, see <link to SCC doc>.

For more information about the Security and Compliance Center PowerShell cmdlets that control information barrier policies, see:

- [Get-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Get-InformationBarrierPolicy.md) 
- [Set-informationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Set-InformationBarrierPolicy.md) 
- [Remove-InformationBarrierPolicy](https://github.com/MicrosoftDocs/office-docs-powershell/blob/InfoBarrier-chrisda/exchange/exchange-ps/exchange/policy-and-compliance/Remove-InformationBarrierPolicy.md)
