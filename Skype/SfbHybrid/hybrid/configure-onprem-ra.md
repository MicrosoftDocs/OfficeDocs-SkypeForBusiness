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

Skype for Business Server 2019 hybrid implementations only use Cloud services provided by Phone System and do not integrate with Exchange Online. In Skype for Business Server 2019 you are now able to use the Cloud call queues and auto attendants described in [Here's what you get with Phone System in Office 365](/MicrosoftTeams/here-s-what-you-get-with-phone-system.md).

To use Phone System services with Skype for Business Server 2019, you will need to create resource accounts that act as application endpoints and can be assigned phone numbers, then use the online Teams admin center to configure the call queue or auto attendant. This resource account can be homed online (see [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts.md) to create resource accounts homed online) or on premise as described in this article. 

Typically you will have multiple call queue and auto attendant nodes, each of which plays an audio outgoing message to callers, each of which is mapped to one of these resource accounts, and each of which routes call to available agents.

If you have an existing auto attendant and call queue system implemented in Exchange UM, before you switch to Exchange Server 2019 or Exchange online you will need to manually record the details as described below and then implement a completely new system using the Teams admin center.

> [!NOTE]
> Microsoft is working on a cost-free licensing model for applications such as Cloud auto attendants and call queues, for now you need to use the user-licensing model.

If your Phone System service will need a phone number, the process will be:

1. Obtain a service number (if using a Microsoft service number)
2. Buy a Phone System license, and a Calling Plan if you are using a Microsoft service number
3. Create the resource account
4. Wait for an active directory sync between online and on premise.
5. Assign the Phone System license to the resource account
6. Assign the Calling Plan to the resource account (if you are using a Microsoft service number).
7. Assign a telephone number to the resource account.
8. Create a Phone System service (call queue or auto attendant)
9. Associate the resource account with a service: (New-CsApplicationInstanceAssociation)

If the Phone system service you're creating will be nested and will not need a phone number, the process is:

1. Create the resource account  
2. Wait for an active directory sync between online and on premise.
3. Create a Phone System service (call queue or auto attendant)
4. Associate the resource account with a service

## Create a resource account on premise

This section discusses creating a resource account that is homed on premise. Creating a resource account that is homed online is discussed at [Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts.md).

These steps are necessary whether you are creating a brand new call queue or auto attendant system, or rebuilding structure originally created in Exchange UM.

Log in to the Skype for Business front end server and run the following PowerShell cmdlets:

1. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each call queue or auto attendant, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.


2. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of Phone System services. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

3. create the service
4. Associate RA and Service

An example of a small business implementation is available in  [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) and [Small business example - Set up a call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-cq.yml).

### Apply phone numbers

Creating a resource account that uses a phone number would require performing the following tasks in the following order:

1. Transfer or get a toll or toll-free service number. The number can't be assigned to any other voice services or resource accounts.

   Before you assign a phone number to a resource account, you will need to get or port your existing toll or toll-free service numbers. After you get the toll or toll-free service phone numbers, they will show up in **Microsoft Teams admin center** > **Voice** > **Phone numbers**, and the **Number type** listed will be listed as **Service - Toll-Free**. To get your service numbers, see [Getting service phone numbers](../../SfbOnline/what-is-phone-system-in-office-365/getting-service-phone-numbers.md)  ?toc=/MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json  or if you want to transfer an existing service number, see [Transfer phone numbers to Office 365](/MicrosoftTeams/transfer-phone-numbers-to-office-365.md).

2. Buy a Phone System license and a Calling Plan. See:  
   - [Office 365 Enterprise E1 and E3](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e1-e3.md)
   - [Office 365 Enterprise E5](/MicrosoftTeams/teams-add-on-licensing/office-365-enterprise-e5-with-audio-conferencing.md)
   - [Office 365 Enterprise E5 Business Software](https://products.office.com/business/office-365-enterprise-e5-business-software)
   - [Calling Plans for Office 365](/MicrosoftTeams/calling-plans-for-office-365.md)

3. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet for each call queue or auto attendant, and give each one a name, sip address, and so on.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:appinstance01@contoso.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

4. (Optional) Once your resource accounts are created, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of Phone System services. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

5. Assign the Phone System license and the Calling Plan to the resource account. See [Assign Microsoft Teams licenses](/MicrosoftTeams/assign-teams-licenses.md) and [Assign licenses to one user](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#assign-licenses-to-one-user).

6. Assign the service number to the resource account.

7. Use the `Set-CsHybridApplicationEndpoint` command to a assign a phone number (with the -LineURI option) to the resource account.

    ``` Powershell
    Set-CsHybridApplicationEndpoint -Identity appinstance01@contoso.com -LineURI tel:+14255550100
    ```

    See [Set-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/set-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

To assign a direct routing number to  a resource account, use the following cmdlet:

``` Powershell 
Set-CsOnlineApplicationInstance -Identity appinstance01@contoso.com -OnpremPhoneNumber +14250000000
```

8. Associate the resource account with a Phone system service (call queue or auto attendant). See [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant.md) or [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue.md)

An example of a small business implementation is available in  [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) and [Small business example - Set up a call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-cq.yml).

## Online service configuration steps

2. Assign phone numbers. A phone number homed on Skype for business Server can be assigned using the `Set-CsHybridApplicationEndpoint` command as mentioned earlier. Phone numbers using Direct Routing or O365 Calling Plans will need to be assigned using the Teams admin center.
3. Use the procedures in [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue.md) or [Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant.md) to implement the Phone System service settings.  



## Test the implementation

The best way to test the implementation is to call the number configured for a call queue or auto attendant and connect to one of the agents or menus. You can also quickly place a test call by using the **Test button** in the admin center Action pane. If you want to make changes to a call queue or auto attendant, select it and then in the Action pane click **Edit**.

## Manually moving an Exchange UM auto attendant or call queue to Phone System

1. Get a list of all auto attendants and call queues by running the following command on the Exchange 2013 or 2016 system while logged in as admin:

    ``` Powershell
    Get-UMAutoAttendant | Format-List
    ```

2. For each listed call queue or auto attendant, note its place in the structure, settings, and get copies of associated sound or text-to-speech file (the guid in the output will be the name of a folder where the files are stored). You can get these details by running the command:

    ``` Powershell
    Get-UMAutoAttendant -Identity MyUMAutoAttendant
    ```

    See [Get-UMAutoAttendant](https://docs.microsoft.com/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) for more details on this command. A complete list of call queue options you might need to capture is at [UMAutoAttendant members](https://msdn.microsoft.com/library/microsoft.exchange.data.directory.systemconfiguration.umautoattendant_members.aspx) but the most important options to note down are:

    - Business hours
    - Non-business hours
    - Language
    - Holiday schedule

3. Create new on-premises endpoints as described above in [Online service configuration steps](#online-service-configuration-steps).
   Assign the top-level auto attendant a temporary number for testing purposes.

4. Configure a Phone system service that uses the endpoints as described above in [Online service configuration steps](#online-service-configuration-steps).

   You may find it useful to use the exercises in the tutorial titled [Small business example - Set up an auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) to create a logical map of the auto attendant and user or call queue hierarchies in your old Exchange UM system.
5. Test the Cloud call queue.
6. Reassign the phone number linked to the Exchange UM call queue to the Cloud call queue.  

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

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts.md)  (to create resource accounts homed online)