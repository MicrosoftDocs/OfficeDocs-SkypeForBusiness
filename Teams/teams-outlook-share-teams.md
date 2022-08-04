---
title: Share to Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: kblevens
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the Share to Teams feature, which allows users to share emails and email attachments from Outlook to any chat or channel in Teams.  
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Share to Teams from Outlook

Share to Teams from Outlook (Share to Teams) enables users to share emails, including attachments, from Outlook to any chat or channel in Teams.

## Outlook add-in for Share to Teams 

The Share to Teams feature requires an add-in for Outlook. This add-in is installed automatically whenever a user logs on to either the Teams Web app or the Teams desktop client.

> [!NOTE]
> Be sure to review [Add-ins for Outlook in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/add-ins-for-outlook) and [Client Access Rules in Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) to make sure your add-ins for Outlook function correctly. Also, disabling connected experiences can prevent add-ins for Outlook from working properly. See [Connected experiences in Office](https://support.microsoft.com/topic/connected-experiences-in-office-8d2c04f7-6428-4e6e-ac58-5828d4da5b7c) for more information. Shared mailboxes are not supported by the add-in. 

Share to Teams uses the same transport mechanism as when a user emails a channel. For sharing to chats, emails (including email attachments) are copied to the sender's OneDrive. For sharing to channels, emails and attachments are copied to the **Email messages** folder in SharePoint.

The Outlook add-in for Share to Teams uses requirement set 1.7, as detailed in [Outlook add-ins documentation](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/add-ins-for-outlook), which includes details on Outlook add-ins, environment requirements for Outlook add-ins, and the specific Outlook clients that are supported with requirement set 1.7.

## Enabling or disabling Share to Teams

The Outlook add-in for Share to Teams can be selectively disabled or enabled on a per-user basis using the following PowerShell cmdlets.

> [!NOTE]
> Disabling the add-in is only possible after the add-in has been installed. If you would like to enforce disabling for all users in your tenant, run a script periodically.

To disable the add-in for Outlook used by Share to Teams, run the [cmdlet found here](/powershell/module/exchange/disable-app).

To enable the add-in for Outlook used by Share to Teams, run the [cmdlet found here](/powershell/module/exchange/enable-app).

## Browsers and Single Sign-on

Share to Teams, in both Outlook on the web and Outlook desktop clients, relies on a browser WebView. See [Browsers used by Office Add-ins](/office/dev/add-ins/concepts/browsers-used-by-office-web-add-ins) for details on which clients use which specific browsers. 

> [!IMPORTANT]
> Share to Teams requires both third-party cookies and local storage access to be enabled for users' browsers.

Share to Teams uses Single Sign-on (SSO), which means users don't need to provide their credentials when using the add-in via Share to Teams. SSO for Outlook on the web supports <https://outlook.office365.com/owa/extSSO.aspx> and <https://outlook.office.com/owa/extSSO.aspx> reply URLs by default. For vanity domains, administrators need to add the appropriate Azure Active Directory reply URL.
