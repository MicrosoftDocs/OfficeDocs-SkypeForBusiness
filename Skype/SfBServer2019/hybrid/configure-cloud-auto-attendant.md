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

In Skype for Business Server 2019 you are able to use the cloud auto attendant feature described in [What are Phone System auto attendants?](../../SfbOnline/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md)

To use Cloud Auto Attendant with Skype for Business Server 2019, you will need to create  virtual on-prem users that contain disabled user objects (DUOs) and assigned phone numbers, then use the online Admin Center to configure the Cloud AA experience.

If you have an existing Auto Attendant implemented in Exchange UM, you will ned to manually record the details as described below and then implement a completely new Cloud Auto Attendant using the Office Online Admin portal.

## Server configuration steps - Create disabled user objects

These steps are necessary whether you are creating a brand new Auto Attendant or rebuilding an Auto Attendant originally created in Exchange UM.

1. Create unique disabled user objects (DUOs) for every AA <br/> Supports Multiple numbers and Multiple DUOs for every AA <br/> **[using Active Directory Administrative Center:**
    ```
    New-ADUser -Name "John Smith" -GivenName "John" -Surname "Smith" -SamAccountName "jsmith" -UserPrincipalName "jsmith@<span></span>contoso<span></span>.com" -Path "OU=Users,OU=Europe,DC=contoso,DC=com" -AccountPassword(Read-Host -AsSecureString "Type Password for User") -Enabled $false
    ```
    See [New-ADUser](https://docs.microsoft.com/en-us/powershell/module/addsadministration/new-aduser?view=win10-ps)

2. Delete contact objects (COs) for every AA  <br/> See [Remove-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csexumcontact?view=skype-ps0)

3. Run AAD Connect Sync
    ```
    Start-ADSyncSyncCycle -PolicyType Initial    
    ```
    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler)
4. Assign licenses to DUOs [ask Tony]

5. Provision numbers and assign them to DUOs  [ask Tony]

6. Hydrate the AAs [what  does this mean?]

**How does [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/en-us/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) fit into this process?**

## Moving an Exchange UM Auto Attendant to Cloud Auto Attendant

### Capture the existing Exchange UM Auto Attendant

For every AA in the Dial Plan you want to move:

* Record the properties of the AA object <br/>  run [Get-UMAutoAttendant](https://docs.microsoft.com/en-us/powershell/module/exchange/unified-messaging/get-umautoattendant?view=exchange-ps) logged in to the on-prem Exchange server as admin
    * Be sure to create copies of the sound file for each AA object.
    * **We don't yet have guidance on how to manually parse this output in order to recreate the experience using Cloud AA, which could be an article all by itself**
* Using Active Directory Administrative Center, create a Disabled User Object in AD for each instance of Auto Attendant.
    ```
    New-ADUser -Name "John Smith" -GivenName "John" -Surname "Smith" -SamAccountName "jsmith" -UserPrincipalName "jsmith@<span></span>contoso<span></span>.com" -Path "OU=Users,OU=Europe,DC=contoso,DC=com" -AccountPassword(Read-Host -AsSecureString "Type Password for User") -Enabled $false
    ```
    See [New-ADUser](https://docs.microsoft.com/en-us/powershell/module/addsadministration/new-aduser?view=win10-ps)
    * For AAs with multiple numbers, create multiple disabled user objects, distinguishable by numbered suffixes (AA1, AA2, and so on).
    * No suffix is required for an AA with a single number.

* Delete the contact objects associated with the AA. **why is this necessary? we just barely created the object. Why would there be contacts associated with it?**
    ```
    Remove-CsExUmContact
    ```
    See [Remove-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/remove-csexumcontact?view=skype-ps)

## Online Configuration steps

Review [Writing better Auto Attendant scripts](plan-cloud-auto-attendant.md#writing-better-auto-attendant-scripts) then see [Set up a Phone System auto attendant](../../SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md).  

## See Also

[Plan Cloud Auto Attendant](plan-cloud-auto-attendant.md)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)