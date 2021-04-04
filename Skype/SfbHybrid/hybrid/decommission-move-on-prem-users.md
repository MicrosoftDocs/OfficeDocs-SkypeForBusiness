---
title: Move users and endpoints to the cloud
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Moving user and endpoints before decommissioning a Skype for Business on-premises environment."

---

# Move required users and endpoints before decommissioning your on-premises environment

This article describes how to remove required users and application endpoints before decommissioning your on-premises Skype for Business environment. This is step 1 of the following steps to decommission your on-premises environment:

- **Step 1. Move all required users and application endpoints from on-premises to online.** (This article.)

- **Step 2.** [Disable your hybrid configuration](decommission-disable-hybrid.md).

- **Step 3.** [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).


## Move all required users from on-premises to the cloud

Any users that you will continue to use after completing the migration must be first moved from on-premises to the cloud. This is done using the on-premises administration tools. For details, see
Move users between on-premises and cloud

Even though it is possible for users with on-premises Skype for Business Server accounts to use Teams, these users do not have the full functionality of Teams. In particular, these users cannot interop or federate with any other user still using Skype for Business (whether online or on-premises) nor can these users receive PSTN calls in their Teams client. Hence these users must be moved online. This step also ensures any contacts or meetings created in Skype for Business Server are migrated to the Teams.

To check if there are any remaining users in your on-premises deployment, run the following cmdlets in a Skype for Business Server PowerShell window.

```PowerShell
Get-CsUser -Filter { HostingProvider -eq "SRV:"}
```

If any users are returned, review the output to determine if any accounts must be moved to the cloud and for any such users, follow the steps here . For user accounts that are no longer needed, run the following Skype for Business Server PowerShell cmdlet:

```PowerShell
Get-CsUser -Filter { HostingProvider -eq "SRV:"} | Disable-CsUser
```

> [!NOTE]
> This action will remove all Skype for Business attributes for all users meeting the filter criteria. But sure to confirm these accounts are not needed going forward before proceeding.

## Move on-premises hybrid application endpoints to Microsoft 365

1. Record on-premises Hybrid Application Endpoint settings, by executing the following on-premises Skype for Business Server PowerShell command to export endpoint data:

   ```PowerShell
   Get-CsHybridApplicationEndpoint|select Sipaddress, DisplayName, ApplicationID, LineUri |Export-Csv -Path "c:\backup\HybridEndpoints.csv"
   ```
2. Create and license new Resource Accounts in Microsoft 365 to replace existing on-premises hybrid application endpoints.

3. Associate the new Resource Accounts with the existing Hybrid Application Endpoints.

4. Remove phone numbers defined in on-premises Hybrid Application Endpoints by executing the following on-premises Skype for Business Server PowerShell command:

   ```PowerShell
   Get-CsHybridApplicationEndpoint -Filter {LineURI -ne $null} | Set-CsHybridApplicationEndpoint -LineURI ""
   ```
5. Because it's possible the phone numbers for these accounts were managed in Microsoft 365 instead of on-premises, run the following command in Skype for Business Online PowerShell:

   ```PowerShell
   $endpoints = import-csv "c:\backup\HybridEndpoints.csv"
   foreach ($endpoint in $endpoints)
   {
   if($endpoint.LineUri)
       {
           $upn = $endpoint.SipAddress.Replace("sip:","")
           $ra=Get-CsOnlineApplicationInstance | where UserPrincipalName -eq $upn 
           Set-CsOnlineApplicationInstance -Identity $ra.Objectid -OnpremPhoneNumber ""
       }
   }
   ```

6. Assign phone numbers to new Resource Accounts created in Step 2. For more details how to assign phone number to a resource account please refer to the following article: https://docs.microsoft.com/en-us/microsoftteams/manage-resource-accounts#assign-a-service-number.

7. Delete the on-premises endpoints by executing the following on-premises Skype for Business Server PowerShell command:

   ```PowerShell
   Get-CsHybridApplicationEndpoint | Remove-CsHybridApplicationEndpoint
   ```
You are now ready to disable your hybrid configuration.




