---
title: "Configure a Cloud call queue"
ms.author: jambirk
author: jambirk
manager: serdars 
ms.reviewer: wasseemh
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using a Cloud PBX call queue with Skype for Business Server 2019."
---

# Configure Cloud call queues

Skype for Business Server 2019 hybrid implementations only use Cloud services provided by Phone System and do not integrate with Exchange Online.

In Skype for Business Server 2019 you are now able to use the Cloud call queues described in [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue).

To use Cloud call queues with Skype for Business Server 2019, you will need to create on-premises resource accounts that act as application endpoints and can be assigned phone numbers, then use the online Admin Center to configure the call queue. Typically you will have multiple call queues, each of which plays an audio outgoing message to callers, each of which is mapped to one of these on-premises resource accounts, and each of which routes call to available agents.

If you have an existing call queue implemented in Exchange UM, before you switch to Exchange Server 2019 or Exchange online, you will need to manually record the details as described below and then implement a completely new Cloud call queue system using the Teams Admin portal.

## Server configuration steps

These steps are necessary whether you are creating a brand new call queue or rebuilding an call queue originally created in Exchange UM.

Log in to the front end server and run the following PowerShell cmdlets:

1. Create an on-premises resource account by running the `New-CsHybridApplicationEndpoint` cmdlet as needed (for one or more call queues), and give each one a name, sip address, and so on.

    Configuring a phone number for a call queue is required only if you want to connect callers directly to a queue without using an auto attendant.

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com" -LineURI tel:+14255550100
    ```

    So for a call queue you intend to route a caller to after making an auto attendant selection, you can omit the phone number as shown:

    ``` Powershell
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com"
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/en-us/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

    > [!NOTE]
    > You can also use the `Set-CsHybridApplicationEndpoint` command to a assign a phone number (with the -LineURI option) to the call queue after its initial creation.

    ``` Powershell
    Set-CsHybridApplicationEndpoint -Identity "CN={4f6c99fe-7999-4088-ac4d-e88e0b3d3820},OU=Redmond,DC=litwareinc,DC=com" -DisplayName AANode1 -LineURI tel:+14255550100
    ```

    See [Set-CsHybridApplicationEndpoint](https://docs.microsoft.com/en-us/powershell/module/skype/set-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

2. (Optional) Once these resource accounts are created and the required phone numbers are assigned, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of the call queues. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ``` Powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

## Online configuration steps

Your online implementation will need to have a plan that includes Phone System licenses as described at [Office 365 Enterprise E1, E3, and E4](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e1-e3-e4) or [Office 365 Enterprise E5](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e5-with-audio-conferencing).

1. Assign Phone System licenses to the on-premise resource account as described in  [Assign licenses to users in Office 365 for business](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide) and [Assign Skype for Business and Microsoft Teams licenses](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses).

2. Use the procedures in [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue) to implement the Cloud call queue settings.  

An example of a small business implementation is available in  [Small business example - Set up an auto attendant](/microsoftteams/tutorial-org-aa).

## Test the new call queue

The best way to test the implementation is to call the number configured for a call queue and connect to one of the agents. You can also quickly place a test call to your call queue by using the **Test button** in the admin center Action pane. If you want to make changes to an call queue, select the call queue, and then in the Action pane click **Edit**.

## Manually moving an Exchange UM call queue to Cloud call queue

1. Get a list of all call queues by running the following command on the Exchange 2013 or 2016 system while logged in as admin:

    ``` Powershell
    Get-UMAutoAttendant | Format-List
    ```

2. For each listed call queue, note its place in the structure, settings, and get copies of associated sound or text-to-speech file (the guid in the output will be the name of a folder where the files are stored). You can get these details by running the command:

    ``` Powershell
    Get-UMAutoAttendant -Identity MyUMAutoAttendant
    ```

    See [Get-UMAutoAttendant](https://docs.microsoft.com/en-us/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) for more details on this command. A complete list of call queue options you might need to capture is at [UMAutoAttendant members](https://msdn.microsoft.com/en-us/library/microsoft.exchange.data.directory.systemconfiguration.umautoattendant_members.aspx) but the most important options to note down are:

    - Business hours
    - Non-business hours
    - Language
    - Holiday schedule

3. Create new on-premises endpoints as described above in [Server configuration steps](#server-configuration-steps).
   Assign the call queue a temporary number for testing purposes.

4. Configure a Cloud call queue that uses these endpoints as described above in [Online configuration steps](#online-configuration-steps).

   You may find it useful to use the exercises in the tutorial titled [Small business example - Set up an auto attendant](/microsoftteams/tutorial-org-aa) to create a logical map of the auto attendant and user or call queue hierarchies in your old Exchange UM system.
5. Test the Cloud call queue.
6. Reassign the phone number linked to the Exchange UM call queue to the Cloud call queue.  

   At this point, if you have already migrated UM Voicemail, you should be in a position to migrate to Exchange Server 2019.

## See Also

[Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue)

[What are Cloud auto attendants?](/MicrosoftTeams/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant)

[Plan Cloud auto attendant](plan-cloud-auto-attendant.md)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)

[New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts)  (to create resource accounts homed online)