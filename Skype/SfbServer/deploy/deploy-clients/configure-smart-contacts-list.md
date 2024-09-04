---
ms.date: 03/17/2018
title: "Configure Smart contacts list in Skype for Business clients"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 4eecb5f7-3ef7-4582-a6cb-9f4aa068338d
description: "Summary: Learn how to turn on the Smart contacts list feature in the Skype for Business client."
---

# Configure Smart contacts list in Skype for Business clients

**Summary:** Learn how to turn on the Smart contacts list feature in the Skype for Business client.

The Smart contacts list feature allows automatic population of contact lists for your end users. Upon first using Skype for Business, your users automatically see their manager and other people on their team. This feature is turned on by default for Microsoft 365 and Office 365 users, but you must explicitly enable this feature for your on-premises users by configuring the client policy setting.

Keep the following in mind when configuring this feature:

- Users, up to 13, are automatically added to the Smart contacts list in the following order:

  1. Manager

  2. Directs in alphabetical order

  3. Peers in alphabetical order

- The first time a user logs in, a new group, named My Group, is created. The group is automatically populated with people in the user's AD group relationship based on the user alias populated in the Manager field. Changes to the AD group membership don't cause updates to My Group after it's initially populated. If a user deletes a contact or the group, neither the contact nor the group are re-created. 

- If auto tagging is turned on, contacts in the list are tagged for presence changes. Auto tagging is turned on by default, but you can choose to turn it off. 

- All new users in the group are informed that they're added to the contacts list. Users can manually add new members to their My Group or to other groups of their choosing.

- This feature works only for users who are signing in for the first time. If a user previously signs in from any device--including, for example, any mobile device or a Mac--the feature isn't enabled for that user.

## Configure Smart contacts list

To enable the Smart contacts list feature for your users, you need to perform the following steps: 

- Create a new CsClientPolicy entry and add it to the global client policy. 

- Make sure that Address Book Search is configured for Web Search only.

### Create a policy entry to enable Smart contacts list

To create a policy entry to enable the Smart contacts list feature, use the [New-CsClientPolicyEntry](/powershell/module/skype/new-csclientpolicyentry?view=skype-ps&preserve-view=true) cmdlet with the EnableClientAutoPopulateWithTeam option as follows:

```powershell
$x=New-CsClientPolicyEntry -Name EnableClientAutoPopulateWithTeam -Value $True
```

Next, use the [Set-CsClientPolicy](/powershell/module/skype/set-csclientpolicy?view=skype-ps&preserve-view=true) cmdlet to write the changes to the global policy as follows:

```powershell
Set-CsClientPolicy -Identity Global -PolicyEntry @{Add=$x}
```

You can optionally create a policy to turn off auto tagging as follows:

```powershell
$x=New-CsClientPolicyEntry -Name TagContactsInClientAutoPopulatedGroup -Value $False
Set-CsClientPolicy -Identity Global -PolicyEntry @{Add=$x}
```

You must also set the AddressBookAvailability parameter for the corresponding policy to WebSearchOnly. For more information, see [Set-CsClientPolicy](/powershell/module/skype/set-csclientpolicy?view=skype-ps&preserve-view=true). 

### Troubleshoot

If Smart contacts list isn't functioning as expected, check the following:

- Validate the configuration.

- Confirm that the AD organization information is populated.

- Collect Skype for Business client logs on a new user for further analysis.

- Confirm that the Skype for Business client UI isn't displaying a message that it can't connect to the Address Book. To confirm Address Book connectivity, perform a search for a user in the Skype for Business client search bar.

- AD DS replication issues could cause contacts to be unresolved when a user first signs in to Skype for Business.
