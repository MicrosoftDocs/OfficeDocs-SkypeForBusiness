---
title: "What are the special character restrictions in Teams policies?"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
f1keywords:
- me.teamsadmincenter.policies.naming.error
description: "See what issues there are with special characters in the names of policies and what you can do to fix it."
---

# What are the special character restrictions in Teams policies?

**Although special characters can be used for creating Teams policies with PowerShell, you will be limited in managing these policies .  As such, we strongly recommend policy names do not include special characters.**

Policy names that you create using PowerShell for meetings and chat in Teams can have special characters such as @,#,$. However, if you are wanting to edit the policy in the Microsoft Teams and Skype for Business admin center, you won't be able to. You must use Windows PowerShell and the correct policy cmdlet to make changes.

If you have a policy object with special characters and you want to remove the special characters in order to better manage the policy in the Microsoft Teams and Skype for Business admin center, you will need to use the below procedure. 

Note: The procedure articulated here uses the example of a Messaging policy.  The same process would be used for another policy type (Meetings for example) by subsituting the relevant cmdlets. 

1.) Call Get-CSMessagingPolicy -identity <old_policy_name> and capture the output of the policy.
2.) Call Set-CSMessagingPolicy -identity <new_policy_name> to create a new policy with the same configuration as the original policy but without any special characters in the name.
3.) Call Delete-CSMessagingPolicy -identity <old_policy_name> to delete the policy.  If this command succeeds, you're done and can begin to assign users to the new policy using either PowerShell or the Microsoft Teams and Skype for Business admin center.
4.) If the above command does not succeed, it is because the old policy has been assigned to a user.  Run unassign cmdlet to unassign the policy from user, assign new policy, then run dwlete again.


