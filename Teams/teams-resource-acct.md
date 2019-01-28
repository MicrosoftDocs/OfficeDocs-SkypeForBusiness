---
title: Resource Accounts in Microsoft Teams
author: jambirk
ms.author: lolaj
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: wasseemh
localization_priority: Normal
search.appverid: MET150
description: Learn about Microsoft Teams resource accounts used to provide phone numbers for resources Like Call Queues and Auto Attendants.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
- Skype for Business 
- f1keywords:
- ms.teamsadmincenter.orgwidesettings.resourceaccounts.overview
---

# What is a Resource Account?

A Resource Account is also known as a disabled user object in Azure Active Directory, and can be used to represent resources in general. In Exchange it might be used to represent conference rooms, for example, and allow them to have a phone number. A resource account can be homed in Microsoft 365 or on premises using Skype for Business server, and these accounts are created using Powershell commands.

In Microsoft Teams, an admin can use a resource account to:

- Assign a phone number to a Call Queue or Auto Attendant
- Assign a domain to a Call Queue
- Check Licenses

## Related Information

For implementations that are hybrid with Skype for Business Server:

[Plan Cloud Auto Attendant](../Skype/SfBServer2019/hybrid/plan-cloud-auto-attendant.md)

[Configure Cloud Auto Attendants](../Skype/SfBServer2019/hybrid/configure-cloud-auto-attendant.md)

For implementations in Teams or Skype for Business Online:

[What are Phone System auto attendants?](what-are-phone-system-auto-attendants.md)

[Set up a Phone System auto attendant](../Skype/SfbOnline/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

[Create a Phone System call queue](../Skype/SfbOnline/what-is-phone-system-in-office-365/create-a-phone-system-call-queue.md)

[New-CsHybridApplicationEndpoint](https://docs.microsoft.com/powershell/module/skype/new-cshybridapplicationendpoint?view=skype-ps)

[New-CsOnlineApplicationInstance](https://docs.microsoft.com/powershell/module/skype/new-csonlineapplicationinstance?view=skype-ps)