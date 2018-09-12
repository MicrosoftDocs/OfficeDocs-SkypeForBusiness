---
title: "Configure Cloud Auto Attendant"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 8/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing a Cloud Auto Attendant."
---

[!INCLUDE [disclaimer](../disclaimer.md)]

# Configure Cloud Auto Attendant
 
In Skype for Business Server 2019 you are able to use the cloud auto attendant feature described in [What are Phone System auto attendants?](/microsoftteams/what-are-phone-system-auto-attendants)

To use Cloud Auto Attendant with Skype for Business Server 2019, you will need to create virtual on-prem users that act as application endpoints and can be assigned phone numbers, then use the online Admin Center to configure the overall Cloud AA experience. Typically you will have multiple Auto Attendants, each of which plays an audio outgoing message to callers.

If you have an existing Auto Attendant implemented in Exchange UM, you will ned to manually record the details as described below and then implement a completely new Cloud Auto Attendant using the Office Online Admin portal.

## Server configuration steps

These steps are necessary whether you are creating a brand new Auto Attendant or rebuilding an Auto Attendant originally created in Exchange UM.

1. Create each Auto Attendant by running the `New-CsHybridApplicationEndpoint` cmdlet as needed, and give each one a name, sip address, and so on.

    For an Auto Attendant that will be the Initial Greeting or after-hours greeting, be sure to assign the phone number using the  -LineURI option. This is optional if the auto attendant is a child in the hierarchy.

    ```
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com" -LineURI tel:+14255550100
    ```
    or for a child auto attendant:

    ```
    New-CsHybridApplicationEndpoint -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com" 
    ```

    See [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/en-us/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

    > [!NOTE]
    > You can also use the `Set-CsHybridApplicationEndpoint` command to a assign a phone number (with the -LineURI option) to the Auto Attendant node that will serve as the initial greeting. This is optional if the auto attendant is a child in the hierarchy. You could do this step later if desired, or reset the phone number at a later time.
    ```
    Set-CsHybridApplicationEndpoint -Identity "CN={4f6c99fe-7999-4088-ac4d-e88e0b3d3820},OU=Redmond,DC=litwareinc,DC=com" -DisplayName AANode1 -LineURI tel:+14255550100
    ```

    See [Set-CsHybridApplicationEndpoint](https://docs.microsoft.com/en-us/powershell/module/skype/set-cshybridapplicationendpoint?view=skype-ps) for more details on this command.

3. (Optional) Once these endpoints are created and the required phone numbers are assigned, you can either wait for AD to sync between online and on premise, or force a sync and proceed to online configuration of the Auto Attendants.
    ```
    Start-ADSyncSyncCycle -PolicyType Initial
    ```
    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

## Online configuration steps

Your online implementation will need to have a plan that includes Phone System as described at https://docs.microsoft.com/en-us/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e1-e3-e4 or https://docs.microsoft.com/en-us/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e5-with-audio-conferencing.

1. Assign Phone System licenses to the on-premise hybrid endpoints as described in  https://docs.microsoft.com/en-us/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.

2. Use the procedures in [Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md) to implement the Cloud Auto Attendant structure.  

## Manually moving an Exchange UM Auto Attendant to Cloud Auto Attendant

1. Get a list of all Auto Attendants by running the following command on the Exchange 2013 or 2016 system while logged in as admin: 
    ```
    Get-UMAutoAttendant | Format-List
    ```
2. For each listed Auto Attendant, note its place in the structure, settings, and get copies of associated sound or text-to-speech file (the guid in the output will be the name of a folder where the files are stored). You can get these details by running the command:
    ```
    Get-UMAutoAttendant -Identity MyUMAutoAttendant
    ```
    See [Get-UMAutoAttendant](https://docs.microsoft.com/en-us/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) for more details on this command. A complete list of Auto Attendant options you might need to capture is at https://msdn.microsoft.com/en-us/library/microsoft.exchange.data.directory.systemconfiguration.umautoattendant_members.aspx  but the most important other options to note down are:
    - Business hours
    - After hours
    - Language
    - Holiday schedule

3. Create new onprem endpoints as described above in [Server configuration steps](#server-configuration-steps).
4. Configure a Cloud Auto Attendant system that uses these endpoints as described above in [Online configuration steps](#online-configuration-steps).

## See Also

[What are Phone System auto attendants?](/microsoftteams/what-are-phone-system-auto-attendants)

[Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

[Plan Cloud Auto Attendant](plan-cloud-auto-attendant.md)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)