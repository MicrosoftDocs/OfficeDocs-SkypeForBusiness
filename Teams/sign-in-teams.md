---
title: Sign in to Microsoft Teams using modern authentication
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 11/15/2018
audience: Admin
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: 
description: How to sign in to Microsoft Teams by using modern authentication.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Sign in to Microsoft Teams using modern authentication
==========================

Microsoft Teams uses modern authentication to keep the sign-in experience simple and secure. To see how users sign in to Teams, read [Sign in to Teams](https://support.office.com/article/sign-in-to-teams-ea4b1443-d11b-4791-8ae1-9977e7723055).

## How modern authentication works

Modern authentication is a process that lets Teams know that users have already entered their credentials (like their work email and password) elsewhere, and they shouldn't be required to enter them again to start the app. The experience will vary depending on a couple factors, like if users are working in Windows or on a Mac. It will also vary depending on whether your organization has enabled single-factor authentication or multi-factor authentication (multi-factor authentication usually involves verifying credentials via a phone, providing a unique code, entering a PIN, or presenting a thumbprint). Here's a rundown of each modern authentication scenario.

### Windows users 

- If users have already signed in to other Office apps through their Office 365 Enterprise account, when they start Teams they're taken straight to the app. There's no need for them to enter their credentials.

- If users are not signed in to their Office 365 Enterprise account anywhere else, when they start Teams, they're asked to provide either single-factor or multi-factor authentication (SFA or MFA), depending on what your organization has decided they'd like the process to entail.

- If users are signed in to a domain-joined computer, when they start Teams, they might be asked to go through one more authentication step, depending on whether your organization opted to require MFA or if their computer already requires MFA to sign in. If their computer already requires MFA to sign in, when they open up Teams, the app automatically starts.

### Mac users 

When users start Teams, their computer won't be able to pull their credentials from their Office 365 Enterprise account or any of their other Office applications. Instead, they'll see a prompt asking them for SFA or MFA (depending on your organization's settings). Once users enter their credentials, they won't be required to provide them again. From that point on, Teams automatically starts whenever they're working on the same computer.

## Switching accounts after completing modern authentication

If users are working on a domain-joined computer (for example, if their tenant has enabled Kerberos), they cannot switch user accounts once they've completed modern authentication. If users are not working on a domain-joined computer, they can switch accounts.

## Signing out of Microsoft Teams after completing modern authentication
To sign out of Teams, users can click their profile picture at the top of the app, and then select **Sign out**. They can also right-click the app icon in their taskbar, and then select **Log out**. Once they've sign out of Teams, they need to enter their credentials again to launch the app.

## Troubleshooting modern authentication

Modern authentication is available for every organization that uses Teams, so if users are not able to complete the process, there might be something wrong with your domain or your organization's Office 365 Enterprise account. 

For more information, see [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/why-am-i-having-trouble-signing-in-to-microsoft-teams-a02f683b-61a3-4008-9447-ee60c5593b0f).

