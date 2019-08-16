---
title: "Skype Room System single forest on-premises deployments"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 80da9d71-3dcd-4ca4-8bd1-6d8196823206
description: "Read this topic to learn how to deploy Skype Room System in a single forest on-premises environment."
---

# Skype Room System single forest on-premises deployments
 
Read this topic to learn how to deploy Skype Room System in a single forest on-premises environment.
  
This section provides an overview of the steps for provisioning the Skype Room System account on Exchange Server and Skype for Business Server hosted in a single forest on-premises deployment.
  
## Single forest on-premises deployments

If you already have a resource mailbox account for the conferencing room, you can use it. Otherwise, you will need to create a new one. You can use either Exchange Management Shell (PowerShell) or Exchange Management Console to create a new resource mailbox account. We recommend using a new (delete old mailbox and re-create) resource mailbox for Skype Room System. Make sure to back up mailbox data before deleting and then export it back to the re-created mailbox using the Outlook client (see Export or back up messages, calendar, tasks, and contacts for more information). To restore the meetings lost by deleting the mailbox, see [Connect or restore a deleted mailbox](https://technet.microsoft.com/library/jj863438%28v=exchg.150%29.aspx). 
  
To use an existing resource mailbox account (for example, LRS-01) follow the steps below:
  
1. Run the following Exchange Management PowerShell command:
    
   ```
   Set-Mailbox -Name 'LRS-01' -Alias 'LRS01' -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

2. If you plan to create a new mailbox, then, for a single forest on-premises Exchange organization, run the following command:
    
   ```
   New-Mailbox -UserPrincipalName LRS01@contoso.com -Alias LRS01 -Name "LRS-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   The above example creates an enabled user account in Active Directory and a room mailbox for a conference room in an on-premises Exchange organization. The RoomMailboxPassword parameter specifies the password for the user account.
    
3. Configure the account to automatically resolve conflicts by accepting/rejecting meetings. Skype Room System-equipped conference room accounts in Exchange can be managed by individuals, but note that until the individual accepts a meeting it will not appear on the Skype Room System home screen calendar.
    
   ```
   Set-CalendarProcessing -Identity LRS01 -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteSubject $false -RemovePrivateProperty $false
   ```

   For a complete set of commands available, see Set-CalendarProcessing.
    
   To remind meeting organizers to make the meeting an online Skype for Business meeting in Outlook, run the following command to set up a MailTip for the new account: 
    
   ```
   Set-Mailbox -Identity LRS01@contoso.com -MailTip "This room is equipped with Lync Meeting Room (LRS), please make it a Lync Meeting to take advantage of the enhanced meeting experience from LRS"
   ```
4. Use the following commands to configure localized strings. If required by your organization, you can also add custom translations: 
   ```
   $Temp = Get-Mailbox  LRS01@ contoso.com 
   $Temp.MailTipTranslations += "ES: Spanish translation of the message"
   Set-Mailbox -Identity LRS01@contoso.com -MailTipTranslations $Temp.MailTipTranslations
   ```

5. Optional: Configure meeting acceptance text that provides users with information about Skype for Business Meeting Room, and what to expect when they schedule and join meetings. 
    
   ```
   Set-CalendarProcessing -Identity LRS01 -AddAdditionalResponse $TRUE -AdditionalResponse "This is the Additional Response Text"
   ```

## Check Resource Mailbox Account in Active Directory

The conference room mailbox account created by Exchange in step 1 above might be a disabled user object in Active Directory. Skype Room System cannot sign in or authenticate by using Kerberos/NTLM authentication if the account is disabled in Active Directory. The Skype Room System client must be able to authenticate against Exchange Web Services to retrieve calendar settings, and must also be able to send email with whiteboard contents. 
  
Therefore, if the account is disabled, you must enable this account in Active Directory by doing the following: 
  
1. In Active Directory, run the following command to enable account log on: 
    
   ```
   Set-ADAccountPassword -Identity LRS01
   ```

   Running this command will prompt you to enter the current password, and then to re-enter the password twice for confirmation.
    
2. Once the password is set, run the following command to enable the account: 
    
   ```
   Enable-ADAccount -Identity LRS01
   ```

## Enabling Skype Room System Accounts for Skype for Business

This section provides an overview of the steps required to enable Skype for Business for your conference room account, which will be configured on Skype Room System. 
  
After you create a resource mailbox account for the conferencing rooms, use Skype for Business Server Management Shell to enable Skype Room System accounts for Skype for Business services.
  
> [!NOTE]
> The following procedure assumes that you have enabled the Skype Room System account in Active Directory. 
  
1. Run the following command to enable the Skype Room System account on a Skype for Business Server pool:
    
   ```
   Enable-CsMeetingRoom -SipAddress "sip:LRS01@contoso.com" -domaincontroller DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com -Identity LRS01
   ```

2. Optional: Allow this account to make and receive PSTN phone calls by enabling the account for Enterprise Voice. Enterprise Voice is not required for Skype Room System, but if you do not enable it for Enterprise Voice, the Skype Room System client won't be able to provide PSTN dialing functionality:
    
   ```
   Set-CsMeetingRoom LRS01 -domaincontroller DC-ND-001.contoso.com -LineURItel: +14255550555;ext=50555"
   Set-CsMeetingRoom -domaincontroller DC-ND-001.contoso.com -Identity LRS01 -EnterpriseVoiceEnabled $true
   ```

> [!NOTE]
> If you enable Enterprise Voice for the Skype Room System conference room account, make sure to configure a restricted Voice Policy suitable for your organization. If the Skype for Business Meeting Room is a publicly available resource, anyone could use it to join a meeting, either scheduled or ad hoc. After joining a meeting, the person could dial out to any number. In Skype for Business Server, the dial-out from conferences feature uses the voice policy of the user, in this case the Skype Room System account used to join the meeting. In earlier versions of Lync Server, the voice policy of the organizer is used. Therefore, if a user of an earlier version of Lync Server schedules a meeting room and invites the Skype Room System room account, anyone could use the Skype for Business Meeting Room to join the meeting and could dial any national/regional or international phone number, as long as the organizer is allowed to dial those numbers. 
  

