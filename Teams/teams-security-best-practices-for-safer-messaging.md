---
title: Teams security best practices for safer messaging
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.date: 10/30/2023
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

Collaboration through instant messaging and video conferencing has allowed many industries and schools to move their interactions online. However, online real-time collaboration at such a broad scale also comes with *risks* that must be addressed. Otherwise, bad actors take advantage of this change in work and life with **phishing** and **spam** campaigns.

The numbered reference list in this article acts as a primer for general security when using Teams to interact with others. It is security training guidance for people new to Teams, or to any online collaboration solutions.

## Security at a user level

**The same phishing risks that exist in email exist in instant messaging and collaboration apps** so the same user-awareness and guidance should be applied to safeguard Teams users.

At a user level, some measures can be simple, and users should feel empowered to rely on them.

- Users shouldn’t click to open links from anyone that they don’t know, or whose identity they can't verify per the article [Protect yourself from phishing](https://support.microsoft.com/windows/protect-yourself-from-phishing-0c7ea947-ba98-3bd9-7184-430e1f860a44).

- Users can choose to [accept or block messages](https://support.microsoft.com/office/accept-or-block-people-outside-your-org-who-send-you-a-chat-4b5b917d-895a-4379-a204-a111b2e24f41) when interacting with users they do not know or do not expect to be contacted by.

- To further protect against external attacks, tenant admins can disable interaction with external users through enterprise federation and Teams for Life (TFL) and Skype interoperability—see [Manage external access (federation) - Microsoft Teams | Microsoft Docs](/microsoftteams/manage-external-access).

The Teams collaboration feature set allows messaging, file collaboration, meetings, whiteboards, and many other opportunities to connect. These features work across Teams for Enterprise, Teams for Life, Skype, Skype for Business, Azure Communication Services (ACS), and more. That also means it’s necessary to protect yourself, your peers, and your customers across the breadth of these capabilities. Here, again, *every user should be empowered to make the safest decision for themselves, their peers, and their customers*.

## As with email messages, online safety must be practiced with Microsoft Teams messages

Standard safety measures should become ingrained while working in Teams.

1. Be wary of contacts and meeting requests from outside of your organization. Strangers can be well meaning. And some can secretly mean harm.
1. When you get new chat-based message from an external person that you haven't accepted any chat or interaction with before, you'll be presented with an option to [accept or block the communication request](https://support.microsoft.com/office/block-or-unblock-people-outside-your-org-in-microsoft-teams-5b590992-c938-4ed9-933b-37ee1fb84d32).
1. If you don’t recognize the sender, you can check the [profile card](https://support.microsoft.com/office/profile-cards-in-microsoft-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501). When in doubt, don't interact with unknown and unverified users.
1. If you receive a link or file from an unknown person, don't click on it. Again, use your best judgment for your own, other users', and your customers' safety.
1. If selecting a link lands you on a safe links page where you're blocked from navigation, don't try to circumvent that page. The same goes for selecting any attachment that may end in a red, blocking attachments safe page. Users, you can report that message [Report messages in Teams](https://support.microsoft.com/office/report-messages-in-microsoft-teams-c7a69a60-767b-4288-8713-7c28b4a73913) and admins can [Report the problem to Microsoft](/microsoft-365/security/office-365-security/submissions-admin). Users should remember to alert whomever directed them to the suspicious link so that they don't continue to send the problem link of attachment. Many reasons exist to land on a blocking page, so consider the red flags behind rather than to simply go around the blocking page.
1. Never give personal information out to any unsolicited requests. Providing personal information is also a risk to personal safety. Attackers can use details as simple as your birthday.
1. Scan your links for iffy spelling, added digits, or strange characters. You may be expecting a link to `www.litware.com/strategies/Metricsbreakout.xlsx`, but find that the address looks like `www.litwre.com`, `www.litwarecom.com`, or even `www.litwαre.com`. If you don’t recognize the link, be suspicious. The address `www.litware.com` isn't the same as `www.litware2021.com`.

Maintaining your vigilance is important. Don't take your security or the security of those you work with lightly or for granted. You should always feel empowered to protect yourself, your peers, and your customers by verifying before you trust.

**Finally, recognizing that everyone makes mistakes is critical**. Users are prone to clicking when in a hurry or tired, for example. Admins must provide users in their organization resources to escalate problem link clicks and other security incidents. Those resources need to be well known so that if a user makes a mistake, the person has recourse and more security actions they know how to take.

> [!TIP]
> Check the [Profile card](https://support.microsoft.com/office/profile-cards-in-microsoft-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501) of any contact you’re not sure about, particularly if the email is external to your company (for example, an account ending in *@litware.com* if your organization is not *Litware*). A user can verify that people they don't know are welcome Guests to a meeting by checking the Profile card for **(GUEST)**. Guests are expressly invited to participate.

## Also see

The [Teams Security Guide](/microsoftteams/teams-security-guide)
