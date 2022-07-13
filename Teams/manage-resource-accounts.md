---
title: "Manage resource accounts in Teams"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark, wasseemh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
  - seo-marvel-apr2020
description: "In this article, you will learn how to create, edit and manage resource accounts in Microsoft Teams."
---

# Manage resource accounts in Microsoft Teams

[!INCLUDE [set-up-resource-account-steps](./includes/set-up-resource-account-steps.md)]

## Next steps

Once you've completed the resource account setup and assigning a service number if needed, you're ready to use the resource account with an auto attendant or call queue.

See the following references to learn more:

- [Cloud auto attendant](create-a-phone-system-auto-attendant.md)
- [Cloud call queue](create-a-phone-system-call-queue.md)

You can edit the resource account **Display name** and **Resource account** type using the **Edit** option. Click **Save** when you are done.

## Change an existing resource account to use a Teams Phone Resource Account license

If you decide to switch the licenses on your existing resource account from a **Teams Phone Standard** license to a **Microsoft Teams Phone Resource Account** license, you'll need to acquire the free **Teams Phone Resource Account** license, and then follow the steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a full Teams Phone Standard License and assign the **Microsoft Teams Phone Resource Account** license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the **Microsoft Teams Phone Resource Account** license and remove the broken resource account.

## Skype For Business Server 2019

For resource accounts homed on Skype For Business Server 2019 that can be used with cloud call queues and cloud auto attendants, see [Plan Cloud call queues](/SkypeforBusiness/hybrid/plan-call-queue) or [Plan Cloud auto attendants](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant). Hybrid implementations (numbers homed on Direct Routing) are configured using the [New-CsHybridApplicationEndpoint](/powershell/module/skype/new-cshybridapplicationendpoint) cmdlet on an on-premises Skype for Business Server 2019 server.

The application IDs that you need to use while creating the application instances are:

- **Auto Attendant:** ce933385-9390-45d1-9512-c8d228074e07
- **Call Queue:** 11cd3e2e-fccb-42ad-ad00-878b93575e07

> [!NOTE]
> If you want the call queue or auto attendant to be searchable by Skype For Business Server 2019 users, you should create your resource accounts on Skype For Business Server 2019, since online resource accounts are not synced down to Active Directory. When DNS SRV records for sipfederationtls resolve to Skype for Business Server 2019, then resource accounts **must** be created on Skype For Business Server 2019 using SfB Management shell and synchronized to Azure AD.

For implementations that are hybrid with Skype for Business Server:

   [Plan Cloud auto attendants](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant)

   [Plan Cloud call queues](/SkypeforBusiness/hybrid/plan-call-queue)

   [Configure on-prem resource accounts](/SkypeForBusiness/hybrid/configure-onprem-ra)

## Delete a resource account

Make sure you dissociate the telephone number from the resource account before deleting it, to avoid getting your service number stuck in pending mode.

After you do that, you can delete the resource account in the Microsoft 365 admin center, under the Users tab.

To disassociate a direct routing telephone number from the resource account, use the following cmdlet:

```powershell
Remove-CsPhoneNumberAssignment -Identity <Resource Account Object ID> -PhoneNumber <assigned phone number> -PhoneNumberType DirectRouting
```
