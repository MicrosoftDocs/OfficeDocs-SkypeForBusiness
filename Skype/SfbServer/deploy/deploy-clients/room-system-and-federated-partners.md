---
title: "Skype Room System and Skype for Business federated partners"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1cc20323-ecba-4e87-a861-e54193e64cf0
description: "Read this topic to learn how to set up Skype Room System for Skype for Business federated partners."
---

# Skype Room System and Skype for Business federated partners
 
Read this topic to learn how to set up Skype Room System for Skype for Business federated partners.
  
## Skype Room System and Skype for Business federated partners

Skype Room System relies on the Join Skype for Business Meeting link in the calendar meeting request. The join link is usually found in the body of a meeting request. However, Skype Room System depends on this link to be present in the MAPI properties of the message. When this meeting request is sent to remote organizations (Skype for Business federated partners), by default the remote organization's Skype Room System will not show the meeting join link on the calendar. In fact, any Outlook users in the remote organization will be unable to join the Skype for Business meeting with a right click of the calendar item or from within the meeting reminder. They must open meeting invite and click Join Skype for Business Meeting in the body of the message. 
  
The reason for this limitation is that Outlook and Microsoft Exchange do not use a special method to package information for sending messages across the Internet. This method, referred to as Transport Neutral Encapsulation Format (TNEF), is disabled by default for messages sent externally from an Exchange organization. For a meeting join link to appear on a remote Skype Room System, the sending organization must enable TNEF by using the following command:
  
```
New-RemoteDomain -DomainName Contoso.com -Name Contoso
Set-RemoteDomain -Identity Contoso -TNEFEnabled $true
```

After TNEF is enabled for the remote organization, any message sent over the Internet to the organization is sent as an attachment in TNEF format. With TNEF enabled, when a Skype for Business meeting request is sent to the Skype for Business federated partner, Skype Room System will be able to render the Join Skype for Business Meeting and remote users will be able to join Skype for Business meetings. 
