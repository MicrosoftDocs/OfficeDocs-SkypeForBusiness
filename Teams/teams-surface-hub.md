---
title: Microsoft Teams on Surface Hub - Admin Help
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/20/2018
ms.topic: article
ms.service: msteams
ms.reviewer: jatpatel
description: Configure admin settings for Microsoft Teams on Surface Hub.
ms.custom:
- Devices
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Microsoft Teams on Surface Hub - Admin Help
===========================================
> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]


> [!NOTE]
> This feature is currently in preview and could change as it is released or updated. 

Before you deploy Microsoft Teams for Surface Hub, be sure you have met the hardware, operating system, and other requirements. For more information, see the [Microsoft Surface Hub admin guide](https://docs.microsoft.com/en-us/surface-hub/).

## Set up user accounts
 
To set up user accounts that can be used with Teams for Surface Hub, create the device account as you would for support with Skype for Business. The device account needs to have multi-factor authentication disabled (to allow automatic logon) for the following dependent services of Teams in Office 365:  
- Exchange 
- SharePoint 
- Office Apps 

### Add a device account 

1. Start a remote Windows PowerShell session on a PC and connect to Exchange. Be sure you have the correct permissions set to run the associated cmdlets. The following are some examples of cmdlets that can be used and modified in your environment.

```
Set-ExecutionPolicy Unrestricted
$org='contoso.com'
$cred=Get-Credential $admin@$org
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ 
-Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2. After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox. This will allow the account to authenticate to Teams.

If you are changing an existing resource mailbox:

```
Set-Mailbox -Identity 'PROJECTRIGEL01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

If you’re creating a new resource mailbox:

```
New-Mailbox -MicrosoftOnlineServicesID PROJECTRIGEL01@contoso.com -Alias PROJECTRIGEL01 
-Name "Project-Rigel-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword
 (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3. Various Exchange properties must be set on the device account to improve the meeting experience. You can see which properties need to be set in the Exchange properties section.

```
Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false
 -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Skype Meeting room!"
```

4. You will need to connect to Azure Active Directory to apply some account settings. To connect to Azure AD, run the following cmdlet:

```
Connect-MsolService -Credential $cred
```

5. If you do not want the password to expire, run the Set-MsolUser cmdlet with the PasswordNeverExpires option as follows: 

```
Set-MsolUser -UserPrincipalName $acctUpn -PasswordNeverExpires $true
```

You can also set a phone number for the room as follows:

```
Set-MsolUser -UniversalPrincipalName <upn> -PhoneNumber <phone number>
```

6. The device account needs to have a valid Office 365 license, or Exchange and Skype for Business will not work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use Get-MsolAccountSku to retrieve a list of available SKUs for your Office 365 tenant as follows:
 
```
Get-MsolAccountSku
```

Next, you can add a license using the Set-MsolUserLicense cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK).

```
Set-MsolUser -UserPrincipalName $acctUpn -UsageLocation "US"
Get-MsolAccountSku
Set-MsolUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense
```

7. Next, you need to enable the device account with Teams for Surface Hub. Be sure your environment meets the requirements defined in [Microsoft Surface Hub admin guide](https://docs.microsoft.com/en-us/surface-hub/).

Start a remote Windows PowerShell session as follows (be sure to install Skype for Business Online PowerShell components):

```
Import-Module LyncOnlineConnector
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

Next, enable your Teams for Surface Hub account by running the following cmdlet:

```
Enable-CsMeetingRoom -Identity $rm -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
```

Obtain the RegistrarPool information from the new user account being setup, as shown in this example:

```
Get-CsOnlineUser -Identity $rm | Select -Expand RegistrarPool
```

> [!NOTE]
> New user accounts might not be created on the same registrar pool as existing user accounts in the tenant. The command above will prevent errors in account setup due to this situation. 

After you've completed the preceding steps to enable your Teams for Surface Hub account, you need to assign a license to the Surface Hub v2 device. Using the Office 365 administrative portal, assign a Teams for Surface Hub license to the device.

### Assign a license to the account

1. Log on as a tenant administrator, open the Office 365 Administrative Portal, and click on the Admin app.
2. Click **Users and Groups**, and then click **Add users, reset passwords, and more**.
3. Select the Teams for Surface Hub account, and then click or tap the pen icon, which means edit.
4. Click the **Licenses** option.
5. In the **Assign licenses** section, you need to select the plan, depending on your licensing.
6. Click **Save** to complete the task.

## Install Teams for Surface Hub from the Microsoft Store 

These instructions include the current workarounds for installing Teams for Surface Hub from the Microsoft Store. 
 
1. Start the Windows Store:
   a. Tap **Start** > **All Apps** > **Settings**. 
   b. Tap **Surface Hub Device account, management**. 
   c. On the left, tap the **Apps & Features** tab. 
   d. On the right, tap the **Open Store** button. 
2. Open the Edge browser. 
3. In the location bar of Edge, type in one of the following ms-windows-store protocol links to see Teams for Surface Hub in the Microsoft Store. 

|Build      | ms-windows-store protocol link  |
|-----------|---------|
|Dev        | ms-windows-store://pdp/?productid=9N8NWZVTB53S  |
|Dogfood    | ms-windows-store://pdp/?productid=9MVV3NT3WPJ2  |
|Tap        | ms-windows-store://pdp/?productid=9NGRP1GCM35Q  |
|Production | ms-windows-store://pdp/?productid=9PCZM4LGF8S6  |

4. The Microsoft Store should appear showing the version you linked above for Microsoft Teams for Surface Hub. Tap the **Get the app** button to install. 
5. When the installation is complete, restart the Surface Hub. 
6. After the Surface Hub restarts, you should be able to start the Teams app from the **Start** menu and join a meeting from the calendar. 

## Make Teams the default VTC application

Teams can be set up to be the default VTC application instead of Skype for Business. A Mobile Device Management (MDM) policy needs to be applied to the Surface Hub device. 
 
There are two options for configuring MDM policies: 

- If you have a policy configured, add it via the Device management app. 
- If you do not have a remote policy configured, we have a provisioned package file that you can load onto an USB key.

### Device management configuration

The following is an example of adding an MDM policy configured from a central MDM authority. If you are on the corporate network, you can follow the below instructions verbatim, including user account. 
 
1. Under the **Device Management** section, tap **+**.<br>
   The **Connect to work or school** dialog box will open. 
2. Enter the policy e-mail address and password when prompted.<br>
   There's a bug in the OS that doesn't automatically refresh the UI after you've entered your device management account. You'll need to close and re-open settings in order to see the account listed. 
3. It'll take a few minutes for the MDM policy settings to sync. If you want to force a sync, tap the **MDM account** button, and then tap the **Info** button. This will bring up the Info window where you can then tap **Sync**. 
4. To verify that you have what you need, you can check the registry. You should see two keys under **HKLM\Software\Microsoft\Windows\CurrentVersion\PPI\VtcCallSettings**. <br><br>
   The **VtcAppMeetingHandlingMode** DWORD value indicates that Teams is the default app. The following values are recognized. <br><br>
    |Number | Value   |
    |-------|---------|
    |0      | SkypePreferred            |
    |1      | VtcPreferred (Teams)      |
    |2      | VtcExclusive (Teams only) |

    The **VtcCallAppPackageId** is the name of the installed Teams package. If this doesn't show up, make sure you've installed the Teams package, and re-sync. 
 
### Configure MDM via USB key 
 
The packages can be found at \\scratch2\scratch\TeamsOnShub\ppkg. Pick the appropriate one for the package that you're planning to install and copy it to a USB key. The correct .ppkg file to use depends on the Teams package that has been installed from the store (either Dev or Dogfood), and the policy you'd like to apply (Skype exclusive, Skype preferred, Teams preferred, Teams exclusive). 
 
1. Attach the USB with the .ppkg file in its root folder to a Surface Hub device's USB port where you want to apply the new configuration. 
2. Open the **Settings** app on a Surface Hub device. 
3. Click the **Add Package** button. 
4. Select the **Removable Media** option from the drop-down menu. 
5. Select the .ppkg file name from where you want to apply the new configuration to this device.


 
 

