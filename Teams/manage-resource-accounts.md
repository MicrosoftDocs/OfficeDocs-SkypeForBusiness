---
title: Manage resource accounts in Teams
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.reviewer: jastark, wasseemh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
  - seo-marvel-apr2020
description: In this article, you'll learn how to create, edit, and manage resource accounts in Microsoft Teams.
---

# Manage resource accounts in Microsoft Teams

[!INCLUDE [set-up-resource-account-steps](./includes/set-up-resource-account-steps.md)]

## Next steps

Once you've completed the resource account setup and assigning a service number if needed, you're ready to use the resource account with an auto attendant or call queue.

See the following references to learn more:

- [Cloud auto attendant](create-a-phone-system-auto-attendant.md)
- [Cloud call queue](create-a-phone-system-call-queue.md)

You can edit the resource account **Display name** and **Resource account** type using the **Edit** option. Select **Save** when you're done.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

To switch the licenses on your existing resource account from a **Teams Phone Standard** license to a **Microsoft Teams Phone Resource Account** license, you'll need to acquire the **Microsoft Teams Phone Resource Account** license, and then follow the steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a **Teams Phone Standard** license and assign the **Microsoft Teams Phone Resource Account** license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the **Microsoft Teams Phone Resource Account** license and remove the broken resource account.

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

   [Configure on-premises resource accounts](/SkypeForBusiness/hybrid/configure-onprem-ra)

## Delete a resource account

Make sure you dissociate the telephone number from the resource account before deleting it, to avoid getting your service number stuck in pending mode.

After you do that, you can delete the resource account in the Microsoft 365 admin center, under the **Users** tab.

To disassociate a Direct Routing telephone number from the resource account, use the following cmdlet:

```powershell
Remove-CsPhoneNumberAssignment -Identity <Resource Account Object ID> -PhoneNumber <assigned phone number> -PhoneNumberType DirectRouting
```

## Hide resource accounts from Teams users

You may want to hide certain resources accounts from Teams users. For example, you may want to prevent Teams users from directly calling a call queue and bypassing the auto attendant where the hours of operation are configured.

[Information Barriers](information-barriers-in-teams.md) are used to hide the resource accounts.  Review the Information Barriers documentation to understand the possible impacts before proceeding with the steps below.

### Required subscriptions and permissions 

To access and use information barriers, your organization must have one of the following subscriptions or add-ons: 

-	Microsoft 365 E5/A5 subscription (paid or trial version)
-	Office 365 E5/A5/A3/A1 subscription (paid or trial version)
-	Office 365 Advanced Compliance add-on
-	Microsoft 365 E3/A3/A1 subscription + the Microsoft 365 E5/A5 Compliance add-on
- Microsoft 365 E3/A3/A1 subscription + the Microsoft 365 E5/A5 Insider Risk Management add-on

[!NOTE]
> If you already have [Exchange Online](/exchange/address-books/address-book-policies/address-book-policies) address book policies configuredthese must be removed before proceeding with the steps below.   
> 
>	All the steps below are performed by the Tenant Global Administrator credentials. 
>	
> These instructions assume there are no other Information Barriers configured.

#### Teams Admin Center

Go to Teams -> Teams settings and scroll down to "Search by name" and turn on the toggle and save the change.

For more information on this option refer to: [Limit who users can see when searching the directory in Teams](teams-scoped-directory-search)

#### Compliance - Auditing

Go to [Microsoft Purview compliance portal](https://compliance.microsoft.com/)

1. In the left navigation pane, click Audit 
2. If auditing is turned off, the following banner will be displayed 
 
     :::image type="content" source="/microsoft-365/media/AuditingBanner.png" alt-text="Screenshot showing audit banner if auditting is not enabled":::
  
3. Click the Start recording user and admin activity 

For more information on auditing refer to: [Set up Audit (Standard) in Microsoft 365](/microsoft-365/compliance/audit-standard-setup?view=o365-worldwide&preserve-view=true)

#### Segmenting Data

The Resource Accounts that shouldn't be called directly need to be segmented / easily identifiable.  This can be done by making them members of a particular group or by some unique information in their user profile such as: 

-	Company
-	User principal name
-	Location
-	Department
-	Usage location
-	Mail nickname (Alias)
-	Physical delivery office name (Office)
-	Postal code
-	Proxy address (Email Address)
-	Street address
-	Target address (ExternalEmailAddress)
-	Mail (WindowsEmailAddress)
-	Description

In the example steps below, the Department field will be used. 

For more information on segmenting users refer to: [Identify segments](/microsoft-365/compliance/information-barriers-policies?view=o365-worldwide#identify-segments&preserve-view=true)

#### Microsoft Admin Center

Go to: [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?#/homepage)

1. In the left navigation pane, click Active Users 
2. Click on the first Resource Account to block direct calls to 
3. Click on Manage contact information in the right pane 
4. Replace the contents of the Department field with a unique word or acronym that is not used as a department name. For example: DNC 
5. Save changes 
6. Repeat for each Resource Account that needs to be blocked from receiving direct calls 

#### Compliance - Information Barriers

Go to [Microsoft Purview compliance portal](https://compliance.microsoft.com/)

1. In the left navigation pane, click **Information barriers -> Segments**
2. Click **New segment*
3. Enter a name for the segment and click **Next**.  For example: Uncallable Resource Accounts 
4. Click **+Add** and then **Department**
5. Enter the unique word or acronym used in Microsoft Admin Center step 4 above.  For example: DNC 
6. Click **Next** and then **Submit** and Done 
7. Click **New segment** 
8. Enter a name for the segment and click **Next**.  For example: Callable Users 
9. Click **+Add** and then Department 
10. Click on the **Equal** drop-down and select **Not equal to**
11. Enter the unique word or acronym used in Microsoft Admin Center step 4 above.  For example: DNC 
12. Click **Next** and then **Submit* and Done 
13. In the left navigation pane, click **Information barriers -> Policies** 
14. Click **Create policy** 
15. Enter a name for the policy and click **Next**.  For example: Uncallable Resource Accounts 
16. Click **+Choose segment** and add the segment created in step 8 above and click **Next** 
17. Select **Blocked** from the **Communication and collaboration** drop-down 
18. Click **+Choose segment** and add the segment created in step 3 above and click **Next** 
19. Set the policy to **On** and click **Next** and then **Submit**
20. Click **Create policy** 
21. Enter a name for the policy and click **Next**.  For example: Callable Users 
22. Click **+Choose segment** and add the segment created in step 3 and click **Next **
23. Select **Blocked** from the **Communication and collaboration** drop-down 
24. Click **+Choose segment** and add the segment created in step 8 above and click **Next** 
25. Set the policy to **On** and click **Next** and then **Submit** 
26. In the left navigation pane, click **Information barriers -> Policy application** 
27. Click on **Apply all policies** 

[!NOTE]
> It may take 30 minutes or more for the policy to be applied.  
> 
> Once the status shows completed go into Teams Client and try to search for the Resource Accounts that were blocked.  It may be necessary to clear the Teams cache.  
> 
> If a Teams user has saved the Resource Account as a contact they will no longer be able to call it
