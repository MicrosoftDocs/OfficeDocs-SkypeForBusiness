---
title: "Managing the Skype for Business client from Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: d1ccc7b6-99ff-4ffd-bd29-9088fb8fe837

description: "The following cmdlets manage the Lync client:"
---

# Managing the Skype for Business client from Skype for Business Online
[]
The following cmdlets manage the Lync client:
  
|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md) <br/> |Retrieves information about the URI restrictions in use in your organization.  <br/> When sending instant messages, users can embed a URI within the text of that message that refers other participants in the conversation to a particular website or share. Skype for Business Online can be configured so that hyperlinks with certain prefixes are blocked or are not active. This helps to ensure that participants can't click the link and go to the site the URI refers to. Instead, they must copy and paste the link manually into a browser.  <br/> |
|[Get-CsPresencePolicy](get-cspresencepolicy.md) <br/> |Returns information about two important aspects of presence subscriptions: prompted subscribers and category subscriptions.  <br/> When you are added to someone's Contact list, the default behavior is for you to receive a pop-up notification informing you that you've been added to that list. Until you dismiss the pop-up, each notification counts as a prompted subscriber.  <br/> Category subscriptions represent a request for a specific category of information—for example, an application that requests calendar data.  <br/> |
|[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)          [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md) <br/> |Configures default privacy values in Skype for Business Online, while still giving users the option to change these values.  <br/> Skype for Business Online gives users the opportunity to share a wealth of presence information with other people. Users can publish a photograph of themselves, provide detailed location information, and have presence information automatically available to everyone in the organization (instead of only to people on their Contacts list). **CsPrivacyConfiguration** cmdlets enable administrators to configure default privacy values in Skype for Business Online, while still allowing users the option to change these values.  <br/> |
   
You can also manage a subset of the privacy configuration settings by using the Skype for Business Online admin center:
  
![Lync admin center presence private mode settings](media/LyncOnlinePowerShell_Privacy_Settings.png)
  
## See also

#### 

[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)
  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

