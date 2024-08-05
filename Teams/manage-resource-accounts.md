---
title: Manage resource accounts for service numbers
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: roykuntz, jastark
ms.date: 05/21/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
  - seo-marvel-apr2020
description: In this article, you'll learn how to create, edit, and manage resource accounts for service numbers in Microsoft Teams.
---

# Manage resource accounts for service numbers

[!INCLUDE [set-up-resource-account-steps](./includes/set-up-resource-account-steps.md)]

## Next steps

Once you complete the resource account setup and assign a phone number if needed, you're ready to use the resource account with an Auto attendant or Call queue.

To learn more, see the following references:

- [Cloud Auto attendant](create-a-phone-system-auto-attendant.md)
- [Cloud Call queue](create-a-phone-system-call-queue.md)

You can edit the resource account **Display name** and **Resource account** type using the **Edit** option. Select **Save** when you're done.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

To switch the licenses on your existing resource account from a **Teams Phone Standard** license to a **Microsoft Teams Phone Resource Account** license, you'll need to acquire the **Microsoft Teams Phone Resource Account** license, and then follow the steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a **Teams Phone Standard** license and assign the **Microsoft Teams Phone Resource Account** license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the **Microsoft Teams Phone Resource Account** license and remove the broken resource account.

## Skype For Business Server 2019

For resource accounts homed on Skype For Business Server 2019 that can be used with cloud Call queues and cloud Auto attendants, see [Plan Cloud Call queues](/SkypeforBusiness/hybrid/plan-call-queue) or [Plan Cloud Auto attendants](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant). Hybrid implementations (numbers homed on Direct Routing) are configured using the [New-CsHybridApplicationEndpoint](/powershell/module/skype/new-cshybridapplicationendpoint) cmdlet on an on-premises Skype for Business Server 2019 server.

The application IDs that you need to use while creating the application instances are:

- **Auto Attendant:** ce933385-9390-45d1-9512-c8d228074e07
- **Call Queue:** 11cd3e2e-fccb-42ad-ad00-878b93575e07

> [!NOTE]
> If you want the Call queue or Auto attendant to be searchable by Skype For Business Server 2019 users, you should create your resource accounts on Skype For Business Server 2019, since online resource accounts are not synced down to Active Directory. When DNS SRV records for `sipfederationtls` resolve to Skype for Business Server 2019, then resource accounts **must** be created on Skype For Business Server 2019 using SfB Management shell and synchronized to Microsoft Entra ID.

For hybrid implementations with Skype for Business Server:

- [Plan Cloud Auto attendants](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant).
- [Plan Cloud Call queues](/SkypeforBusiness/hybrid/plan-call-queue).
- [Configure on-premises resource accounts](/SkypeForBusiness/hybrid/configure-onprem-ra).

## Delete a resource account

Make sure you dissociate the telephone number from the resource account before deleting it, to avoid getting your phone number stuck in pending mode.

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
2. Expand **Voice**, and then select **Resource accounts** page.
3. Select the resource account to which you want to assign a phone number, and then select **Assign/unassign**.
4. Select the **X** on the assigned Auto attendant or Call queue.
5. Select the **Save** button.

After you do that, you can delete the resource account in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), under the [**Users**](https://go.microsoft.com/fwlink/p/?linkid=834822) tab.

## Hide resource accounts from Teams users

You may want to hide certain resources accounts from Teams users. For example, you may want to prevent Teams users from directly calling a Call queue and bypassing the Auto attendant where the hours of operation are configured.

[Information barriers](information-barriers-in-teams.md) are used to hide the resource accounts.  Review the information barriers documentation to understand the possible impacts before proceeding with the steps below.

### Required subscriptions and permissions

To access and use information barriers, your organization must have one of the following subscriptions or add-ons:

- Microsoft 365 E5/A5 subscription (paid or trial version).
- Office 365 E5/A5/A3/A1 subscription (paid or trial version).
- Office 365 Advanced Compliance add-on.
- Microsoft 365 E3/A3/A1 subscription + the Microsoft 365 E5/A5 Compliance add-on.
- Microsoft 365 E3/A3/A1 subscription + the Microsoft 365 E5/A5 Insider Risk Management add-on.

> [!NOTE]
> If you already have [Exchange Online](/exchange/address-books/address-book-policies/address-book-policies) address book policies configured, they must be removed before proceeding with the steps below.
>
> All the steps below are performed by the Tenant Global Administrator.
>
> These instructions assume there are no other information barriers configured.

#### Teams admin center

1. Sign into the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851).
2. In the left-rail menu, expand **Teams**.
3. Select **Teams settings**.
4. Scroll down to **Search by name**.
5. Turn on the toggle, and save the change.

For more information on this option, see [Limit who users can see when searching the directory in Teams](teams-scoped-directory-search.md).

#### Compliance - Auditing

1. Sign into the [Microsoft Purview compliance portal](https://compliance.microsoft.com/).
2. In the left navigation pane, select **Audit**.
3. If auditing is turned off, the following banner is displayed:

     :::image type="content" source="/microsoft-365/media/AuditingBanner.png" alt-text="Screenshot showing audit banner if auditing is not enabled."lightbox="/microsoft-365/media/AuditingBanner.png":::
  
4. Select the **Start recording user and admin activity**.

For more information on auditing, see [Set up Audit (Standard) in Microsoft 365](/microsoft-365/compliance/audit-standard-setup).

#### Segmenting Data

The Resource Accounts that shouldn't be called directly need to be segmented and easily identifiable. This can be done by making them members of a particular group or by some unique information in their user profile such as:

- Company
- User principal name
- Location
- Department
- Usage location
- Mail nickname (Alias)
- Physical delivery office name (Office)
- Postal code
- Proxy address (Email Address)
- Street address
- Target address (ExternalEmailAddress)
- Mail (WindowsEmailAddress)
- Description

In the example steps below, the `Department` field is used.

For more information on segmenting users, see [Identify segments](/microsoft-365/compliance/information-barriers-policies).

#### Microsoft admin center

1. Sign into the [Microsoft 365 Admin Center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the left navigation pane, select **Active Users**.
3. Select the first Resource Account to block direct calls to.
4. Select **Manage contact information** in the right pane.
5. Replace the contents of the `Department` field with a unique word or acronym that isn't used as a department name. For example, `DNC`.
6. Save changes.
7. Repeat for each Resource Account that needs to be blocked from receiving direct calls.

#### Compliance - Information Barriers

1. Sign into the [Microsoft Purview compliance portal](https://compliance.microsoft.com/).
2. In the left navigation pane, select **Information barriers** > **Segments**.
3. Select **New segment**.
4. Enter a name for the segment, and select **Next**. For example, `Uncallable Resource Accounts`.
5. Select **+ Add**, and then **Department**.
6. Enter the unique word or acronym used in Microsoft admin center step 5 above. For example, `DNC`.
7. Select **Next**, and then **Submit**.
8. Select **New segment**.
9. Enter a name for the segment, and select **Next**. For example, `Callable Users`.
10. Select **+ Add**, and then **Department**.
11. Select the **Equal** drop-down, and select **Not equal to**.
12. Enter the unique word or acronym used in Microsoft admin center step 5 above. For example, `DNC`.
13. Select **Next**, and then **Submit**.
14. In the left navigation pane, select **Information barriers** > **Policies**.
15. Select **Create policy**.
16. Enter a name for the policy, and select **Next**. For example, `Uncallable Resource Accounts`.
17. Select **+ Choose segment**, add the segment created in step 9 above, and select **Next**. For example, `Callable Users`.
18. Select **Blocked** from the **Communication and collaboration** drop-down.
19. Select **+ Choose segment**, add the segment created in step 4 above, and select **Next**. For example, `Uncallable Resource Accounts`.
20. Set the policy to **On**, select **Next**, and then **Submit**.
21. Select **Create policy**.
22. Enter a name for the policy, and select **Next**. For example, `Callable Users`.
23. Select **+ Choose segment**, add the segment created in step 4, and select **Next**.
24. Select **Blocked** from the **Communication and collaboration** drop-down.
25. Select **+ Choose segment**, add the segment created in step 9 above, and select **Next**.
26. Set the policy to **On**, select **Next**, and then **Submit**.
27. In the left navigation pane, select **Information barriers** > **Policy application**.
28. Select **Apply all policies**.

> [!NOTE]
> It may take 30 minutes or more for the policy to be applied.  
>
> Once the status shows completed, go into Teams Client and try to search for the Resource Accounts that were blocked. It may be necessary to clear the Teams cache.  
>
> If a Teams user has saved the Resource Account as a contact, they will no longer be able to call it.
