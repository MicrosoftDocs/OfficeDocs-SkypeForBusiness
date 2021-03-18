---
title: "Disable hybrid to complete migration to the cloud"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.prod: skype-for-business-itpro
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This article includes detailed steps for disabling hybrid as part of cloud consolidation for Teams and Skype for Business."
---

# Disable hybrid to complete migration to the cloud: Overview

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. Aside from removing any hardware, a critical step is to logically separate that on-premises deployment from Microsoft 365 or Office 365 by disabling hybrid. Disabling hybrid consists of three steps:

1. Update DNS records to point to Microsoft 365 or Office 365.

2. Disable shared sip address space (also known as "split domain") in the Microsoft 365 or Office 365 organization.

3. Disable the ability in on-premises to communicate with Microsoft 365 or Office 365.

These steps logically separate your on-premise deployment of Skype for Business Server from Office 365 and should be done together as a unit. Details for each step are provided in this article below. Once that is complete, you can decommission your on-premises Skype for Business Deployment using one of two methods referenced below.

> [!Important] 
>Once this logical separation is complete, msRTCSIP attributes from your on-premises Active Directory still have values and will continue to sync via Azure AD Connect into Azure AD. How you decommission the on-premises environment depends on whether you intend to leave these attributes in place, or first clear them from your on-premises Active Directory. Be aware that clearing the on-premises msRTCSIP attributes after you have migrated from on-premises could result in loss of service for users! Details and tradeoffs of the two decommissioning approaches are described later below.

## Disable hybrid to complete migration to the cloud: Detailed Steps

1. *Update DNS to point to Microsoft 365 or  Office 365.* The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Microsoft 365 or Office 365 instead of the on-premises deployment. Specifically:

    |Record type|Name|TTL|Value|
    |---|---|---|---|
    |SRV|_sipfederationtls._tcp|3600|100 1 5061 sipfed.online.lync.<span>com|
    |SRV|_sip._tls|3600|100 1 443 sipdir.online.lync.<span>com|
    |CNAME|	lyncdiscover|	3600|	webdir.online.lync.<span>com|
    |CNAME|	sip|	3600|	sipdir.online.lync.<span>com|

    In addition, CNAME records for meet or dialin (if present) can be deleted. Finally, any DNS records for Skype for Business in your internal network should be removed.

    > [!Note] 
    > In rare cases, changing DNS from pointing on premises to Microsoft 365 or Office 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:
    >
    > - Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud.
    > 
    > - Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on-premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.
    >
    > If you suspect that any of your federated partners may be using Direct Federation or have not federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.


2.  *Disable shared sip address space in Microsoft 365 or Office 365 organization.* The command below needs to be done from a Skype for Business Online PowerShell window.

     ```PowerShell
     Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false
     ```
 
3.  *Disable the ability in on-premises to communicate with Microsoft 365 or Office 365.* The command below needs to be done from an on-premises PowerShell window:

     ```PowerShell
     Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false
     ```

## Managing attributes after moving users from on-premises to the cloud

By default, all users that were previously enabled for Skype for Business Server and subsequently moved to the cloud still have msRTCSIP attributes configured in your on-premises Active Directory. These attributes, in particular sip address (msRTCSIP-PrimaryUserAddress) and potentially phone number (msRTCSIP-Line), continue to sync into Azure AD. If changes are required to any of the msRTCSIP attributes, these changes must be made in the on-premises Active Directory and then sync'd to Azure AD. However, once the Skype for Business Server deployment has been removed, the Skype for Business Server tools will not be available to manage these attributes.

There are two options available for handling this situation:

1. Leave users that were enabled for Skype for Business server accounts as is, and manage the  msRTCSIP attributes using Active Directory tools. This ensures no loss of service for migrated users, and allows you to easily remove the Skype for Business Server deployment by eliminating (e.g. wiping) the servers, without a full decommissioning. However, newly licensed users will not have these attributes populated in your on-premises Active Directory and will need to be managed online.

2.  Clear all msRTCSIP attributes from migrated users in your on-premises Active Directory and manage these attributes using online tools. This method allows for a consistent management approach for existing and new users, however it may potentially result in a temporary loss of service during the on-premises decommissioning process.


### Method 1 - Manage sip addresses and phone numbers for users in Active Directory

Administrators can manage users who were previously moved from an on-premises Skype for Business Server to the cloud, even after the on-premises deployment is decommissioned. If you want to make changes to a user’s sip address or to a user’s phone number (and the sip address or phone number already has a value in the on-premises Active Directory), you must do this in the on-premises Active Directory and let the value(s) flow up to Azure AD. This does NOT require on-premises Skype for Business Server. Rather, you can modify these attributes directly in the on-premises Active Directory, using either the Active Directory Users and Computers MMC snap-in (as shown below), or by using PowerShell. If you are using the MMC snap-in, open the properties page of the user, click Attribute Editor tab, and find the appropriate attributes to modify:

- To modify a user’s sip address, modify the `msRTCSIP-PrimaryUserAddress`. Note, if the `ProxyAddresses` attribute contains a sip address, also update that value as a best practice. Although the sip address in `ProxyAddresses` is ignored by O365 if `msRTCSIP-PrimaryUserAddress` is populated, it may be used by other on-premises components.

- To modify a user’s phone number, modify `msRTCSIP-Line` *if it already has a value*.

  ![Active Directory users and computers tool](../media/disable-hybrid-1.png)
  
-  If the user did not originally have a value for `msRTCSIP-Line` on-premises before the move, you can modify the phone number using the -`onpremLineUri` parameter in the [Set-CsUser cmdlet](https://docs.microsoft.com/powershell/module/skype/set-csuser?view=skype-ps) in the Skype for Business Online PowerShell module.

These steps are not necessary for new users created after you disable hybrid, and those users can be managed directly in the cloud. If you are comfortable using the mix of these method as well as with leaving the msRTCSIP attributes in place in your on-premises Active Directory, you can simply re-image the on-premises Skype for Business servers. However, if you prefer to clear all msRTCSIP attributes and do a traditional uninstall of Skype for Business Server, then use Method 2.


### Method 2 - Clear Skype for Business Attributes for all on-premises users in Active Directory

This option requires additional effort and proper planning because users that were previously moved from an on-premises Skype for Business Server to the cloud are required to be re-provisioned. These users can be categorized into two different categories: users without Phone System and users with Phone System. Users with Phone System will experience a temporary loss of phone service as part of transitioning the phone number from being managed in on-premises Active Directory to the cloud. **It's recommended to perform a pilot involving a small number of users with Phone System prior to start bulk user operations.** For large deployments users can be processed in smaller groups in different time windows. 

Note: the process is simplest for users who have a matching sip address and UserPrincipalName. For organizations that have users with non-matching values across these two attributes, extra care must be taken as noted below for a smooth transition. 


1. Confirm the following on-premises Skype for Business PowerShell cmdlet returns an empty result. An empty result means no users are homed on-premises and have either been moved to Office 365 or have been disabled:

   ```PowerShell
   Get-CsUser -Filter { HostingProvider -eq "SRV:"} | Select-Object Identity, SipAddress, UserPrincipalName, RegistrarPool
   ```

2. Record users' current phones number (LineUri), UserPrincipalName and related info, by executing the following on-premises Skype for Business Server PowerShell cmdlet to export user data:

   ```PowerShell
   Get-CsUser | Select-Object SipAddress, UserPrincipalName, SamAccountName, RegistrarPool, HostingProvider, EnabledForFederation, EnabledForInternetAccess, LineUri, EnterpriseVoiceEnabled, HostedVoiceMail | Sort SipAddress | Export-Csv -Path  "c:\backup\SfbUserSettings.csv"
   ```

   > [!Important] 
   > Before proceeding open SfbUserSettings.csv file and confirm all user data has been successfully exported. It's recommended to keep a copy of this file.  Do not use this file in the following steps for processing users. 

3. Create a file with a group of users to be used in the following steps. After the first group of users has completed successfully, proceed with the next group of users. In the example below, the groups of users are selected alphabetically, but you may filter on users based on criteria that matches how you would like to process the users.

   ```PowerShell
   Get-CsUser | where userprincipalname -like "abc*" | Select-Object SipAddress, UserPrincipalName, SamAccountName, RegistrarPool, HostingProvider, EnabledForFederation, EnabledForInternetAccess, LineUri, EnterpriseVoiceEnabled, HostedVoiceMail | Sort SipAddress | Export-Csv -Path "c:\data\SfbUsers.csv"
   ```

   > [!Important] 
   > Before proceeding open SfbUsers.csv file and confirm user data has been successfully exported. You will need the LineUri (phone number), UserPrincipalName, SamAccountName, and SipAddress from this file in a later step.

4. Delete the attribute information related to Skype for Business Server from active Directory for the set of users you are ready to update.  There are 2 steps to this process, as shown below.

   > [!Important] 
   > After the next AAD Sync cycle after running this step, users with Phone System who were previously moved from an on-premises Skype for Business Server to the cloud will lose the ability to make and receive calls until step 8 is successfully completed and confirmed in step 9. In addition, make sure you have saved user's phone numbers and related information as per step 2, since that information is required for that step.

 
   ```PowerShell
   $sfbusers=import-csv "c:\data\SfbUsers.csv"
   foreach($user in $sfbusers){
   Disable-CsUser -Identity $user.SipAddress}
   ```

   Next, for the same set of users, clear the value of msRTCSIP-DeploymentLocator using on-premises Active Directory PowerShell:

   ```PowerShell
   $sfbusers=import-csv "c:\data\SfbUsers.csv"
   foreach($user in $sfbusers){
   Set-ADUser -Identity $user.SamAccountName -Clear msRTCSIP-DeploymentLocator}
   ```

5. Run the following on-premise Skype for Business PowerShell cmdlet to add sip address value back to the on-premises Active Directory proxyAddresses. This will prevent interoperability issues that rely on this attribute. 

   ```PowerShell
      $sfbusers=import-csv "c:\data\SfbUsers.csv"
      foreach($user in $sfbusers){
        $userUpn=$user.UserPrincipalName
        $userSip=$user.SipAddress
        $proxies=Get-ADUser -Filter "UserPrincipalName -eq '$userUpn'" -properties * | Select-Object @{Name="proxyAddresses";Expression={$_.proxyAddresses}}
        if(($null -eq $proxies) -or ($proxies.proxyAddresses -NotContains $userSip))
        {
                Get-ADUser -Filter "UserPrincipalName -eq '$userUpn'" | Set-ADUser -Add @{"proxyAddresses"=$user.SipAddress}
        }
      }
   ```

6. Run Azure AD Sync

   ```PowerShell
   Start-ADSyncSyncCycle -PolicyType Delta
   ```

7. Wait for user provisioning to complete. You can monitor user provisioning progress by running the following Skype for Business Online PowerShell command. The following Skype for Business Online PowerShell command returns an empty result as soon process is completed.

   ```PowerShell
   Get-CsOnlineUser -Filter {Enabled -eq $True -and (MCOValidationError -ne $null -or ProvisioningStamp -ne $null -or SubProvisioningStamp -ne $null)} | fl SipAddress, InterpretedUserType, OnPremHostingProvider, MCOValidationError, *ProvisioningStamp
   ```

8. Execute the following Skype for Business Online PowerShell command to assign phone numbers and enable users for Phone System:
     
   ```PowerShell
   $sfbusers=import-csv "c:\data\SfbUsers.csv"
   foreach($user in $sfbusers){
   if($user.LineUri)
        {
                Set-CsUser -Identity $user.SipAddress -OnPremLineURI $user.LineUri -EnterpriseVoiceEnabled $True
        }
   }
    ```
   > [!Note]
   >  If you still have Skype for Business endpoints (either Skype clients or 3rd party phones), you will also want to set -HostedVoiceMail to $true. If your organization is only using Teams endpoints for voice enabled users, this setting is not applicable to your users. 

9. Confirm users with Phone System functionality have been provisioned correctly. The following Skype for Business Online PowerShell command returns an empty result as soon process is completed.

   ```PowerShell
   $sfbusers=import-csv "c:\data\SfbUsers.csv"
   foreach($user in $sfbusers)
   {
   if($user.LineUri)
        {
                $u=Get-CsOnlineUser -Identity $user.SipAddress
                if ($u.LineURI -ne $user.LineUri -or $u.EnterpriseVoiceEnabled -ne $true)
                {
                Get-CsOnlineUser -Identity $user.SipAddress | fl SipAddress, InterpretedUserType, OnPremLineURI, LineURI, EnterpriseVoiceEnabled, HostedVoicemail
                }
        }
   }
   ``` 
10. Repeat steps 3 through 9 until all users are processed.

11. Confirm that all users have been processed successfully by running the following two PowerShell commands.

    On-premises Skype for Business Server on-premises PowerShell command:

    ```PowerShell
    Get-CsUser | Select-Object SipAddress, UserPrincipalName
    ``` 
    Skype for Business Online PowerShell command:

    ```PowerShell
    Get-CsOnlineUser -Filter {Enabled -eq $True -and (OnPremHostingProvider -ne $null -or MCOValidationError -ne $null -or ProvisioningStamp -ne $null -or SubProvisioningStamp -ne $null)} | fl SipAddress, InterpretedUserType, OnPremHostingProvider, MCOValidationError, *ProvisioningStamp
    ``` 


## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)
