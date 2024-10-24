---
ms.date: 10/10/2024
ms.custom:
  - has-azure-ad-ps-ref, azure-ad-ref-level-one-done
---

Based on organization policies, resource account passwords may be set to expire automatically after a period of time. If the resource account password expires, the Teams Rooms device with sign out and can't sign in again without manual intervention.
  
> [!NOTE]
> Setting **Password never expires** is a requirement for shared Microsoft Teams devices. If your organization prohibits passwords that don't expire, you'll need to create an exception for Teams device resource accounts.

To turn off password expiration, follow the steps in one of the following tabs:

#### [**Microsoft Graph PowerShell**](#tab/graph-powershell-password/)

1. Connect to [Microsoft Graph PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell):

    ```PowerShell
       Connect-MgGraph -Scopes "User.ReadWrite.All"
    ```

2. Set the password to never expire, this example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Update-MgUser -UserId ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
    ```

#### [**Active Directory (On-premises)**](#tab/active-directory1-password/)

1. Connect to [Active Directory PowerShell](/powershell/module/activedirectory):

    ```PowerShell
       Import-Module ActiveDirectory
    ```
    

2. Set the password to never expire, this example sets the password for the account ConferenceRoom01@contoso.com to never expire.

    ```PowerShell
    Set-ADUser -Identity ConferenceRoom01@contoso.com -PasswordNeverExpires $true
    ```


---

