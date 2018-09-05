---
title: Deploy Microsoft Teams for Surface Hub
author: ChuckEdmonson
ms.author: chucked
manager: serdars
ms.date: 08/29/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: jatpatel
description: Configure admin settings for Microsoft Teams for Surface Hub.
localization_priority: Normal
ms.custom:
- Devices
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Deploy Microsoft Teams for Surface Hub
======================================

Before you deploy Microsoft Teams for Microsoft Surface Hub, be sure you have met the hardware, operating system, and other requirements. For more information, see the [Microsoft Surface Hub admin guide](https://docs.microsoft.com/en-us/surface-hub/).

## Set up user accounts
 
To set up user accounts that can be used with Teams for Surface Hub, create the device account as you would for support with Skype for Business. The device account needs to have multi-factor authentication disabled (to allow automatic logon) for the following dependent services of Teams in Office 365:  
- Exchange 
- SharePoint 
- Office Apps 

## Add a device account 

1\. Start a remote Windows PowerShell session on a PC and connect to Exchange. Be sure you have the correct permissions set to run the associated cmdlets. The following are some examples of cmdlets that can be used and modified in your environment.

```
Set-ExecutionPolicy Unrestricted
$org='contoso.com'
$cred=Get-Credential $admin@$org
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ 
-Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2\. After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox. This will allow the account to authenticate to Teams.

If you are changing an existing resource mailbox:

```
Set-Mailbox -Identity 'TEAMS01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

If you’re creating a new resource mailbox:

```
New-Mailbox -MicrosoftOnlineServicesID TEAMS01@contoso.com -Alias TEAMS01 
-Name "Teams-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword
 (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3\. Various Exchange properties must be set on the device account to improve the meeting experience. You can see which properties need to be set in the Exchange properties section.

```
Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false
 -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Skype Meeting room!"
```

4\. You will need to connect to Azure Active Directory to apply some account settings. To connect to Azure AD, run the following cmdlet:

```
Connect-MsolService -Credential $cred
```

5\. If you do not want the password to expire, run the Set-MsolUser cmdlet with the PasswordNeverExpires option as follows: 

```
Set-MsolUser -UserPrincipalName $acctUpn -PasswordNeverExpires $true
```

You can also set a phone number for the room as follows:

```
Set-MsolUser -UniversalPrincipalName <upn> -PhoneNumber <phone number>
```

6\. The device account needs to have a valid Office 365 license, or Exchange and Skype for Business will not work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use Get-MsolAccountSku to retrieve a list of available SKUs for your Office 365 tenant as follows:
 
```
Get-MsolAccountSku
```

Next, you can add a license using the Set-MsolUserLicense cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK).

```
Set-MsolUser -UserPrincipalName $acctUpn -UsageLocation "US"
Get-MsolAccountSku
Set-MsolUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense
```

7\. Next, you need to enable the device account with Teams for Surface Hub. Be sure your environment meets the requirements defined in [Microsoft Surface Hub admin guide](https://docs.microsoft.com/en-us/surface-hub/).

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

1. Log on as a tenant administrator, open the Office 365 admin center, and click on the Admin app.
2. Click **Users and Groups**, and then click **Add users, reset passwords, and more**.
3. Select the Teams for Surface Hub account, and then click or tap the pen icon, which means edit.
4. Click the **Licenses** option.
5. In the **Assign licenses** section, you need to select the plan, depending on your licensing.
6. Click **Save** to complete the task.

## Install Teams for Surface Hub from the Microsoft Store 

These instructions are for installing Teams for Surface Hub from the Microsoft Store. 
 
1. Start the Microsoft Store:<br>
   a. Tap **Start** > **All Apps** > **Settings**.<br> 
   b. Tap **Surface Hub Device account, management**.<br>
   c. On the left, tap the **Apps & Features** tab.<br> 
   d. On the right, tap the **Open Store** button. 
2. From the Microsoft Store, search for *Microsoft Teams*. The **Microsoft Teams for Surface Hub** will be displayed. Tap the **Get the app** button to install.  
3. When the installation is complete, restart the Surface Hub. 

> [!NOTE]
> Do not tap on **Launch** from the Store listing page.

## Make Teams the default calling and meetings application
 
There are two options for configuring the default calling and meetings application policy: 

- **Option 1**: Configure via USB key. 
- **Option 2**: Configure via MDM such as Intune.
 
### Option 1: Configure via USB key 
 
The packages can be found on this [download page](https://1drv.ms/f/s!ArcnbnREun0Vnp9Wps9MlWB-UJZw3g). Pick the appropriate one for the package that you're planning to install and copy it to a USB key. The correct .ppkg file to use depends on the default application policy you'd like to apply as follows: 

|Number  |Description  |
|---------|---------|
|0     | Skype preferred app on the Start Screen, Teams Meetings available        |
|1     | Teams preferred app on the Start Screen, Skype Meetings available        |
|2     | Teams exclusive app on the Start screen (Skype app not available)        |
 
1. Attach the USB key to the Surface Hub device. 
2. Open the **Settings** app on a Surface Hub device. 
3. Open **Surface Hub Device Account Management**.
4. Open **Device Management**. 
5. Click **Add or Remove a provisioning package**. 
6. Click **Add Package**.
7. Select the **Removable Media** option from the drop-down menu. 
8. Add the appropriate **TeamsRTMMode*.ppkg** package that was previously copied to the USB key. 
9. Restart the Surface Hub device. 
10. After the device restarts, you should be able to start the Teams app from the Start screen and join a meeting from the calendar. 

### Option 2: Configure via MDM such as Intune 

Use the following to configure the default calling and meetings application policy via Intune.

.

|Setting   |Value    |Description    |
|----------|---------|---------|
|Path      | ./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode        |
|Data Type | integer (0-2)   |0 - Skype preferred app on the Start Screen, Teams Meetings available<br>1 - Teams preferred app on the Start Screen, Skype Meetings available<br>2 - Teams exclusive app on the Start screen (Skype app not available) |
|Operations| Get, Set        |

|Setting   |Value    |
|----------|---------|
|Path      | ./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId        |
|Data Type | string - set string to Teams application package ID as **Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams** |
|Operations| Get, Set        |

Restart the Surface Hub device. After the device restarts, you should be able to start the Teams app from the Start screen and join a meeting from the calendar.

