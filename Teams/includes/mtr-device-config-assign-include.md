
After you create the resource account, you need to assign a license to it. The resource account needs a Microsoft 365 or Office 365 license to sign into Microsoft Teams.

> [!NOTE]
> Microsoft Teams Rooms Basic and Microsoft Teams Rooms Pro are the two available SKUs for shared meeting room devices, including Teams Rooms. A meeting room license is required for Teams displays with hot-desking. For more information, see [Teams meeting room licensing](rooms-licensing.md).

To assign licenses using the Microsoft 365 admin center, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users). To assign licenses using Azure AD, see one of the following tabs:

#### [**Active Directory 2.0**](#tab/active-directory2-license/)


1. Connect to Azure AD
  
    ```PowerShell
    Connect-AzureAD
    ```

     For details about Active Directory, see [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview?view=azureadps-2.0).
    
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

    For details about Active Directory, see [Azure Active Directory (MSOnline).](/powershell/azure/active-directory/overview?view=azureadps-1.0)

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