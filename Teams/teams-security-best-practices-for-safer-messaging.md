---
title: Teams security best practices for safer messaging
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.date: 11/10/2021
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: pawa
description: A quick reference on how to securely use Teams, this article acts as a primer on general security best practices and tips for training users on safe messaging.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---
# Security best practices for Microsoft Teams

Collaboration through instant messaging and video conferencing has allowed many industries and schools to move their interactions online. However, online real-time collaboration at such a broad scale also comes with *risks* that must be addressed. Otherwise, bad actors take advantage of this change in work and life with **phishing** and **spam** campaigns. The numbered reference list in this article acts as a primer for general security when using Teams to interact with others, and is training guidance for people new to Teams, or to any online collaboration, security.

The same phishing risks that exist in email exist in instant messaging and collaboration apps so the same user-awareness and guidance should be applied to safeguard Teams users.

At a user level, some measures can be simple, and users should feel empowered to rely on them. Users shouldn’t click to open links from anyone that they don’t know, or whose identity they can't verify per the article [Protect yourself from phishing](https://support.microsoft.com/en-us/windows/protect-yourself-from-phishing-0c7ea947-ba98-3bd9-7184-430e1f860a44). Users can choose to [accept or block messages](https://support.microsoft.com/en-us/office/accept-or-block-people-outside-your-org-who-send-you-a-chat-4b5b917d-895a-4379-a204-a111b2e24f41) when interacting with users they do not know or do not expect to be contacted by. And to further protect against external attacks, tenant admins can disable interaction with external users through enterprise federation and Teams for Life (TFL) and Skype interoperability—see [Manage external access (federation) - Microsoft Teams | Microsoft Docs](/microsoftteams/manage-external-access).

The Teams collaboration feature set allows messaging, file collaboration, meetings, whiteboards, and many other opportunities to connect. These features work across Teams for Enterprise, Teams for Life, Skype, Skype for Business, Azure Communication Services (ACS), and more. That also means it’s necessary to protect yourself, your peers, and your customers across the breadth of these capabilities. Here, again, every user should be empowered to make the safest decision for themselves, their peers, and their customers.

## As with email, online safety must be practiced in Microsoft Teams messaging

Standard safety measures should become ingrained while working in Teams.

1. Be wary of contacts and meeting requests from outside of your organization. Strangers can be well meaning. And some can secretly mean harm.
2. If you don’t recognize the sender, you can check the known global address list of your company for their identity and escalate any communications you can’t verify to a higher level for handling. When in doubt, do not interact with unknown and unverified users.
3. If you receive a link or file from an unknown person, do not click on it. Again, use your best judgment for your own, other users', and your customers' safety.
4. If selecting a link lands you on a safe links page where you are blocked from navigation, don't try to circumvent that page. The same goes for selecting any attachment that may end in a red, blocking attachments safe page. If you know and trust the target site, report the problem to Microsoft and to whomever directed you there. Many reasons exist to land on a blocking page, so consider the red flags behind those reasons, rather than circumnavigate the blocking page.
5. Never give personal information out to any unsolicited requests. Providing personal information is also a risk to personal safety. Attackers can leverage details as simple as your birthday.
6. Scan your links for iffy spelling, added digits, or strange characters. You may be expecting a link to `www.litware.com/strategies/Metricsbreakout.xlsx`, but find that the address looks like `www.litwre.com`, `www.litwarecom.com`, or even `www.litwαre.com`. If you don’t recognize the link, be suspicious. The address `www.litware.com` is not the same as `www.litware2021.com`.

Maintaining your vigilance is important. Don't take your security or the security of those you work with lightly or for granted. You should always feel empowered to protect yourself, your peers, and your customers by verifying before you trust.

Finally, recognizing that everyone makes mistakes is critical. Users are prone to clicking when in a hurry or tired, for example. Admins must provide users in their organization with resources to escalate problematic link clicks and other security incidents and make those resources known so that if a user makes a mistake, the user has recourse and further security actions are available.

> [!TIP]
> Check the Profile card of any contact you’re not sure about, particularly if the email is external to your company (for example, an account ending in *@litware.com* if your organization is not *Litware*). A user can verify that people they don't know are welcome Guests to a meeting by checking the Profile card for **(GUEST)**. Guests are expressly invited to participate.
