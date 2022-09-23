
Each Microsoft Teams Rooms device needs its own resource account. The resource account is the account the Teams Rooms device logs into and is what users in your organization invite to book the Teams Room.

When you create the resource mailbox, you can specify whether you want to allow recurring meetings, have the room auto accept invites, how many days into the future to accept invites, and so on.

> [!TIP]
> When naming your resource accounts, we recommend using a standard naming convention to the beginning of the e-mail address. This will help with creating dynamic groups to ease management in Azure Active Directory. For example, you could use "mtr-" for all resource accounts that will be associated with Microsoft Teams Rooms.

> [!TIP]
> We recommend that you create all resource accounts using Exchange Online and Azure Active Directory.

Create a resource account using a method from one of the following tabs:

#### [**In Microsoft 365 admin center**](#tab/m365-admin-center)

1. Sign in to the Microsoft 365 admin center.

2. Provide the admin credentials for your Microsoft 365 tenant.

3. Go to **Resources** in the left panel, and then select **Rooms & equipment**. If these options aren't available in the left panel, you may need to select **Show all** first.

4. Select **Add resource** to create a new resource account. Enter a display name and email address for the account and then select **Save**.

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

You may also need to apply bandwidth policies or meeting policies to this account. You can set mailbox policies in a later step.

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
