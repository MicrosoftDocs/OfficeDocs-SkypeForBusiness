If the resource account password expires, the device won't sign in after the expiration date. The password will then need to be changed for the resource account and then updated on each device. To avoid this, you can turn off password expiration.
  
> [!NOTE]
> Setting **Password never expires** is a requirement for shared Microsoft Teams devices. If your domain rules prohibit passwords that don't expire, you'll need to create an exception for each Teams device resource account.

Follow the steps in one of the following tabs to turn off password expiration:

#### [**Azure Active Directory 2.0**](#tab/azure-active-directory2-password/)

First, Connect to Active Directory PowerShell:

```PowerShell
   Connect-AzureAD
```

Then, see [Set a password to never expire](/microsoft-365/admin/add-users/set-password-to-never-expire?view=o365-worldwide#set-a-password-to-never-expire).

This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

```PowerShell
Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
```

#### [**Azure Active Directory 1.0**](#tab/azure-active-directory1-password/)

 1. Connect to MSOnline PowerShell:

       ```PowerShell
       Connect-MsolService
       ```

       For details about Active Directory, see [Azure Active Directory (MSOnline)](/powershell/azure/active-directory/overview?view=azureadps-1.0).

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
    
    For details about Active Directory PowerShell, see [ActiveDirectory](/powershell/module/activedirectory/?view=windowsserver2022-ps).

2. Set the password to never expire by using the following syntax:

    ```PowerShell
    Set-ADUser -Identity <samAccountName> -PasswordNeverExpires $true
    ```

    This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Set-ADUser -Identity ConferenceRoom01@contoso.com -PasswordNeverExpires $true
    ```

---