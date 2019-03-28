---
title: "Configure Smart contacts list in Skype for Business clients"
ms.reviewer: 
ms.author: chucked
author: chuckedmonson
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4eecb5f7-3ef7-4582-a6cb-9f4aa068338d
description: "Summary: Learn how to turn on the Smart contacts list feature in the Skype for Business client."
---

# Configure Smart contacts list in Skype for Business clients

**Summary:** Learn how to turn on the Smart contacts list feature in the Skype for Business client.

The Smart contacts list feature allows automatic population of contact lists for your end users. Upon first using Skype for Business, your users will automatically see their manager and other people on their team. This feature is turned on by default for Office 365 users, but you must explicitly enable this feature for your on-premises users by configuring the client policy setting.

Keep the following in mind when configuring this feature:

- Users, up to 13, are automatically added to the Smart contacts list in the following order:

  1. Manager

  2. Directs in alphabetical order

  3. Peers in alphabetical order

- The first time a user logs in, a new group, named My Group, is created. The group is automatically populated with people in the user's AD group relationship based on the user alias populated in the Manager field. Note that changes to the AD group membership do not cause updates to My Group after it is initially populated. If a user deletes a contact or the group, neither the contact nor the group are re-created. 

- If auto tagging is turned on, contacts in the list will be tagged for presence changes. Auto tagging is turned on by default, but you can choose to turn it off. 

- All new users in the group will be informed that they have been added to the contacts list. Users can manually add new members to their My Group or to other groups of their choosing.

- This feature works only for users who are signing in for the first time. If a user has previously signed in from any device--including, for example, any mobile device or a Mac--the feature is not enabled for that user.

## Configure Smart contacts list

To enable the Smart contacts list feature for your users, you will need to perform the following steps: 

- Create a new CsClientPolicy entry and add it to the global client policy. 

- Make sure that Address Book Search is configured for Web Search only.

### Create a policy entry to enable Smart contacts list

To create a policy entry to enable the Smart contacts list feature, use the [New-CsClientPolicyEntry](https://docs.microsoft.com/powershell/module/skype/new-csclientpolicyentry?view=skype-ps) cmdlet with the EnableClientAutoPopulateWithTeam option as follows:

```
$x=New-CsClientPolicyEntry -Name EnableClientAutoPopulateWithTeam -Value $True
```

Next, use the [Set-CsClientPolicy](https://docs.microsoft.com/powershell/module/skype/set-csclientpolicy?view=skype-ps) cmdlet to write the changes to the global policy as follows:

```
Set-CsClientPolicy -Identity Global -PolicyEntry @{Add=$x}
```

You can optionally create a policy to turn off auto tagging as follows:

```
$x=New-CsClientPolicyEntry -Name TagContactsInClientAutoPopulatedGroup -Value $False
Set-CsClientPolicy -Identity Global -PolicyEntry @{Add=$x}
```

You must also set the AddressBookAvailability parameter for the corresponding policy to WebSearchOnly. For more information, see [Set-CsClientPolicy](https://docs.microsoft.com/powershell/module/skype/set-csclientpolicy?view=skype-ps). 

### Troubleshoot

If Smart contacts list is not functioning as expected, check the following:

- Validate the configuration. 

- Confirm that the AD organization information is populated.

- Collect Skype for Business client logs on a new user for further analysis.

- Confirm that the Skype for Business client UI is not displaying a message that it cannot connect to the Address Book. To confirm Address Book connectivity, perform a search for a user in the Skype for Business client search bar.

- AD DS replication issues could cause contacts to be unresolved when a user first signs in to Skype for Business.


