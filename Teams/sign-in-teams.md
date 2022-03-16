---
title: Sign in to Microsoft Teams
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
audience: Admin
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: anwara
description: Learn how modern authentication works, how to switch accounts, and how to troubleshoot modern authentication. Includes how to tell Teams to ignore the pre-fill of the user's name (UPN) at sign-in.
ms.custom: seo-marvel-apr2020
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# Sign in to Microsoft Teams

## Windows users

Microsoft recommends that organizations use recent versions of Windows 10 with either Hybrid Domain Join or Azure AD Join configuration. Using recent versions ensures that users’ accounts are primed in Windows’ Web Account Manager, which in turn enables single sign-on to Teams and other Microsoft applications. Single sign-on provides a better user experience (silent sign-in) and a better security posture.

Microsoft Teams uses modern authentication to keep the sign-in experience simple and secure. To see how users sign in to Teams, read [Sign in to Teams](https://support.office.com/article/sign-in-to-teams-ea4b1443-d11b-4791-8ae1-9977e7723055).

### How modern authentication works

Modern authentication is a process that lets Teams know that users have already entered their credentials, such as their work email and password elsewhere, and they shouldn't be required to enter them again to start the app. The experience varies depending on a couple factors, like if users are working in Windows or on a Mac. It will also vary depending on whether your organization has enabled single-factor authentication or multifactor authentication. Multifactor authentication usually involves verifying credentials via a phone, providing a unique code, entering a PIN, or presenting a thumbprint. Here's a rundown of each modern authentication scenario.

Modern authentication is available for every organization that uses Teams. If users aren't able to complete the process, there might be an underlying issue with your organization's Azure AD configuration. For more information, see [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/why-am-i-having-trouble-signing-in-to-microsoft-teams-a02f683b-61a3-4008-9447-ee60c5593b0f)

- If users have already signed in to Windows or to other Office apps with their work or school account, when they start Teams they're taken straight to the app. There's no need for them to enter their credentials.

- Microsoft recommends using Windows 10 version 1903 or later for the best Single Sign-On experience.

- If users are not signed in to their Microsoft work or school account anywhere else, when they start Teams, they're asked to provide either single-factor or multifactor authentication (SFA or MFA). This process depends on what your organization has decided they'd like the sign-in procedure to require.

- If users are signed in to a domain-joined computer, when they start Teams, they might be asked to go through one more authentication step, depending on whether your organization opted to require MFA or if their computer already requires MFA to sign in. If their computer already requires MFA to sign in, when they open up Teams, the app automatically starts.

- On Domain joined PCs, when SSO isn't possible Teams may pre-fill its login screen with the user principal name (UPN). There are cases where you may not want this, especially if your organization uses different UPNs on-premises and in Azure Active Directory. If that's the case, you can use the following Windows registry key to turn off pre-population of the UPN:

  Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams<br/>
  SkipUpnPrefill(REG_DWORD)<br/>
  0x00000001 (1)

    > [!NOTE]
    > Skipping or ignoring user name pre-fill for user names that end in ".local" or ".corp" is on by default, so you don't need to set a registry key to turn these off.

### Signing in to another account on a Domain Joined computer

Users on domain-joined computer may not be able to sign in to Teams with another account in the same Active Directory domain.

## macOS users

On macOS, Teams will prompt users to enter their username and credentials and may prompt for multifactor authentication depending on your organization's settings. Once users enter their credentials, they won't be required to provide them again. From that point on, Teams automatically starts whenever they're working on the same computer.

## Teams on iOS and Android users

Upon sign in, mobile users will see a list of all the Microsoft 365 accounts that are either currently signed-in or were previously signed-in on their device. Users can tap on any of the accounts to sign in. There are two scenarios for mobile sign in:

1. If the selected account is currently signed in to other Office 365 or Microsoft 365 apps, then the user will be taken straight to Teams. There's no need for the user to enter their credentials.

2. If user isn't signed in to their Microsoft 365 account anywhere else, they will be asked to provide single-factor or multifactor authentication (SFA or MFA), depending on what your organization has configured for mobile sign-in policies.

> [!NOTE]
> For users to experience the sign on experience as described in this section, their devices must be running Teams for iOS version 2.0.13 (build 2020061704) or later, or Teams for Android version 1416/1.0.0.2020061702 or later.

## Using Teams with multiple accounts

Teams for iOS and Android supports the use of multiple work or school and multiple personal accounts side by side. Teams desktop applications will support one work/school and one personal account side by side in December 2020, with support for multiple work/school accounts coming at a later date.

The following images show how users can add multiple accounts in Teams mobile applications.

:::image type="content" source="media/sign-in-multiple-accounts.png" alt-text="Adding multiple accounts in Teams.":::

## Restrict sign in to Teams

Organization may want to restrict how corporate-approved apps are used on managed devices, for example to restrict students' or employees’ ability to access data from other organizations or use corporate-approved apps for personal scenarios. These restrictions can be enforced by setting Devices Policies that Teams applications recognize.

### How to restrict sign in on mobile devices

Teams for iOS and Android offers IT administrators the ability to push account configurations to Microsoft 365 accounts. This capability works with any Mobile Device Management (MDM) provider that uses the [Managed App Configuration](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html) channel for iOS or the [Android Enterprise](https://developer.android.com/work/managed-configurations) channel for Android.

For users enrolled in Microsoft Intune, you can deploy the account configuration settings using Intune in the Azure portal.

Once account setup configuration has been configured in the MDM provider, and after the user enrolls their device, on the sign-in page, Teams for iOS and Android will only show the allowed account(s) on the Teams sign-in page. The user can tap on any of the allowed accounts on this page to sign in.

Set the following configuration parameters in the Azure Intune portal for managed devices.

|Platform |Key  |Value  |
|---------|---------|---------|
|iOS     |  **IntuneMAMAllowedAccountsOnly**       | **Enabled**: The only account allowed is the managed user account defined by the IntuneMAMUPN key.<br> **Disabled** (or any value that is not a case insensitive match to **Enabled**): Any account is allowed.        |
|iOS     |   **IntuneMAMUPN**      |   UPN of the account allowed to sign in to Teams.<br> For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account.       |
|Android     |**com.microsoft.intune.mam.AllowedAccountUPNs**         |    Only account(s) allowed are the managed user account(s) defined by this key.<br> One or more semi-colons;]- delimited UPNs.<br> For Intune enrolled devices, the {{userprincipalname}} token may be used to represent the enrolled user account.

Once the account setup configuration has been set, Teams will restrict the ability to sign in, so that only allowed accounts on enrolled devices will be granted access.

To create an app configuration policy for managed iOS/iPadOS devices, see [Add app configuration policies for managed iOS/iPadOS devices](/mem/intune/apps/app-configuration-policies-use-ios).

To create an app configuration policy for managed Android devices, see [Add app configuration policies for managed Android devices](/mem/intune/apps/app-configuration-policies-use-android).

### How to restrict sign in on desktop devices

Teams apps on Windows and macOS are gaining support for device policies that restrict sign in to your organization. The policies can be set via usual Device Management solutions such as MDM (Mobile Device Management) or GPO (Group Policy Object). 

When this policy is configured on a device, users can only sign in with accounts homed in an Azure AD tenant that is included in the “Tenant Allow List” defined in the policy. The policy applies to all sign-ins, including first and additional accounts. If your organization spans multiple Azure AD tenants, you can include multiple Tenant IDs in the Allow List. Links to add another account may continue to be visible in the Teams app, but they won't be operable.

> [!NOTE]
> 
>1. The policy only restricts sign-ins. It does not restrict the ability for users to be invited as a guest in other Azure AD tenants, or switch to those other tenants (where users have been invited as a guest).
>2. The policy requires Teams for Windows version 1.3.00.30866 or higher, and Teams for macOS version 1.3.00.30882 (released mid-November 2020).

**Policies for Windows**
Administrative Template files (ADMX/ADML) are available from the [Download center](https://www.microsoft.com/download/details.aspx?id=49030) (the policy setting descriptive name in the administrative template file is "Restrict sign in to Teams to accounts in specific tenants"). Additionally, you can manually set keys in Windows Registry:

- Value Name: RestrictTeamsSignInToAccountsFromTenantList
- Value Type: String
- Value Data: Tenant ID, or comma-separated list of Tenant IDs
- Path: use one of the following

 Computer\HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Cloud\Office\16.0\Teams
 Computer\HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Teams
 Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Teams

Example:
SOFTWARE\Policies\Microsoft\Office\16.0\Teams\RestrictTeamsSignInToAccountsFromTenantList = Tenant ID
or
SOFTWARE\Policies\Microsoft\Office\16.0\Teams\RestrictTeamsSignInToAccountsFromTenantList = Tenant ID 1,Tenant ID 2,Tenant ID 3

**Policies for macOS**
For macOS managed devices, use .plist to deploy sign-in restrictions. The configuration profile is a .plist file that consists of entries identified by a key (which denotes the name of the preference), followed by a value, which depends on the nature of the preference. Values can either be simple (such as a numerical value) or complex, such as a nested list of preferences.

- Domain: com.microsoft.teams
- Key: RestrictTeamsSignInToAccountsFromTenantList
- Data Type: String
- Comments: Enter comma separate list of Azure AD tenant ID(s)

### Global sign in

The Teams Android app now supports Global sign-in, to provide a hassle free sign-in experience for Frontline Workers. Employees can pick a device from the shared device pool and do a single sign in to "make it theirs" for the duration of their shift. At the end of their shift, they should be able to perform sign out to globally sign out on the device. See [Sign out of Teams](sign-out-of-teams.md) to learn more. This will remove all of their personal and company information from the device so they can return the device to the device pool. To get this capability, the device must be in shared mode. Make sure to end any active meeting or call on the device before signing out. To learn how to set up a shared device, see [How to use a shared device mode in Android](/azure/active-directory/develop/tutorial-v2-shared-device-mode#set-up-an-android-device-in-shared-mode).

The sign-in experience looks similar to our standard Teams sign-in experience.

## URLs and IP address ranges

Teams requires connectivity to the Internet. To understand endpoints that should be reachable for customers using Teams in Office 365 plans, Government, and other clouds, read [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges).


## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
