---
ms.date: 11/16/2023
ms.custom:
  - has-azure-ad-ps-ref, azure-ad-ref-level-one-done
---

Like any Microsoft 365 account, a newly created resource account's password is set to expire automatically after a period of time. However, if the resource account password expires, the Teams Rooms device it's signed into won't be able to sign in again after the expiration date. 

To avoid resetting the resource account's password and logging into each Teams Rooms device again, you can turn off password expiration for the account.
  
> [!NOTE]
> Setting **Password never expires** is a requirement for shared Microsoft Teams devices. If your domain rules prohibit passwords that don't expire, you'll need to create an exception for each Teams device resource account.

Follow the steps in one of the following tabs to turn off password expiration:

#### [**Microsoft Graph PowerShell**](#tab/graph-powershell-password/)

First, connect to the Microsoft Graph PowerShell:

```PowerShell
   Connect-MgGraph -Scopes "User.ReadWrite.All"
```

This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

```PowerShell
Update-MgUser -UserId ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration -PassThru
```

#### [**Microsoft Entra ID 2.0/AzureAD**](#tab/azure-active-directory2-password/)

First, connect to Active Directory PowerShell:

```PowerShell
   Connect-AzureAD
```

Then, see [Set a password to never expire](/microsoft-365/admin/add-users/set-password-to-never-expire#set-a-password-to-never-expire).

This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

```PowerShell
Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
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

