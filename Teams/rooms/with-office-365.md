---
title: Create resource accounts for rooms and shared Teams devices
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Read this article for information on how to create resource accounts for rooms and shared devices, including Microsoft Teams Rooms, Teams Rooms on Surface Hub, and hot-desking on Teams displays.
---

# Create and configure resource accounts for rooms and shared Teams devices

This article provides steps to create resource accounts for shared spaces and devices, and it includes steps to configure resource accounts for Microsoft Teams Rooms on Windows, Teams Rooms on Android, Teams Rooms on Surface Hub, and hot-desking on Teams displays.

Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room or projector. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room that will automatically accept or decline meeting invites depending on its calendar availability. 

Every resource account is unique to a single Microsoft Teams Rooms installation or Teams display hot-desking implementation.

> [!NOTE]
> If using Microsoft Teams panels, the Teams Rooms resource account signs in to both Teams Rooms and associated Teams panels.

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

> [!NOTE]
> **Skype for Business** <br><br>
> If you need to enable your resource account to work with Skype for Business, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)

## Before you begin

### Requirements

Depending on your environment, you need one or more roles to create resource accounts.

|**Environment**|**Required Roles**|
|-----|-----|
|Azure Active Directory  <br/> |Global Administrator or User Administrator  <br/> |
|Active Directory  <br/> |Active Directory Enterprise Admins, Domain Admins, or have delegated rights to create users. Azure Active Directory Connect Sync rights.  <br/> |
|Exchange Online  <br/> |Global Administrator or Exchange Administrator   <br/> |
|Exchange Server  <br/> |Exchange Organization Management or Recipient Management   <br/> |

If you're creating resource accounts for Teams Rooms, the UPN must match the SMTP address of the resource account. See [Microsoft Teams Rooms requirements](requirements.md) before you deploy Teams Rooms.

### What license do you need?

Before you create a Microsoft 365 resource account, check to see what kind of license it needs:

- **Teams meetings** If you want to associate the resource account with a shared device, such as a Microsoft Teams Room or Teams display with hot-desking, and use it to join a Teams meeting so attendees can use it to present video and audio through it, you need a Meeting Room License. For more information about licensing for meeting rooms, see [Teams Meeting Room Licensing](rooms-licensing.md).

- **PSTN calls** If you want the resource to make or receive calls to or from an external phone number (called a Public Switched Telephone Network or PSTN call), you need a Microsoft 365 Phone System or Microsoft 365 Business Voice license. You only need to complete Step 1 in the following overview. Then, see [Microsoft Teams add-on licenses](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md) for more information.

- If you're only using a resource account to book a resource&mdash;that is, invite the resource to your meeting and have it automatically accept or decline the invitation&mdash;you don't need to assign a license to the resource account and you only need to complete Step 1 in the following overview.  

## Overview

**Step 1 -** [Create a new resource account](#create-a-resource-account). Or, if a room mailbox already exists and you want to convert it to a resource account, you can [modify an existing Exchange room mailbox](?tabs=existing-account#create-a-resource-account).

**Step 2 -**  Then, [configure your account](#configure-mailbox-properties) for Teams Meetings.

**Step 3 -**  If the resource account is going to be associated with a shared device, such as Teams displays with hot-desking, [turn off password expiration](#turn-off-password-expiration).

**Step 4 -**  Lastly, [assign a meeting room license](#assign-a-meeting-room-license) so the account can access Microsoft Teams.

After you create and configure your resource accounts, see [Next steps](#next-steps) to review additional setup tasks, including distribution groups, network capability, and calling.

## Create a resource account

> [!TIP]
> When naming your resource accounts, we recommend using a standard naming convention to the beginning of the e-mail address. This will help with creating dynamic groups to ease management in Azure Active Directory. For example, you could use "mtr-" for all resource accounts that will be associated with Microsoft Teams Rooms.

> [!TIP]
> We recommend that you create all resource accounts using Exchange Online and Azure Active Directory.

Create a resource account using a method from one of the following tabs:

#### [**In Microsoft 365 admin center**](#tab/m365-admin-center)

1. Sign in to the Microsoft 365 admin center.

2. Provide the admin credentials for your Microsoft 365 tenant.

3. Go to **Resources** in the left panel, and then select **Rooms & equipment**. If these options aren't available in the left panel, you may need to select **Show all** first.

4. Select **Add resource** to create a new room account. Enter a display name and email address for the account, select **Add**, and then select **Close**.

5. By default, resource accounts are configured with the following settings:

    - Allow repeat meetings
    - Automatically decline meetings outside of the following limits
      - Booking window (days): 180
      - Maximum duration (hours): 24
    - Auto accept meeting requests

    If you want to change them, select **Edit booking options** before you select **Close**. If you want to change them later, go to **Resources** > **Rooms & equipment**, select the resource account. Then  under **Booking options**, select **Edit**.

6. Go to **Users** > **Active users**, and select the room you created to open the properties panel.

7. Next, assign a password to the resource account. In the panel, select **Reset password**.
 
8. Requiring users to change the password on a shared device will cause sign in problems. Uncheck **Require this user to change their password when they first sign in**, and select **Reset password**.

9. In the **Licenses and Apps** section, set **Select location** to the country or region where the device will be installed. Then select the license you want to assign, such as Meeting Room, and select **Save changes**. The license may vary depending on your organization.

To change the settings of the resource mailbox, see [Configure mailbox properties](#configure-mailbox-properties) or use the Exchange admin center.

You may also need to apply bandwidth policies or meeting policies to this account. See [Next steps](#next-steps) for more information.

#### [**With Exchange Online**](#tab/exchange-online)

1. Connect to [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

    ``` PowerShell
    Connect-ExchangeOnline
    ```

2. By default, room mailboxes don't have associated accounts. Add an account when you create a room mailbox so it can authenticate with Microsoft Teams.

    If you're creating a new resource mailbox:
    
    ``` PowerShell
    New-Mailbox -MicrosoftOnlineServicesID <Office365 ID> -Name <String> -Alias <string> -Room -EnableRoomMailboxAccount $true  -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
    ```
    
    This example creates a new room mailbox with the following settings:

    - Account: ConferenceRoom01@contoso.com
          
    - Name: ConferenceRoom01
        
     - Alias: ConferenceRoom01
        
     - Account password: P@$$W0rd5959

    ``` PowerShell
    New-Mailbox -MicrosoftOnlineServicesID ConferenceRoom01@contoso.com -Name "ConferenceRoom01" -Alias ConferenceRoom01 -Room -EnableRoomMailboxAccount $true  -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
    ```

If you're not in an Exchange hybrid configuration, then you can continue to the next step, [Configure mailbox properties](#configure-mailbox-properties).

If you're in an Exchange hybrid configuration, you need to add an email address for your on-premises domain account. See [Sync on-premises and Office 365 user accounts directories](https://support.microsoft.com/topic/how-to-use-smtp-matching-to-match-on-premises-user-accounts-to-office-365-user-accounts-for-directory-synchronization-75673b94-e1b8-8a9e-c413-ee5a2a1a6a78) for more information.

#### [**With Exchange Server**](#tab/exchange-server)

  1. Connect to Exchange Management Shell. [Open the Exchange Management Shell](/powershell/exchange/exchange-server/open-the-exchange-management-shell) or [connect to your Exchange server using remote PowerShell](/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell).

   2. To create a new room mailbox:

      ``` PowerShell
      New-Mailbox -UserPrincipalName <UPN> -Name <String> -Alias <String> -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
      ```
     
   This example creates a new room mailbox with the following settings:

   - Account: ConferenceRoom01@contoso.com
  
   - Name: ConferenceRoom01

   - Alias: ConferenceRoom01

   - Account password: P@$$W0rd5959

   ``` PowerShell
   New-Mailbox -UserPrincipalName ConferenceRoom01@contoso.com -Name "ConferenceRoom01" -Alias ConferenceRoom01 -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
   ```

#### [**Modify an existing Exchange room mailbox**](#tab/existing-account)

To modify an existing room mailbox to become a resource account, use the following syntax:

``` PowerShell
Set-Mailbox -Identity <RoomMailboxIdentity> -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
```

This example enables the account for the existing room mailbox that has the alias value ConferenceRoom02, and sets the password to 9898P@$$W0rd.

``` PowerShell
Set-Mailbox -Identity ConferenceRoom02 -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '9898P@$$W0rd' -AsPlainText -Force)
```

If you're in an Exchange hybrid configuration, you'll also need to add an email address for your on-premises domain account. See [Sync on-premises and Office 365 user accounts directories](https://support.microsoft.com/topic/how-to-use-smtp-matching-to-match-on-premises-user-accounts-to-office-365-user-accounts-for-directory-synchronization-75673b94-e1b8-8a9e-c413-ee5a2a1a6a78) for more information.

For detailed syntax and parameter information, see [New-Mailbox](/powershell/module/exchange/mailboxes/new-mailbox) and [Set-Mailbox](/powershell/module/exchange/mailboxes/set-mailbox).

> [!NOTE]
> If you're creating this account for Teams Room on Surface Hub, you should also enable ActiveSync on this account. This will allow you to send e-mail directly from the Surface Hub, which you can use for features like Whiteboard. See [Applying ActiveSync policies to device accounts (Surface Hub)](/surface-hub/apply-activesync-policies-for-surface-hub-device-accounts) to learn more.

---

> [!IMPORTANT]
> If you're only using this resource account to book space and automatically accept or decline invitations, you've completed the set up. If you're using this resource account for PSTN calling, see [Microsoft Teams add-on licenses](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md) to determine what license it needs.
>
> Continue to the next section only if the resource account is for a Teams Rooms on Windows, Teams Rooms on Android, Teams Rooms on Surface Hub, or a Teams display with hot-desking.

## Configure mailbox properties

In Exchange PowerShell, either online or on-premises, configure the following settings on the room mailbox to improve the meeting experience:

- **AutomateProcessing: `AutoAccept`** Meeting organizers receive the room reservation decision directly without human intervention.

- **AddOrganizerToSubject: `$false`** The meeting organizer isn't added to the subject of the meeting request.

- **DeleteComments: `$false`** Keep any text in the message body of incoming meeting requests. This is required to process external Teams and third-party meetings to provide One Touch Join experience.

- **DeleteSubject: `$false`** Keep the subject of incoming meeting requests.

- **ProcessExternalMeetingMessages: `$true`** Specifies whether to process meeting requests that originate outside the Exchange organization. Required for external Teams meetings and [third-party meetings](/microsoftteams/rooms/third-party-join).

- **RemovePrivateProperty: `$false`** Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.

- **AddAdditionalResponse: `$true`** The text specified by the AdditionalResponse parameter is added to meeting requests.

- **AdditionalResponse: "This is a Microsoft Teams Meeting room!"** The additional text to add to the meeting acceptance response.

This example configures these settings on a room mailbox named ConferenceRoom01:

``` PowerShell
Set-CalendarProcessing -Identity "ConferenceRoom01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
```

For detailed syntax and parameter information, see [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing).

## Turn off password expiration

If the resource account password expires, the device won't sign in after the expiration date. The password will then need to be changed for the resource account and then updated on each device. To avoid this, you can turn off password expiration.
  
> [!NOTE]
> Setting **Password never expires** is a requirement for shared Microsoft Teams devices. If your domain rules prohibit passwords that don't expire, you'll need to create an exception for each Teams device resource account.

Follow the steps in one of the following tabs to turn off password expiration:

#### [**Azure Active Directory 2.0**](#tab/azure-active-directory2-password/)

First, Connect to Active Directory PowerShell:

```PowerShell
   Connect-AzureAD
```

Then, see [Set a password to never expire](/microsoft-365/admin/add-users/set-password-to-never-expire#set-a-password-to-never-expire).

This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

```PowerShell
Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
```

#### [**Azure Active Directory 1.0**](#tab/azure-active-directory1-password/)

 1. Connect to MSOnline PowerShell:

       ```PowerShell
       Connect-MsolService
       ```

       For details about Active Directory, see [Azure Active Directory (MSOnline)](/powershell/azure/active-directory/overview?view=azureadps-1.0&preserve-view=true).

2. Set the password to never expire by using the following syntax:

    ```PowerShell
    Set-MsolUser -Identity <samAccountName> -PasswordNeverExpires $true
    ```

    This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -PasswordNeverExpires $true
    ```

#### [**Active Directory (On premises)**](#tab/active-directory1-password/)

1. Connect to Active Directory PowerShell:

    ```PowerShell
       Import-Module ActiveDirectory
    ```
    
    For details about Active Directory PowerShell, see [ActiveDirectory](/powershell/module/activedirectory/).

2. Set the password to never expire by using the following syntax:

    ```PowerShell
    Set-ADUser -Identity <samAccountName> -PasswordNeverExpires $true
    ```

    This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Set-ADUser -Identity ConferenceRoom01@contoso.com -PasswordNeverExpires $true
    ```

---

## Assign a meeting room license

The resource account needs a Microsoft 365 or Office 365 license to sign into Microsoft Teams.

> [!NOTE]
> Microsoft Teams Rooms Basic and Microsoft Teams Rooms Pro are the two available SKUs for shared meeting room devices, including Teams Rooms. A meeting room license is required for Teams displays with hot-desking. For more information, see [Microsoft Teams Rooms licenses](rooms-licensing.md).

To assign licenses using the Microsoft 365 admin center, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users). To assign licenses using Azure AD, see one of the following tabs:

#### [**Active Directory 2.0**](#tab/active-directory2-license/)


1. Connect to Azure AD
  
    ```PowerShell
    Connect-AzureAD
    ```

     For details about Active Directory, see [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview?view=azureadps-2.0&preserve-view=true).
    
2. Assign a usage location to your resource account using the `Set-AzureADUser` cmdlet. This determines what license SKUs are available.

    In this example, the user is located in the United States (US):

    ```PowerShell
    Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -UsageLocation 'US'
    ```

3. Then, use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.

    ```PowerShell
    Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
    ```

4. To assign the license, use the `Set-AzureADUser` cmdlet, and convert the license SKU ID (see step 2) into a PowerShell license type object. Then, assign that object to the resource account. In the following example, the license SKU ID is 6070a4c8-34c6-4937-8dfb-39bbc6397a60, and it's assigned to the account conferenceroom01@contoso.com:

    ```PowerShell
    #Create an object for a single license type
    $License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
    $License.SkuId = "6070a4c8-34c6-4937-8dfb-39bbc6397a60" 
       
    #Create an object for a multiple license type
    $Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
       
    #Add the single license object to the multiple license object
    $Licenses.AddLicenses = $License 
       
    #Assign the license to the resource account
    Set-AzureADUserLicense -ObjectId ConferenceRoom01@contoso.com -AssignedLicenses $Licenses
    ```

#### [**Active Directory 1.0**](#tab/active-directory1-license/)

1. Connect to MSOnline PowerShell.

   ```PowerShell
   Connect-MsolService
   ```

    For details about Active Directory, see [Azure Active Directory (MSOnline).](/powershell/azure/active-directory/overview?view=azureadps-1.0&preserve-view=true)

2.  Assign a usage location to your resource account using the `Set-MsolUser` cmdlet. This determines what license SKUs are available.

    In this example, the user is located in the United States (US).
    
    ```PowerShell
    Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -UsageLocation 'US'
    ```
    
    You can then use `Get-MsolAccountSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.

4. To assign the license, use the `Set-MsolUser` cmdlet. In this example, the "contoso:MEETING_ROOM" license is assigned to the account conferenceroom01@contoso.com:

    ```PowerShell
    Set-MsolUserLicense -UserPrincipalName 'ConferenceRoom01@contoso.com' -AddLicenses 'contoso:MEETING_ROOM'
    ```

---

To validate the account creation and license assignment, sign in to any Teams Client using the account you created.

## Next steps

### Meeting policies

You may need to apply custom network, bandwidth, or meeting policies to this account. For more information on network and bandwidth policies, see [Meeting policy settings for audio & video](/microsoftteams/meeting-policies-audio-and-video). For Teams Rooms, we recommend you set the meeting policy bandwidth to 10 Mbps.

For collaboration purposes, turn on PowerPoint Live, Whiteboard, and shared notes. It is recommended that you enable the meeting policy setting "Meet now in private meetings". You may want to create a meeting policy to adjust participants and guest settings for Teams Rooms. For example, review the lobby settings such as which attendees to automatically admit to meetings. For more information on Teams meeting policies, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

### Calling

There are no unique requirements to enable calling with resource accounts. You enable the resource account for calling in the same way you enable a regular user.

> [!NOTE]
> We recommend turning off voice mail for shared devices by assigning a calling policy to the device resource accounts. See [Calling and call-forwarding in Teams](../teams-calling-policy.md) for more information.

### Configure distribution groups for Teams Calendar

To organize your meeting room locations, you can add your device resource accounts to Exchange distribution groups. For example, if you have offices in three different geographic locations, you can create three distribution groups and add the appropriate resource accounts to each location. For more information, see [Create a rooms list](/exchange/recipients/room-mailboxes?view=exchserver-2019&preserve-view=true#create-a-room-list).

### Configure places for Outlook Calendar
In order for meeting room locations to appear in the Outlook Room Finder, you need to use the Set-Place Exchange PowerShell cmdlet. Not only does Set-Place populate the Room Finder in Outlook, it also allows you to add additional metadata such as the capacity of the room or the floor of building the room is in. For more information, see [Set-Place](/powershell/module/exchange/set-place).

## Related articles

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Microsoft Teams Rooms Licensing](rooms-licensing.md)
