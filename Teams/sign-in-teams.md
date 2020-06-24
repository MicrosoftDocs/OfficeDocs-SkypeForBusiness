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

Microsoft recommends that organizations use recent versions of Windows 10 with either Hybrid Domain Join or Azure AD Join configuration. This ensures that users’ accounts are primed in Windows’ Web Account Manager, which in turns enables single sign-on to Teams and other Microsoft applications. This provides a better user experience (silent sign-in) and a better security posture.

Microsoft Teams uses modern authentication to keep the sign-in experience simple and secure. To see how users sign in to Teams, read [Sign in to Teams](https://support.office.com/article/sign-in-to-teams-ea4b1443-d11b-4791-8ae1-9977e7723055).

## How modern authentication works

Modern authentication is a process that lets Teams know that users have already entered their credentials (like their work email and password) elsewhere, and they shouldn't be required to enter them again to start the app. The experience will vary depending on a couple factors, like if users are working in Windows or on a Mac. It will also vary depending on whether your organization has enabled single-factor authentication or multi-factor authentication (multi-factor authentication usually involves verifying credentials via a phone, providing a unique code, entering a PIN, or presenting a thumbprint). Here's a rundown of each modern authentication scenario.

### Windows users

- If users have already signed in to Windows or to other Office apps with their work or school account, when they start Teams they're taken straight to the app. There's no need for them to enter their credentials.

- Microsoft recommends using Windows 10 version 1903 or later for the best Single Sign-On experience.

- If users are not signed in to their Microsoft work or school account anywhere else, when they start Teams, they're asked to provide either single-factor or multi-factor authentication (SFA or MFA), depending on what your organization has decided they'd like the process to entail.

- If users are signed in to a domain-joined computer, when they start Teams, they might be asked to go through one more authentication step, depending on whether your organization opted to require MFA or if their computer already requires MFA to sign in. If their computer already requires MFA to sign in, when they open up Teams, the app automatically starts.

- On Domain joined PCs, when SSO isn't possible Teams may pre-fill its login screen with the user principal name (UPN). There are cases where you may not want this, especially if your organization uses different UPNs on-premises and in Azure Active Directory. If that's the case, you can use the following Windows registry key to turn off pre-population of the UPN:

  Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams<br/>
  SkipUpnPrefill(REG_DWORD)<br/>
  0x00000001 (1)

    > [!NOTE]
    > Skipping or ignoring user name pre-fill for user names that end in ".local" or ".corp" is on by default, so you don't need to set a registry key to turn these off.


### Mac users

On MacOS, Teams will prompt users to enter their username and credentials and may prompt for multi-factor authentication depending on your organization's settings. Once users enter their credentials, they won't be required to provide them again. From that point on, Teams automatically starts whenever they're working on the same computer.

## Teams for iOS and Android users

Upon sign in, mobile users will see a list of all the Microsoft 365 accounts that are either currently signed in or were previously signed in on their device. Users can tap on any of the accounts to sign in. There are two scenarios for mobile sign in:
    
1. If the selected account is currently signed in to other Office 365 or Microsoft 365 apps, then the user will be taken straight to Teams. There is no need for the user to enter their credentials.
    
2. If user isn't signed in to their Microsoft 365 account anywhere else, they will be asked to provide single-factor or multi-factor authentication (SFA or MFA), depending on what your organization has configured for mobile sign in policies.

### Adding multiple accounts to Teams

Teams for iOS and Android supports adding multiple accounts from a single device to Teams. The following images show how users can add multiple accounts in Teams.
    
:::image type="content" source="media/sign-in-multiple-accounts.png" alt-text="Adding multiple accounts in Teams":::

### Use enterprise mobility management to control which accounts can sign in to Teams

Teams for iOS and Android offers IT administrators the ability to push account configurations to Microsoft 365 accounts. This capability works with any Mobile Device Management (MDM) provider who uses the [Managed App Configuration](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html) channel for iOS or the [Android Enterprise](https://developer.android.com/work/managed-configurations) channel for Android.

For users enrolled in Microsoft Intune, you can deploy the account configuration settings using Intune in the Azure Portal.

Once account setup configuration has been setup in the MDM provider, and after the user enrolls their device, on the login pgae, Teams for iOS and Android will only show the allowed account(s) on the Teams login page. The user can tap on any of the allowed accounts on this page to sign in.

Set the following configuration parameters in the Azure Intune portal for managed devices.


|Platform |Key  |Value  |
|---------|---------|---------|
|iOS     |  **IntuneMAMAllowedAccountsOnly**       | **Enabled**: The only account allowed is the managed user account defined by the IntuneMAMUPN key.<br> **Disabled** (or any value that is not a case insensitive match to **Enabled**): Any account is allowed.        |
|iOS     |   **IntuneMAMUPN**      |   UPN of the account allowed to sign in to Teams.<br> For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account.       |
|Android     |**com.microsoft.intune.mam.AllowedAccountUPNs**         |    Only account(s) allowed are the managed user account(s) defined by this key.<br> One or more semi-colon [;]- delmited UPNs.<br> For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account.

Once the account setup configuration has been set, Teams will restrict the ability to sign in, so that only allowed accounts on enrolled devices will be granted access.

To create an app configuration policy for managed iOS/iPadOS devices, see [Add app configuration policies for managed iOS/iPadOS devices](https://docs.microsoft.com/en-us/mem/intune/apps/app-configuration-policies-use-ios).

To create an app configuration policy for managed Android devices, see [Add app configuration policies for managed Android devices](https://docs.microsoft.com/en-us/mem/intune/apps/app-configuration-policies-use-android).


## Switching accounts after completing modern authentication

If users are working on a domain-joined computer (for example, if their tenant has enabled Kerberos), they cannot switch user accounts once they've completed modern authentication. If users are not working on a domain-joined computer, they can switch accounts.

## Signing out of Teams after completing modern authentication

To sign out of Teams, users can click their profile picture at the top of the app, and then select **Sign out**. They can also right-click the app icon in their taskbar, and then select **Log out**. Once they've sign out of Teams, they need to enter their credentials again to launch the app.

### Signing out of Teams for iOS and Android

Mobile users can sign out of Teams by going to the menu and choosing the **More** menu, and then choosing **Sign out**. Once signed out, users will need to re-enter their credentials the next time they launch the app.

> [!NOTE]
> Teams for Android uses single sign-on (SSO) to simplify the sign in experience. Users should make sure to log out of **all** Microsoft apps, in addition to Teams, in order to completely log out on the Android platform.

## URLs and IP address ranges

Teams requires connectivity to the Internet. To understand endpoints that should be reachable for customers using Teams in Office 365 plans, Government and other clouds, read [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).

> [!IMPORTANT]
> Teams presently requires access (TCP port 443) to the Google ssl.gstatic.com service (<https://ssl.gstatic.com)> for all users; this is true even if you're not using Gstatic. Teams will remove this requirement soon (early 2020), and we'll update this article accordingly at that time.

## Troubleshooting modern authentication

Modern authentication is available for every organization that uses Teams, so if users are not able to complete the process, there might be something wrong with your domain or your organization's Microsoft work or school account.

For more information, see [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/why-am-i-having-trouble-signing-in-to-microsoft-teams-a02f683b-61a3-4008-9447-ee60c5593b0f)
