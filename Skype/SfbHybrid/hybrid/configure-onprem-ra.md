---
ms.date: 06/22/2018
title: "Configure a resource account in Skype for Business Server 2019"
ms.author: serdars
author: MicrosoftHeidi
manager: serdars 
ms.reviewer: wasseemh
ms.audience: ITPro
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.collection: 
description: "Set up a resource account for Skype for Business Server 2019."
---

# Configure resource accounts

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Skype for Business Server 2019 hybrid implementations only use Cloud services provided by Phone System for unified messaging and don't integrate with Exchange Online. In Skype for Business Server 2019, you're now able to use the Cloud call queues and auto attendants described in [Here's what you get with Phone System in Microsoft 365 or Office 365](/MicrosoftTeams/here-s-what-you-get-with-phone-system).

To use a Phone System auto attendant or call queue with Skype for Business Server 2019, you'll need to create resource accounts that act as application endpoints and can be assigned phone numbers, then use the online Teams admin center to configure the call queue or auto attendant. This resource account can be homed online (see [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts) to create resource accounts homed online) or on premises as described in this article. Typically you'll have multiple Phone System auto attendant or call queue nodes, each of which is mapped to a resource account, which can be homed online or in Skype for Business Server 2019.

If you have an existing Exchange UM auto attendant and call queue system, before you switch to Exchange Server 2019 or Exchange online, you'll need to manually record the details as described below and then implement a new system using the Teams admin center.

## Overview

If your Phone System auto attendant or call queue will need a service number, the various dependencies can be met in the following sequence:

1. Obtain a service number.
2. Obtain a free [Microsoft Teams Phone Resource Account license](/MicrosoftTeams/teams-add-on-licensing/virtual-user) or a paid Phone System license to use with the resource account.
3. Create the resource account. An auto attendant or call queue is required to have an associated resource account.
4. Wait for an active directory sync between online and on premises.
5. Assign the Phone System license to the resource account.
6. Assign a service number to the resource account.
7. Create a Phone System call queue or auto attendant.
8. Associate the resource account with an auto attendant or call queue: (New-CsApplicationInstanceAssociation).

If the auto attendant or call queue is nested under a top level auto attendant, the associated resource account only needs a phone number if you want multiple points of entry into the structure of auto attendants and call queues.

To redirect calls to people in your organization who are homed Online, they must have a **Phone System** license and be enabled for Enterprise Voice or have Microsoft 365 or Office 365 Calling Plans. See [Assign Microsoft Teams licenses](/MicrosoftTeams/assign-teams-licenses). To enable them for Enterprise Voice, you can use Windows PowerShell. For example, run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`

If the Phone system auto attendant or call queue you're creating will be nested and won't  need a phone number, the process is:

1. Create the resource account  
2. Wait for an active directory sync between online and on premises
3. Create a Phone System auto attendant or call queue
4. Associate the resource account with a Phone System auto attendant or call queue

## Create a resource account with a phone number

Creating a resource account that uses a phone number would require performing the following tasks in the following order:

1. Port or get a toll or toll-free service number. The number can't be assigned to any other voice services or resource accounts.

   Before you assign a phone number to a resource account, you'll need to get or port your existing toll or toll-free service numbers. After you get the toll or toll-free service phone numbers, they'll show up in **Microsoft Teams admin center** > **Voice** > **Phone numbers**, and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see [Getting service phone numbers](/MicrosoftTeams/getting-service-phone-numbers) or if you want to transfer an existing service number, see [Transfer phone numbers to Teams](/MicrosoftTeams/phone-number-calling-plans/transfer-phone-numbers-to-teams).

   If you're outside the United States, you can't use the Microsoft Teams admin center to get service numbers. Go to [Manage phone numbers for your organization](/MicrosoftTeams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization) instead to see how to do it from the outside of the United States.

2. Buy a Phone System license. See:  
   - [Microsoft Teams Phone Resource Account license](/MicrosoftTeams/teams-add-on-licensing/virtual-user)
   - [Office 365 Enterprise E1 and E3](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e1-e3)
   - [Office 365 Enterprise E5](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e5-with-audio-conferencing)
   - [Office 365 Enterprise E5 Business Software](https://products.office.com/business/office-365-enterprise-e5-business-software)

3. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each Phone System auto attendant or call queue, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -ApplicationID <GUID> -DisplayName appinstance01 -SipAddress sip:appinstance01@contoso.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    For more information, see [New-CsHybridApplicationEndpoint](/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps).

4. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premises, or force a sync and proceed to online configuration of Phone System auto attendant or call queues. To force a sync, run the following command on the computer running Azure AD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

    Note-at this point, the account may have synced, but provisioning may not be complete.  Check the output of [Get-CsOnlineApplicationEndpoint](/powershell/module/skype/get-csonlineapplicationendpoint).  If the synced endpoint hasn't completed provisioning yet, then it will not appear here.  You can check the status of the provisioning requests in the Microsoft 365 portal under [Teams Setup Status](https://admin.microsoft.com/AdminPortal/Home#/teamsprovisioning). This provisioning phase can take up to 24 hours.

5. Assign the **Microsoft Teams Phone Resource Account** license or **Teams Phone Standard** license to the resource account. See [Assign Microsoft Teams add-on licenses](/MicrosoftTeams/teams-add-on-licensing/assign-teams-add-on-licenses) and [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

   If you're assigning a phone number to a resource account you can now use the cost-free **Microsoft Teams Phone Resource Account** license. This provides Phone System capabilities to phone numbers at the organizational level, and allows you to create auto attendant and call queue capabilities.

6. Assign the service number to the resource account. Use the `Set-CsHybridApplicationEndpoint` command to a assign a phone number (with the -LineURI option) to the resource account.

    ``` Powershell
    Set-CsHybridApplicationEndpoint -Identity appinstance01@contoso.com -LineURI tel:+14255550100
    ```

    For more information, see [Set-CsHybridApplicationEndpoint](/powershell/module/skype/set-cshybridapplicationendpoint?view=skype-ps).

    To assign a Direct Routing or hybrid number to  a resource account, use the following cmdlet:

   ``` Powershell
   Set-CsOnlineApplicationInstance -Identity appinstance01@contoso.com -OnpremPhoneNumber +14250000000
   ```

   The resource account will need an assigned phone number if it will be assigned to a top level auto attendant or call queue. User (subscriber) phone numbers can't be assigned to a resource account, only service toll or toll-free phone numbers can be used.

     You can assign a Direct Routing or hybrid number to your resource account. For details, see [Plan Direct Routing](/MicrosoftTeams/direct-routing-plan) and [Plan Cloud auto attendants](plan-cloud-auto-attendant.md).

     > [!NOTE]
     > Direct Routing service numbers assigned to resource accounts for auto attendant and call queues are supported for Microsoft Teams users and agents only.

7. Create the Phone System auto attendant or call queue. See one of the following:

   - [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant)
   - [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue)  

8. Associate the resource account with the Phone System auto attendant or call queue you chose previously.

## Create a resource account without a phone number

This section discusses creating a resource account that is homed on premises. Creating a resource account that is homed online is discussed at [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts).

These steps are necessary whether you're creating a brand new Phone System auto attendant or call queue structure, or rebuilding a structure originally created in Exchange UM.

Log in to the Skype for Business front end server and run the following PowerShell cmdlets:

1. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each Phone System auto attendant or call queue, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName appinstance01 -SipAddress sip:appinstance01@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    For more information, see [New-CsHybridApplicationEndpoint](/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps).

2. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premises, or force a sync and proceed to online configuration of Phone System auto attendant or call queues. To force a sync you would run the following command on the computer running Azure AD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

3. Create the Phone System auto attendant or call queue. See one of the following:
   - [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant)
   - [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue)  
4. Associate the resource account and the Phone System auto attendant or call queue you chose previously.

## Test the implementation

The best way to test the implementation is to call the number configured for a Phone System auto attendant or call queue and connect to one of the agents or menus. You can also quickly place a test call by using the **Test button** in the admin center Action pane. If you want to make changes to a Phone System auto attendant or call queue, select it and then in the Action pane select **Edit**. 

> [!TIP]
> If your resource account has difficulties with being assigned to a call queue or auto attendant, see [Known issues for Microsoft Teams](/MicrosoftTeams/Known-issues#phone-system) and the [How to fix my hybrid application instances](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521) section in the Microsoft Teams Blog.

## Moving an Exchange UM auto attendant or call queue to Phone System

Migration from Exchange UM to Phone System will require recreating the call queue and auto attendant structure, directly migrating from one to the other isn'g supported. To re-implement a set of call queues and auto attendants:

1. Get a list of all Exchange UM auto attendants and call queues by running the following command on the Exchange 2013 or 2016 system while logged in as admin:

    ``` Powershell
    Get-UMAutoAttendant | Format-List
    ```

2. For each listed Exchange UM call queue or auto attendant, note its place in the structure, settings, and get copies of associated sound or text-to-speech files (the guid in the output will be the name of a folder where the files are stored). You can get these details by running the command:

    ``` Powershell
    Get-UMAutoAttendant -Identity MyUMAutoAttendant
    ```

    See [Get-UMAutoAttendant](/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) for more details on this command. A complete list of options you might need to capture is at [UMAutoAttendant members](/previous-versions/office/exchange-server-api/ff340649(v=exchg.150)) but the most important options to note down are:

    - Business hours
    - Non-business hours
    - Language
    - Holiday schedule

3. Create new on-premises endpoints as previously described.
   Assign the top-level auto attendant a temporary number for testing purposes.

4. Configure a Phone System auto attendant or call queue that uses the endpoints as previously described.

5. Test the Phone System auto attendant or call queue.

6. Reassign the phone number linked to the Exchange UM call queue or auto attendant to the corresponding Phone System auto attendant or call queue.  

   At this point, if you have already migrated UM Voicemail, you should be in a position to migrate to Exchange Server 2019.

## See Also

[Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue)

[What are Cloud auto attendants?](/MicrosoftTeams/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant)  

[Plan Cloud auto attendants](plan-cloud-auto-attendant.md)

[Plan Cloud call queues](plan-call-queue.md)

[Plan Cloud Voicemail service for on-premises users](plan-cloud-voicemail.md)

[New-CsHybridApplicationEndpoint](/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts) - \(to create resource accounts homed online\)
