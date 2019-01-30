---
title: "Managing resource accounts in Teams"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: jastark, wasseemh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: Teams_ITAdmin_Help
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords:
- ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
description: "Managing resource accounts in Microsoft Teams"
---

# Manage resource accounts in Teams

A Resource Account is also known as a disabled user object in Azure Active Directory, and can be used to represent resources in general. In Exchange it might be used to represent conference rooms, for example, and allow them to have a phone number. A resource account can be homed in Microsoft 365 or on premises using Skype for Business server, and these accounts are created using Powershell commands.

In Microsoft Teams, an admin uses a resource account to assign a phone number to a Call Queue or Auto Attendant.

## Prerequisites


## Create a resource account in Powershell

 Create a resource account  by running the `New-CsOnlineApplicationInstance` cmdlet as needed (for one or more resource accounts), and give each one a name, sip address, and so on. There is currently no option for creating a resource account in the Microsoft Teams admin center, but you can edit phone numbers and change the Call Queue or Auto Attendant assignments.

Configuring a phone number for a resource account is required only if you want to connect callers directly to a Call Queue without using one or more Auto Attendants. In a larger Auto Attendant system, a phone number for the main Auto Attendant is required but optional for any nested auto attendants or Call Queues called by an Auto Attendant


``` Powershell
New-CsOnlineApplicationInstance -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com" -LineURI tel:+14255550100
```

So for a call queue you intend to route a caller to after making an auto attendant selection, you can omit the phone number as shown:

``` Powershell
New-CsOnlineApplicationInstance -DisplayName AANode1 -SipAddress sip:aanode1@litwareinc.com -OU "ou=Redmond,dc=litwareinc,dc=com"
```

See [New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps) for more details on this command.

> [!NOTE]
> You can also use the `Set-CsOnlineApplicationInstance` command to a assign a phone number (with the -LineURI option) to the Call Queue after its initial creation.

``` Powershell
Set-CsOnlineApplicationInstance -Identity "CN={4f6c99fe-7999-4088-ac4d-e88e0b3d3820},OU=Redmond,DC=litwareinc,DC=com" -DisplayName AANode1 -LineURI tel:+14255550100
```

See [Set-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/set-csonlineapplicationinstance?view=skype-ps) for more details on this command.

Hybrid implementations will use [New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps) to have a resource account that is homed on premises.

Once resource accounts are created, you can either wait for AD to sync between online and on premises, or force a sync and proceed to configuration of Auto Attendants or Call Queues. To force a sync you would run the following command on the computer running AAD Connect (if you haven't done so already you would need to load `import-module adsync` to run the command):

    ```
    Start-ADSyncSyncCycle -PolicyType Delta
    ```
    See [Start-ADSyncSyncCycle](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler) for more details on this command.

## Manage Resource account settings in Microsoft Teams admin center

To manage Resource account settings in Microsoft Teams admin center, navigate to Org-wide settings  > Resource accounts, select the resource account you need to change settings for, and then click on the Edit button. in the Edit resource account screen, you will be able to change the: 

- **Display name* for the account
- Call Queue or Auto Attendant the account is assigned to 
- Phone number assigned to the account (if any)


## Related Information

For implementations that are hybrid with Skype for Business Server:

[Plan Cloud Auto Attendant](/SkypeForBusiness/hybrid/plan-cloud-auto-attendant.md)

[Configure Cloud Auto Attendants](/SkypeForBusiness/hybrid/configure-cloud-auto-attendant.md)

For implementations in Teams or Skype for Business Online:

[What are Phone System auto attendants?](what-are-phone-system-auto-attendants.md)

[Set up a Phone System auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

[Small business example - Set up an Auto Attendant](https://docs.microsoft.com/en-us/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa)

[Create a Phone System call queue](/SkypeForBusiness/what-is-phone-system-in-office-365/create-a-phone-system-call-queue.md)

[New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)