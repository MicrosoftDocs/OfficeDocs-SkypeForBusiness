---
title: "Configure a resource account in Skype for Business Server 2019"
ms.author: jambirk
author: jambirk
manager: serdars 
ms.reviewer: wasseemh
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "set up a resource account for Skype for Business Server 2019."
---

# Configure resource accounts

Skype for Business Server 2019 hybrid implementations only use Cloud services provided by Phone System for unified messaging and do not integrate with Exchange Online. In Skype for Business Server 2019 you are now able to use the Cloud call queues and auto attendants described in [Here's what you get with Phone System in Office 365](/MicrosoftTeams/here-s-what-you-get-with-phone-system.md).

To use these Phone System services with Skype for Business Server 2019, you will need to create resource accounts that act as application endpoints and can be assigned phone numbers, then use the online Teams admin center to configure the call queue or auto attendant. This resource account can be homed online (see [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts) to create resource accounts homed online) or on premise as described in this article. Typically you will have multiple Phone System service nodes, each of which is mapped to a resource accounts, which can be homed online or in Skype for Business Server 2019.

If you have an existing Exchange UM auto attendant and call queue system, before you switch to Exchange Server 2019 or Exchange online you will need to manually record the details as described below and then implement a completely new system using the Teams admin center.

## Overview

If your Phone System service will need a service number, the various dependencies can be met in the following sequence:

1. Obtain a service number
2. Buy a Phone System license (Enterprise E1, E3 or E5)
3. Create the resource account. An auto attendant or call queue is required to have an associated resource account.
4. Wait for an active directory sync between online and on premise
5. Assign the Phone System license to the resource account.
6. Assign a service number to the resource account.
7. Create a Phone System service (a call queue or auto attendant)
8. Associate the resource account with a service: (New-CsApplicationInstanceAssociation)

If the auto attendant or call queue is nested under a top level auto attendant, the associated resource account only needs a phone number if you want multiple points of entry into the structure of auto attendants and call queues.

To redirect calls to people in your organization who are homed Online, they must have a **Phone System** license and be enabled for Enterprise Voice or have Office 365 Calling Plans. See [Assign Microsoft Teams licenses](/MicrosoftTeams/assign-teams-licenses.md). To enable them for Enterprise Voice, you can use Windows PowerShell. For example run:  `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`

If the Phone system service you're creating will be nested and will not need a phone number, the process is:

1. Create the resource account  
2. Wait for an active directory sync between online and on premise
3. Create a Phone System service
4. Associate the resource account with a Phone System service

## Create a resource account with a phone number

Creating a resource account that uses a phone number would require performing the following tasks in the following order:

1. Port or get a toll or toll-free service number. The number can't be assigned to any other voice services or resource accounts.

   Before you assign a phone number to a resource account, you will need to get or port your existing toll or toll-free service numbers. After you get the toll or toll-free service phone numbers, they will show up in **Microsoft Teams admin center** > **Voice** > **Phone numbers**, and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see [Getting service phone numbers](../../SfbOnline/what-is-phone-system-in-office-365/getting-service-phone-numbers.md)  ?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json  or if you want to transfer an existing service number, see [Transfer phone numbers to Office 365](/MicrosoftTeams/transfer-phone-numbers-to-office-365.md).

   If you are outside the United States, you can't use the Microsoft Teams admin center to get service numbers. Go to [Manage phone numbers for your organization](/MicrosoftTeams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md) instead to see how to do it from the outside of the United States.

2. Buy a Phone System license. See:  
   - [Office 365 Enterprise E1 and E3](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e1-e3.md)
   - [Office 365 Enterprise E5](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e5-with-audio-conferencing.md)
   - [Office 365 Enterprise E5 Business Software](https://products.office.com/business/office-365-enterprise-e5-business-software)

3. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each Phone System service, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName appinstance01 -SipAddress sip:appinstance01@contoso.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

4. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of Phone System services. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

5. Assign the Phone System license to the resource account. See [Assign Microsoft Teams licenses](/MicrosoftTeams/assign-teams-licenses.md) and [Assign licenses to one user](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#assign-licenses-to-one-user).

    If you are assigning a phone number and you have an Enterprise E1 or E3 licenses you must buy and assign a Phone System license to your the resource account that you will be using. If you have an Enterprise E5 license, Phone System is already included so there's no need to buy one.

    > [!NOTE]
    > Microsoft is working on a cost-free licensing model for resource accounts used with Phone System services, for now you need to use the user-licensing model.

6. Assign the service number to the resource account. Use the `Set-CsHybridApplicationEndpoint` command to a assign a phone number (with the -LineURI option) to the resource account.

    ``` Powershell
    Set-CsHybridApplicationEndpoint -Identity appinstance01@contoso.com -LineURI tel:+14255550100
    ```

    See [Set-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/set-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

    To assign a direct routing or hybrid number to  a resource account, use the following cmdlet:

   ``` Powershell
   Set-CsOnlineApplicationInstance -Identity appinstance01@contoso.com -OnpremPhoneNumber +14250000000
   ```

The resource account will need an assigned phone number if it will be assigned to a top level auto attendant or call queue. User (subscriber) phone numbers can't be assigned to a resource account, only service toll or toll-free phone numbers can be used.

    You can assign a Direct Routing Hybrid number to your resource account.  See [Plan Direct Routing](direct-routing-plan.md) for details.

    > [!NOTE]
    > Direct Routing service numbers assigned to resource accounts for auto attendant and call queues are supported for Microsoft Teams users and agents only.

    > [!NOTE]
    > Microsoft is working on an appropriate licensing model for applications such as Cloud auto attendants and call queues, for now you need to use the user-licensing model.

7. Create the Phone system service. See one of the following:
   - [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant.md)
   - [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue.md)  
8. Associate the resource account with the Phone system service you chose previously.

An example of a small business implementation is available in  [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) and [Small business example - Set up a call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-cq.yml).

## Create a resource account without a phone number

This section discusses creating a resource account that is homed on premise. Creating a resource account that is homed online is discussed at [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts.md).

These steps are necessary whether you are creating a brand new Phone System service system, or rebuilding structure originally created in Exchange UM.

Log in to the Skype for Business front end server and run the following PowerShell cmdlets:

1. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each Phone System service, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName appinstance01 -SipAddress sip:appinstance01@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

2. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of Phone System services. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

3. Create the Phone system service. See one of the following:
   - [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant.md)
   - [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue.md)  
4. Associate the resource account and the Phone System service you chose previously.

An example of a small business implementation is available in  [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) and [Small business example - Set up a call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-cq.yml).

## Test the implementation

The best way to test the implementation is to call the number configured for a Phone System service and connect to one of the agents or menus. You can also quickly place a test call by using the **Test button** in the admin center Action pane. If you want to make changes to a Phone System service, select it and then in the Action pane click **Edit**.

## Moving an Exchange UM auto attendant or call queue to Phone System

Migration from Exchange UM to Phone System will require recreating the call queue and auto attendant structure, directly migrating from one to the other is not supported. To re-implement a set of call queues and auto attendants:

1. Get a list of all Exchange UM auto attendants and call queues by running the following command on the Exchange 2013 or 2016 system while logged in as admin:

    ``` Powershell
    Get-UMAutoAttendant | Format-List
    ```

2. For each listed Exchange UM call queue or auto attendant, note its place in the structure, settings, and get copies of associated sound or text-to-speech files (the guid in the output will be the name of a folder where the files are stored). You can get these details by running the command:

    ``` Powershell
    Get-UMAutoAttendant -Identity MyUMAutoAttendant
    ```

    See [Get-UMAutoAttendant](https://docs.microsoft.com/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) for more details on this command. A complete list of options you might need to capture is at [UMAutoAttendant members](https://msdn.microsoft.com/library/microsoft.exchange.data.directory.systemconfiguration.umautoattendant_members.aspx) but the most important options to note down are:

    - Business hours
    - Non-business hours
    - Language
    - Holiday schedule

3. Create new on-premises endpoints as previously described.
   Assign the top-level auto attendant a temporary number for testing purposes.

4. Configure a Phone system service that uses the endpoints as previously described.

   You may find it useful to use the exercises in the tutorial titled [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) to create a logical map of the hierarchies in your old Exchange UM system.
5. Test the Phone System service.
6. Reassign the phone number linked to the Exchange UM call queue or auto attendant to the corresponding Phone system service.  

   At this point, if you have already migrated UM Voicemail, you should be in a position to migrate to Exchange Server 2019.

## See Also

[Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue.md)

[What are Cloud auto attendants?](/MicrosoftTeams/what-are-phone-system-auto-attendants.md)

[Set up a Cloud auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

[Plan Cloud auto attendant](plan-cloud-auto-attendant.md)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)

[New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts.md) - \(to create resource accounts homed online\)
