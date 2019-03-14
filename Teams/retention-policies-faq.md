---
title: Microsoft Teams retention policies FAQ
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/11/2018
ms.topic: reference
ms.service: msteams
ms.reviewer: anach
description: Frequently asked questions about retention policies in Microsoft Teams. 
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Microsoft Teams retention policies FAQ

### What types of policies can I set up in retention policies and how do they work?

In the Security & Compliance Center, when you set up a retention policy, for Teams or for any other workload, you can set up two main types of policies: 
- Preservation: These policies ensure that your data is preserved for a given period of time, no matter what happens in the end user tools. They ensure that data is preserved for compliance reasons and available in eDiscovery until this time expires. After the time expires, your policy can indicate whether to do nothing or delete the data. In Teams, if you create a preservation policy for 7 years, even if end users delete their Teams messages, these messages are still preserved for eDiscovery for 7 years.
- Deletion: These policies ensure that data is not a liability for your organization. After the specified duration, data is deleted from all relevant storage in Teams. 

### Can we include Teams in org-wide policies? 

No, not currently. You must create specific policies for Teams chat and channel messages using the Teams location row or these Teams cmdlets: [New-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancepolicy?view=exchange-ps) & [New-TeamsComplianceRetentionRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancerule?view=exchange-ps). These cmdlets have get and set versions as well.

### Are these retention policies retroactive? 

Yes, they are. If you create a retention policy to delete data older than 60 days, it will delete Teams data created more than 60 days ago. 

### What is the default retention policy? 

By default, Teams chat, channel, and files data are retained forever. A user can delete something, but in the absence of retention policies, Teams data is always archived into Exchange online mailboxes (user and group) and stays there for eDiscovery. 

### Can I target sets of users or teams in a policy? 

Yes, you do. In the policy creation wizard, in the Locations step, you can include or exclude teams (**Teams channel messages**) or users (**Teams chat**) and create targeted policies for your organization. 

### What is the main difference between using the Group mailbox location row and Teams channel messages location row in retention policies? 

If you use the Group mailbox and User mailbox location rows for Exchange Online, Teams data will be deleted from the specified mailboxes. However, this only removes data from the mailbox. It doesn’t delete other Teams data, such as chats service. We recommend that you use Teams retention policies to properly manage all Teams data. A Teams retention policy removes teams data from all storage locations – Mailboxes, Chat service, Teams clients. 

Note: Launch of the retention policies feature for Teams makes sure that only Teams policies delete Teams items stored inside Exchange mailbox locations (user or group). Other policies setup on mailboxes cannot affect Teams items. This was true in the past, but has been fixed with the launch of retention policies feature. 

### What happens to Skype for Business Online and Teams interop chats – are they affected by retention policies?

Yes, Skype for Business Online and Teams interop chats work the same way. Once the Skype for Business Online chat comes into Teams, it becomes a message in a Teams chat thread and gets ingested into the appropriate mailbox. So the same flow works – Teams deletion policies will delete these messages from the Teams thread. However, if conversation history is turned on for Skype for Business Online and from the Skype for Business Online client side those are being saved into a mailbox, this chat data is not handled by a Teams retention policy.

### Can I do these through Security & Compliance Center cmdlets? What should I use? 

Absolutely. You can create Teams retention policies using [Security & Compliance Center Powershell cmdlets]( https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps). Remember these are not Exchange Online cmdlets. 
Here are the cmdlets we created for Teams. They follow existing nomenclature and style from retention cmdlets available today in Security & Compliance Center.

|Policy|Rule|
|---|---|
|[New-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancepolicy?view=exchange-ps)| [New-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancerule?view=exchange-ps)|
|[Get-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancepolicy?view=exchange-ps)| [Get-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancerule?view=exchange-ps)|
|[Set-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancepolicy?view=exchange-ps)| [Set-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancerule?view=exchange-ps)|
|[Remove-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancepolicy?view=exchange-ps)| [Remove-TeamsRetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancerule?view=exchange-ps)|

### If there are multiple retention policies for Teams with varying durations, which one wins?

We follow [Principles of retention policies](https://support.office.com/article/overview-of-retention-policies-5e377752-700d-4870-9b6d-12bfc12d2423), and we recommend that you do too. The short answer is: 
-	Preservation always wins over deletion
-	Longest preservation period always wins
-	Explicit inclusion wins over implicit inclusion in terms of locations
-	Shortest deletion period wins
