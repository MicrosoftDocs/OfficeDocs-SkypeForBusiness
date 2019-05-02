---
title: "Manage resource accounts in Teams"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: jastark, wasseemh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-voice
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords:
- ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
description: "Learn about managing resource accounts in Microsoft Teams"
---

# Manage resource accounts in Microsoft Teams

A resource account is also known as a disabled user object in Azure Active Directory, and can be used to represent resources in general. In Exchange it might be used to represent conference rooms, for example, and allow them to have a phone number. A resource account can be homed in Microsoft 365 or on premises using Skype for Business server, and these accounts are created using Powershell commands.

In Microsoft Teams or Skype for Business Online, each call queue or auto attendant is required to have an associated resource account. Whether a resource account needs an assigned phone number will depend on the intended use of the associated call queue or auto attendant. Refer to the articles on call queues and auto attendants linked at the bottom of this article before assigning a phone number to a resource account.

> [!NOTE]
> This article applies to both Microsoft Teams and Skype for Business Online.

## Prerequisites to assign a phone number to a resource account

To get started it's important to remember a few things:
  
- An auto attendant or call queue is required to have an associated resource account. See [Manage resource accounts in Teams](manage-resource-accounts.md) for details on resource accounts.
- If you plan to assign a Direct Routing number, you need to acquire and assign the following licenses to your resource accounts \(Office 365 Enterprise E1, E3 or E5, with the Phone System add-on\).
- If you are assigning a Microsoft service number instead, you need to acquire and assign the following licenses to your resource account \(Office 365 Enterprise E1, E3 or E5, with the Phone System add-on and a Calling Plan\).
- You only need to license the resource accounts with a phone number assigned to them. In a nested auto attendant or call queue, you do not need to license the rest of the auto attendants or call queues if they do not have phone numbers associated with them

> [!NOTE] 
> Direct Routing service numbers for auto attendant and call queues is supported for Microsoft Teams users and agents only at the moment.

> [!NOTE] 
> Microsoft is working on an appropriate licensing model for applications such as Cloud auto attendants and call queues, for now you need to use the user-licensing model.
    
> [!NOTE]
> To redirect calls to people in your organization who are Online, they must have a **Phone System** license and be enabled for Enterprise Voice or have Office 365 Calling Plans. See [Assign Microsoft Teams licenses](assign-teams-licenses.md). To enable them for Enterprise Voice, you can use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`
  
- You can assign a Direct Routing Hybrid number to your resource account.  See [Plan Direct Routing](direct-routing-plan.md) for details.
- For Microsoft calling plans, you can only assign toll and toll-free service phone numbers that you got in the **Microsoft Teams admin center** or ported from another service provider to a resource account. To get and use toll-free service numbers, you need to set up Communications Credits.

> [!NOTE]
> User (subscriber) phone numbers can't be assigned to a resource account. Only service toll or toll-free phone numbers can be used.

To assign a phone number to a resource account, you will need to get or port your existing toll or toll-free service numbers. After you get the toll or toll-free service phone numbers, they will show up in **Microsoft Teams admin center** > **Voice** > **Phone numbers**, and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see [Getting service phone numbers](https://docs.microsoft.com/SkypeForBusiness/what-is-phone-system-in-office-365/getting-service-phone-numbers?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json) or if you want to transfer an existing service number, see [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md).
  
> [!NOTE]
> If you are outside the United States, you can't use the Microsoft Teams admin center to get service numbers. Go to [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) instead to see how to do it from the outside of the United States.

## Create a resource account in Microsoft Teams admin center

In Microsoft Teams admin center, navigate to **Org-wide settings** > **Resource accounts**. 

![asd](media/r-a-master.png)

![number 1](media/sfbcallout1.png)

To create a new resource account click **+ New account**. In the pop-up, fill out the display name and user name for the resource account (the domain name should populate automatically) then click **Save**.

![resource account](media/res-acct.png)

Next, you will  need to apply a license to the resource account, as described in [Assign licenses to users in Office 365 for business](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide)

![number 3](media/sfbcallout3.png) Once you've created the resource account and assigned the license, you can click on **Assign/Unassign** to assign a phone number to the resource account, or assign the resource account to an auto attendant or call queue that already exists. If your call queue or auto attendant still needs to be created, you can link the resource account while you create it. Click **Save** when you are done.

![resource account assign](media/r-a-assign.png)

![number 2](media/sfbcallout2.png) You can edit the resource account display name using the **Edit** option.  Click **Save** when you are done.
![edit resource account](media/r-a-edit.png)

## Create a resource account in Powershell

For Microsoft calling plans, you can only assign toll and toll-free service phone numbers that you got in the **Microsoft Teams admin center** or ported from another service provider to a resource account. To get and use toll-free service numbers, you need to set up Communications Credits.

Depending on whether your resource account is located online or on premises, you would need to connect to the appropriate Powershell prompt with Admin privileges. 
- The following Powershell cmdlet examples presume the resource account is homed online using [New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-CsOnlineApplicationInstance?view=skype-ps) to create a resource account that is homed online.

- For resource accounts homed on-premises in Skype For Business Server 2019 that can be used with Cloud Call Queues and Cloud Auto Attendants, see [Configure Cloud Call Queues](/skypeforbusiness/hybrid/configure-call-queue.md) or [Configure Cloud Auto Attendants](/skypeforbusiness/hybrid/configure-cloud-auto-attendant.md). Hybrid implementations (numbers homed on Direct Routing) will use [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps).

The application ID's that you need to use while creating the application instances are:
- **Auto Attendant:** ce933385-9390-45d1-9512-c8d228074e07
- **Call Queue:** 11cd3e2e-fccb-42ad-ad00-878b93575e07

> [!NOTE]
> If you want the call queue or auto attendant to be searchable by on-premise users, you should create your resource accounts on-premise, since online resource accounts are not synced down to Active Directory.

1. To create a resource account online for use with an auto attendant, use the following command.  

``` Powershell
New-CsOnlineApplicationInstance -UserPrincipalName testra1@contoso.com -ApplicationId “ce933385-9390-45d1-9512-c8d228074e07” -DisplayName "Resource account 1"
```

2. You will not be able to use the resource account until you apply a license to it. For how to apply a license to an account in the O365 admin center, see [Assign licenses to users in Office 365 for business](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide#assign-licenses-to-one-user as well as [Assign Skype for Business licenses](https://docs.microsoft.com/en-us/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses) .

3. (Optional) Once the correct license is applied to the resource account you can  set a phone number to the resource account as shown below. Not all resource accounts will require a phone number. If you did not apply a license to the resource account, the phone number assignment will fail.

``` Powershell
Set-CsOnlineVoiceApplicationInstance -Identity testra1@contoso.com
 -TelephoneNumber +14255550100
Get-CsOnlineTelephoneNumber -TelephoneNumber +14255550100
```

See [Set-CsOnlineVoiceApplicationInstance](https://docs.microsoft.com/powershell/module/skype/set-csonlinevoiceapplicationinstance?view=skype-ps) for more details on this command.

> [!NOTE]
> It's easiest to set the online phone number using the Microsoft Teams admin center, as described previously.

## Manage Resource account settings in Microsoft Teams admin center

To manage Resource account settings in Microsoft Teams admin center, navigate to **Org-wide settings**  > **Resource accounts**, select the resource account you need to change settings for, and then click on the **Edit** button. in the **Edit resource account** screen, you will be able to change these settings:

- **Display name** for the account
- Call queue or auto attendant that uses the account
- Phone number assigned to the account

When finished, click on **Save**.

## Delete a resource account

Make sure you dissociate the telephone number from the resource account before deleting it, to avoid getting your service number stuck in pending mode. You can do that using the following commandlet: 

``` Powershell
Set-csonlinevoiceapplicationinstance -identity <Resource Account oid> -TelephoneNumber $null
```
                
Once you do that, you can delete the resource account from the O365 admin portal, under Users tab.


## Related Information

For implementations that are hybrid with Skype for Business Server:

[Plan Cloud auto attendants](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant)

[Configure Cloud auto attendants](/SkypeForBusiness/hybrid/configure-cloud-auto-attendant)

For implementations in Teams or Skype for Business Online:

[What are Cloud auto attendants?](what-are-phone-system-auto-attendants.md)

[Set up a Cloud auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant)

[Small business example - Set up an auto attendant](https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa)

[Create a Cloud call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/create-a-phone-system-call-queue)

[New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)
