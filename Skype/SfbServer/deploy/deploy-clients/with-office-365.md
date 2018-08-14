---
title: "Deploy Skype Room Systems v2 with Office 365"
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Priority
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: "Read this topic for information on how to deploy Skype Room Systems v2 with Office 365."
---

# Deploy Skype Room Systems v2 with Office 365
 
Read this topic for information on how to deploy Skype Room Systems v2 with Office 365, where Skype for Business and Exchange are both online. 

The easiest way to set up user accounts is to configure them using remote Windows PowerShell. Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Skype Room Systems v2 user accounts. If you prefer, you can follow the steps below to configure accounts your Skype Room Systems v2 device will use.
  
## Deploy Skype Room Systems v2 with Office 365

Before you deploy Skype Room Systems v2 with Office 365, be sure you have met the requirements. For more information, see [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md).
  
To enable Skype for Business, you must have the following:
  
- Skype for Business Online (Plan 2) or higher in your Office 365 plan. The plan needs to support conferencing capability.
    
- If you need Enterprise Voice (PSTN telephony) using telephony service providers for Skype Room Systems v2 you need Skype for Business Online (Plan 3).
    
- Your tenant users must have Exchange mailboxes.
    
- Your Skype Room Systems v2 account does require a Skype for Business Online (Plan 2) or Skype for Business Online (Plan 3) license, but it does not require an Exchange Online license.

For details on Skype for Business Online Plans, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx).

<!-- 
## Meetings Feature support

This table covers features related to Meetings support.
  
> [!NOTE]
>  Skype for Business meeting features aren't available in Skype for Business Online Standalone Plan 1.

In Skype-to-Skype sessions, a Skype for Business Online Plan 1 user can participate in desktop sharing and application sharing if they're invited by a user who has access to sharing features.   
For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx) 

**Using Skype Room Systems** 
|Feature/capability | Skype for Business Online Plan 1 | Skype for Business Online Plan 2 | Skype for Business Online Plan 3 | Skype for Business Online Plan 1 | Skype for Business Online Plan 1 |  
|:-----|:-----|:-----|:-----|:-----|:-----|  
|Add computer audio | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|  
|Add video   |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|View multiparty video (gallery view)   |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Video-based screen sharing   |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Use in-meeting presenter controls|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Access detailed meeting roster|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Participate in multiparty IM| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Share the desktop (if enabled)| | &#x2714;|&#x2714; | &#x2714; |&#x2714; |
|Share a program (if enabled) |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;   |
|Add anonymous participants (if enabled)|   | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Use dial-in audio meetings|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Initiate a Meet Now meeting|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Add and present Microsoft PowerPoint files|| &#x2714;|&#x2714; | &#x2714; |&#x2714; |
|Navigate Microsoft PowerPoint files| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Add and edit OneNote meeting notes | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Use a whiteboard |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Conduct polls |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Upload files to share with others|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Schedule a meeting or conference | Outlook or Skype for Business Web Scheduler   |
|Q&amp;A Manager   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Disable attendee video   || &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Disable meeting IM   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Mute Audience|| &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Make everyone an attendee|  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Produce Skype Meeting Broadcast| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Delegate can schedule a meeting on behalf of delegator || &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Synchronize delegates between Skype for Business and Outlook| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Video Based Screen Sharing| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Set Video Spotlight (lock video)| | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Give/Take control of screen sharing | | &#x2714;|&#x2714; | &#x2714; |&#x2714;||
   
  
## Voice (Telephony) support


This table covers features related to voice services support.
  
> [!NOTE]
> Skype for Business Voice (Telephony) features are limited to certain Skype for Business Online subscription plans. > For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx). 
  
|Feature/capability | Skype for Business Online Plan 1 | Skype for Business Online Plan 2 | Skype for Business Online Plan 3 | Skype for Business Online Plan 1 | Skype for Business Online Plan 1 | 
|:-----|:-----|:-----|:-----|:-----|:-----| 
|feature| | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Initiate a call   || &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Click to call a contact   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Transfer a call || &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Manage call forwarding || &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Manage team call settings | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Manage delegates   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Initiate a call to a Response Group | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Support emergency services (E-911)| | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|IM notification to SIP URI(s) for E-911 call   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|IM notification to distribution list for E-911 call   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Connect to voice mail, set up or change greeting   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Missed call notification |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Make calls on behalf of another contact (manager/delegate scenario)   | | &#x2714;|&#x2714; | &#x2714; |&#x2714;
|Handle another's calls if configured as a delegate | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Manage a high volumes of calls | | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Call park |  | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Group call pickup |   | &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Location-based routing   || &#x2714;|&#x2714; | &#x2714; |&#x2714;|
|Manage Response Group/Team call group|| &#x2714;|&#x2714; | &#x2714; |&#x2714;|
   

   --> 
### Add a device account

1. Start a remote Windows PowerShell session on a PC and connect to Exchange. Be sure you have the right permissions set to run the associated cmdlets. The following are some examples of cmdlets that can be used and modified in your environment.
    
   ```
   Set-ExecutionPolicy Unrestricted
   $org='contoso.com'
   $cred=Get-Credential $admin@$org
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential 
   $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```

2. After establishing a session, you'll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox. This will allow the account to authenticate to Skype Room Systems v2.
    
  If you are changing an existing resource mailbox:
    
```
Set-Mailbox -Identity 'PROJECTRIGEL01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

  If you're creating a new resource mailbox:
    
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
   Set-MsolUser -UserPrincipalName <upn> -PhoneNumber <phone number>
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

7. Next, you need to enable the device account with Skype for Business. Be sure your environment meets the requirements defined in [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md).
    
   Start a remote Windows PowerShell session as follows (be sure to install Skype for Business Online PowerShell components):
    
   ```
   Import-Module LyncOnlineConnector  
   $cssess=New-CsOnlineSession -Credential $cred  
   Import-PSSession $cssess -AllowClobber
   ```

   Next, enable your Skype Room Systems v2 account for Skype for Business Server by running the following cmdlet:
    
   ```
   Enable-CsMeetingRoom -Identity $rm -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```

   Obtain the RegistrarPool information from the new user account being setup, as shown in this example:
    
    ```
    Get-CsOnlineUser -Identity $rm | Select -Expand RegistrarPool
    ```

    > [!NOTE]
    > New user accounts might not be created on the same registrar pool as existing user accounts in the tenant. The command above will prevent errors in account setup due to this situation. 
  
After you've completed the preceding steps to enable your Skype Room Systems v2 account in Skype for Business Online, you need to assign a license to Skype Room Systems v2 device. Using the Office 365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.
  
### Assign a license to your account

1. Login as a tenant administrator, open the Office 365 Administrative Portal, and click on the Admin app.
    
2. Click **Users and Groups** and then click **Add users, reset passwords, and more**.
    
3. Select the Skype Room Systems v2 account, and then click or tap the pen icon, which means edit.
    
4. Click on the **Licenses** option.
    
5. In the **Assign licenses** section, you need to select Skype for Business Online (Plan 2) or Skype for Business Online (Plan 3), depending on your licensing and what you've decided in terms of needing Enterprise Voice. You'll have to use a Plan 3 license if you want to use Cloud PBX on Skype Room Systems v2. Minimally you will need CloudPBX for voice connectivity. Then configure hybrid voice or PSTN calling based on the PSTN connectivity method.
    
6. Click **Save** to complete the task.
    
## Sample: Room account setup in Exchange Online and Skype for Business Online

```
New-Mailbox -MicrosoftOnlineServicesID Rigel1@contoso.com
 -Alias rigel1 -Name "Rigel 1" -Room -EnableRoomMailboxAccount $true
 -RoomMailboxPassword (ConvertTo-SecureString -String "" -AsPlainText -Force)
 
Set-CalendarProcessing -Identity rigel1 -AutomateProcessing AutoAccept 
-AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments 
$false -DeleteSubject $false -RemovePrivateProperty $false
 
Set-CalendarProcessing -Identity rigel1 -AddAdditionalResponse $true 
-AdditionalResponse "This is a Rigel room!"
 
Set-MsolUser -UserPrincipalName rigel1@contoso.com -PasswordNeverExpires $true -UsageLocation "US"
 
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:O365_BUSINESS_PREMIUM"
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOEV"
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOPSTN2"
 
Enable-CsMeetingRoom -Identity rigel1@contoso.onmicrosoft.com -RegistrarPool sippooldm21a05.infra.lync.com
-SipAddressType EmailAddress

```

> [!NOTE]
> This adds CloudPBX and PSTNCallingDomesticAndInternational. Addtionally, you will need to use the Admin interface to assign a phone number. 
  
## Validate

For validation, you should be able to use any Skype for Business client to sign in to the account you created.


## See also

[Configure accounts for Skype Room Systems v2](room-systems-v2-configure-accounts.md)

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Deploy Skype Room Systems v2](room-systems-v2.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

