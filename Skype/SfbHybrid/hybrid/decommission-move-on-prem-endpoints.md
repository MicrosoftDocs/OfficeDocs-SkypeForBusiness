---
title: Migrate hybrid application endpoints to the cloud
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Migrate hyrid application endpoints before decommissioning a Skype for Business on-premises environment."

---

# Migrate hybrid application endpoints before decommissioning your on-premises environment

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

This article describes how to move required hybrid application endpoints to the Microsoft cloud before decommissioning your on-premises Skype for Business environment. This is step 3 of the following steps to decommission your on-premises environment:

- Step 1. [Move all required users from on-premises to online](decommission-move-on-prem-users.md)

- Step 2. [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md).

- **Step 3. Migrate hybrid application endpoints from on-premises to online.** (This article)

- Step 4. [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).


## Migrate all required hybrid application endpoints from on-premises to online

Before you can move these endpoints to online, you must ensure you have updated DNS records to point to Microsoft 365 for all sip domains used by the endpoints. Be aware that once you update DNS to point to Microsoft 365, any existing hybrid application endpoints will no longer be discoverable until you complete this step. Since this step (creating online Resource Accounts) is not possible if DNS records point to on-premises you should plan to do both steps 2 and 3 in the same maintenance window. For more information, see [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md).

1. Retrieve and export on-premises hybrid application endpoint settings by executing the following on-premises Skype for Business Server PowerShell command:

   ```PowerShell
   Get-CsHybridApplicationEndpoint|select Sipaddress, DisplayName, ApplicationID, LineUri |Export-Csv -Path "c:\backup\HybridEndpoints.csv"
   ```
2. Create and license new [Resource Accounts](/microsoftteams/manage-resource-accounts) in Microsoft 365 to replace the existing on-premises hybrid application endpoints.

3. Associate the new Resource Accounts with the existing hybrid application endpoints.

4. Remove phone numbers defined in the on-premises hybrid application endpoints by executing the following on-premises Skype for Business Server PowerShell command:

   ```PowerShell
   Get-CsHybridApplicationEndpoint -Filter {LineURI -ne $null} | Set-CsHybridApplicationEndpoint -LineURI ""
   ```
5. Because it's possible that phone numbers for these accounts were managed in Microsoft 365 instead of on-premises, run the following command in Teams PowerShell:

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

6. Assign phone numbers to the new Resource Accounts created in Step 2. For more information about how to assign a phone number to a resource account, see the following article: [Assign a service number](/microsoftteams/manage-resource-accounts).

7. Delete the on-premises endpoints by executing the following on-premises Skype for Business Server PowerShell command:

   ```PowerShell
   Get-CsHybridApplicationEndpoint | Remove-CsHybridApplicationEndpoint
   ```
You are now ready to [remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).

## See also

- [Decommission your on-premises Skype for Business environment](decommission-on-prem-overview.md)

- [Move all required users from on-premises to online](decommission-move-on-prem-users.md)

- [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md)

- [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md)

- [Create an auto attendant via cmdlets](/microsoftteams/create-a-phone-system-auto-attendant-via-cmdlets)




