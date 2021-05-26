---
title: Decommission Skype for Business Server
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
description: "Instructions for decommissioning Skype for Business Server."

---

# Remove your on-premises Skype for Business deployment

This article describes how to remove your on-premises Skype for Business deployment. This is step 4 of the following steps to decommission your on-premises environment:

- Step 1. [Move all required users from on-premises to online](decommission-move-on-prem-users.md). 

- Step 2. [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md).

- Step 3. [Move hybrid application endpoints from on-premises to online](decommission-move-on-prem-endpoints.md)

- **Step 4. Remove your on-premises Skype for Business deployment.** (This article)


> [!IMPORTANT] 
> The exact steps in this article apply only if you are using Method 2 for managing user attributes, as described [here](cloud-consolidation-disabling-hybrid.md#method-2---clear-skype-for-business-attributes-for-all-on-premises-users-in-active-directory). 
If you are using Method 1, do not complete the whole procedure described in this article to remove your Skype for Business servers. Instead, you can follow this procedure without running steps 5 and 6 from the _Remove your on-premises Skype for Business deployment_ section (without undoing Forest-level and Domain-level changes). 

To complete the steps in this article, you need privileges for both the Schema Admins group and the Enterprise Admin group. You will need these privileges to undo the Skype for Business Server schema and forest-level changes to Active Directory Domain Services. You will also need to be a member of the RTCUniversalServerAdmins group.


## Prepare to remove the Skype for Business deployment

After you move all required user accounts to the cloud, there may still be some remaining on-premises objects such as contacts and applications that you will need clean up.

Use the steps below to clean these objects, and make sure you are a member of both the Local Administrator group and the RTCUniversalServerAdmins group. Note that ExUmContacts and PersistantChatEndPoints are not available in Skype for Business Server 2019. If you have Skype for Business Server 2019, the corresponding cmdlets in the steps below should be omitted.

1. To check if there are any contacts or applications associated with the Skype for Business Server on-premises deployment, run the following Skype for Business Server PowerShell cmdlets.

   ```PowerShell
   Get-CsMeetingRoom
   Get-CsCommonAreaPhone
   Get-CsAnalogDevice
   Get-CsExUmContact
   Get-CsDialInConferencingAccessNumber
   Get-CsRgsWorkflow
   Get-CsTrustedApplicationEndpoint
   Get-CsTrustedApplication
   Get-CsPersistentChatEndpoint
   Get-CsAudioTestServiceApplication
   Get-CsCallParkOrbit
   ```
2. Review the output lists from the cmdlets in Step 1. Then if objects can be removed, run the following Skype for Business Server PowerShell cmdlets:

   ```PowerShell
   Get-CsMeetingRoom | Disable-CsMeetingRoom
   Get-CsCommonAreaPhone | Remove-CsCommonAreaPhone 
   Get-CsAnalogDevice | Remove-CsAnalogDevice
   Get-CsExUmContact | Remove-CsExUmContact
   Get-CsDialInConferencingAccessNumber | Remove-CsDialInConferencingAccessNumber
   Get-CsRgsWorkflow | Remove-CsRgsWorkflow
   Get-CsTrustedApplicationEndpoint | Remove-CsTrustedApplicationEndpoint
   Get-CsTrustedApplication | Remove-CsTrustedApplication -Force
   Get-CsPersistentChatEndpoint |  Remove-CsPersistentChatEndpoint
   Get-CsCallParkOrbit | Remove-CsCallParkOrbit -Force
   Get-CsVoiceRoute | Remove-CsVoiceRoute -Force
   ```
## Remove your on-premises Skype for Business deployment

After completing all the preliminary steps, you can remove the Skype for Business deployment by following these steps:

1. Logically remove the Skype for Business Server deployment, except for a single front end, as follows:

   a. Update your Skype for Business Server topology to have a single front-end pool:

     - In Topology Builder, download a new copy and navigate to the Frontend pool.
     - Right-click the pool, and then click **Edit Properties**.
     - In **Associations**, uncheck **Associate Edge Pool** (for media components) and click **OK**.
     - If there is more than one Frontend Pool, remove Associations for all remaining pools.
     - Select **Action > Remove Deployment**.
     - Select **Action > Publish Topology**.

    b. After publishing the topology, complete the additional steps described in the wizard.

2. Remove Skype for Business Server conference directories by running the following Skype for Business Server PowerShell cmdlet:

   ```PowerShell
   Get-CsConferenceDirectory | Remove-CsConferenceDirectory -Force
   ```

3. Finalize the uninstall of your Skype for Business Server deployment by running the following Skype for Business Server PowerShell cmdlet:

   ```PowerShell
   Publish-CsTopology -FinalizeUninstall
   ```
   > [!NOTE]
   > If this step returns an error, please open a Microsoft support ticket to get help removing the remaining stale objects.

4. Remove Central Management Store Service Control Point by running the following Skype for Business Server PowerShell cmdlet:

   ```PowerShell
   Remove-CsConfigurationStoreLocation
   ``` 

   > [!NOTE]
   > If you are using Method 1 for managing user attributes, as described [here](cloud-consolidation-disabling-hybrid#method-1---manage-sip-addresses-and-phone-numbers-for-users-in-active-directory), do not continue with the following steps.
   
5. Undo Skype for Business Server Active Directory Domain forest-level changes by running the following Skype for Business Server PowerShell cmdlet:

   ```PowerShell
   Disable-CsAdDomain
   ```
6. Undo Skype for Business Server Active Directory Domain schema changes by running the following Skype for Business Server PowerShell cmdlet:

   ```PowerShell
   Disable-CsAdForest
   ```

## See also

- [Decommission your on-premises Skype for Business environment](decommission-on-prem-overview.md)

- [Move all required users from on-premises to online](decommission-move-on-prem-users.md)

- [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md)

- [Move hybrid application endpoints from on-premises to online](decommission-move-on-prem-endpoints.md)









