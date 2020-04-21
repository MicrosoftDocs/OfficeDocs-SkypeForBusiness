---
title: Create a resource account using UI
description: If you prefer to use a graphical user interface, you can create a resource account for your Microsoft Teams Rooms and collaboration bars for Microsoft Teams using the Microsoft 365 Admin Center.
ms.assetid: 
ms.reviewer: 
manager: 
keywords: create device account, Microsoft 365 UI, Microsoft 365 admin center
ms.prod: teams-rooms
ms.sitesec: library
author: mitressl
ms.author: mitressl
ms.topic: article
ms.date: 04/10/2020
ms.localizationpriority: medium
---

# Create a resource account using UI


If you prefer to use a graphical user interface, you can create a device account for your Microsoft Teams Room and collaboration bars with either the [Microsoft 365 UI](#create-device-acct-m365) or the [Exchange Admin Center](#create-device-acct-eac).

## <a href="" id="create-device-acct-m365"></a>Create a device account using Microsoft 365 admin center


1.  [Create the account in the Microsoft 365 admin center](#create-device-acct-m365-admin-ctr).
3.  [Use PowerShell to complete device account creation](#create-device-acct-m365-complete-acct).
4.  [Use PowerShell to configure Exchange properties of the account](#create-device-acct-m365-configure-exch-prop).
5.  [Enable the account with Skype for Business](#create-device-acct-m365-skype-for-business).

### <a href="" id="create-device-acct-m365-admin-ctr"></a>Create the account in the Microsoft 365 admin center

1.  Sign in to Office 365 by visiting https://admin.microsoft.com
2.  Provide the admin credentials for your Microsoft 365 tenant. This will take you to your Microsoft 365 admin center.

    ![Microsoft 365 admin center.](images/setupdeviceaccto365-02.png)

3. In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.

    ![Rooms & equipment option in admin center](images/room-equipment.png)

4. Click **Add** to create a new room account. Enter a display name and email address for the account, and then click **Add**.

    ![Create new room account window](images/room-add.png)

5. Navigate to the Users section in admin center and, in the Active Users list, select the room account you just created. In the right panel, you can see the account properties and several optional actions. Click the **Reset password** key icon under the username to change the password. Unselect **Make this user change their password when they first sign in**. It is not possible to change the password via the device sign-in process.

6. In the **Licenses and Apps** section, scroll down, and check the box next to the license to be assigned - such as Meeting Room - and then click **Save changes**. The license may vary depending on your organization.

### <a href="" id="create-device-acct-o365-skype-for-business"></a>Enable the account with Skype for Business

Enable the resource account with Skype for Business.

In order to enable Skype for Business Online, your environment will need to meet the following prerequisites:

-   You'll need to have Skype for Business Online Standalone Plan 2 or higher in your Microsoft 365 plan. The plan needs to support conferencing capability.
-   If you need Enterprise Voice (PSTN telephony) using telephony service providers, you need Skype for Business Online Standalone Plan 3.
-   Your tenant users must have Exchange mailboxes.
-   You are required to have a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.

1.  Start by creating a remote PowerShell session from a PC.

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $UserCredential=New-CsOnlineSession -Credential $cred
    Import-PSSession $UserCredential -AllowClobber
    ```

2.  First you need to find the `RegistrarPool` parameter in your environment. You can get the value from an existing Skype for Business user using this cmdlet:

    ```PowerShell
    $account = get-csonlineuser '<Your resource accounts UPN>'
    ```
To enable your resource account for Skype for Business Online, run this cmdlet:

    ```PowerShell
    Enable-CsMeetingRoom -Identity $Account.UserPrincipalName -RegistrarPool $Account.RegistrarPool -SipAddressType EmailAddress
    ```