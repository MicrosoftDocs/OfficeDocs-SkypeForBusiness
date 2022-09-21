
Like any Microsoft 365 account, a newly-created resource account's password is set to expire automatically after a period of time. However, if the resource account password expires, the Teams Rooms device it's signed into won't be able to sign in again the expiration date. 

To avoid having to reset the resource account's password and then logging into each Teams Rooms device again, you can turn off password expiration for the account.
  
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
    
    For details about Active Directory PowerShell, see [ActiveDirectory](/powershell/module/activedirectory).

2. Set the password to never expire by using the following syntax:

    ```PowerShell
    Set-ADUser -Identity <samAccountName> -PasswordNeverExpires $true
    ```

    This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Set-ADUser -Identity ConferenceRoom01@contoso.com -PasswordNeverExpires $true
    ```

---