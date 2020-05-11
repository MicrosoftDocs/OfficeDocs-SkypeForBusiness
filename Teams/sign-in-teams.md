---
title: Sign in to Teams using modern authentication
author: LolaJacobsen
ms.author: lolaj
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: 
description: Learn how modern authentication works, how to switch accounts, and how to troubleshoot modern authentication. Includes how to tell Teams to ignore the prefill of the user's name (UPN) at sign in.
ms.custom: seo-marvel-apr2020
localization_priority: Priority
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
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

- If users are signed in to a domain-joined computer and you **don't want their user name pre-populated on the Teams sign-in screen**, admins can set the following Windows registry to turn off pre-population of the user name (UPN):

  Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams<br/>
  SkipUpnPrefill(REG_DWORD)<br/>
  0x00000001 (1)

    > [!NOTE]
    > Skipping or ignoring user name pre-fill for user names that end in ".local" or ".corp" is on by default, so you don't need to set a registry key to turn these off. 


### Mac users 

When users start Teams, their computer won't be able to pull their credentials from their Office 365 Enterprise account or any of their other Office applications. Instead, they'll see a prompt asking them for SFA or MFA (depending on your organization's settings). Once users enter their credentials, they won't be required to provide them again. From that point on, Teams automatically starts whenever they're working on the same computer.

## Switching accounts after completing modern authentication

If users are working on a domain-joined computer (for example, if their tenant has enabled Kerberos), they cannot switch user accounts once they've completed modern authentication. If users are not working on a domain-joined computer, they can switch accounts.

## Signing out of Teams after completing modern authentication
To sign out of Teams, users can click their profile picture at the top of the app, and then select **Sign out**. They can also right-click the app icon in their taskbar, and then select **Log out**. Once they've sign out of Teams, they need to enter their credentials again to launch the app.

## URLs and IP address ranges
Teams requires connectivity to the Internet. To understand endpoints that should be reachable for customers using Teams in Office 365 plans, Government and other clouds, read [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges). 

> [!IMPORTANT]
> Teams presently requires access (TCP port 443) to the Google ssl.gstatic.com service (https://ssl.gstatic.com) for all users; this is true even if you're not using Gstatic. Teams will remove this requirement soon (early 2020), and we'll update this article accordingly at that time.

## Troubleshooting modern authentication

Modern authentication is available for every organization that uses Teams, so if users are not able to complete the process, there might be something wrong with your domain or your organization's Office 365 Enterprise account. 

For more information, see [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/why-am-i-having-trouble-signing-in-to-microsoft-teams-a02f683b-61a3-4008-9447-ee60c5593b0f)

