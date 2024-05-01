---
ms.date: 03/17/2018
title: "Skype for Business Server: Delete an existing collection of SIP trunk configuration settings"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 3b25f14d-884b-42dd-a866-460d276d3e43
description: "Summary: Learn how to delete a collection of trunk configuration settings by using the Skype for Business Server Control Panel."
---

# Skype for Business Server: Delete an existing collection of SIP trunk configuration settings 
 
**Summary:** Learn how to delete a collection of trunk configuration settings by using the Skype for Business Server Control Panel.
  
SIP trunk configuration settings define the relationship and capabilities between a Mediation Server and the Public Switched Telephone Network (PSTN) gateway, an IP-Public Branch eXchange (PBX), or a Session Border Controller (SBC) at the service provider. These settings do such things as specify:
  
- Whether media bypass should be enabled on the trunks
    
- The conditions under which Realtime Transport Control Protocol (RTCP) packets are sent
    
- Whether or not Secure Realtime Transport Protocol (SRTP) encryption is required on each trunk
    
When you install Skype for Business Server, a global collection of SIP trunk configuration settings is created for you. This global collection of settings can't be deleted. However, you can use the Skype for Business Server Control Panel or the [Remove-CsTrunkConfiguration](/powershell/module/skype/remove-cstrunkconfiguration) cmdlet to "reset" the properties in the global collection to their default values. For example, if you set the `Enable3pccRefer` property to True, when you reset the global collection the `Enable3pccRefer` property reverts to its default value of False.
  
Administrators can also create custom trunk configuration settings at the site scope or at the service scope (for an individual PSTN gateway); these custom settings can be removed. When you remove these custom settings keep the following things in mind:
  
- If you remove service scope settings, then the SIP trunk managed by those settings is managed by the settings applied to their site, if they exist. If site settings don't exist, those trunks are managed by the global collection of trunk configuration settings.
    
- If you remove site-scoped settings, any SIP trunks managed by those settings are managed by the global collection of trunk configuration settings.
    
### To remove trunk configuration settings with Skype for Business Server Control Panel

1. In Skype for Business Server Control Panel, select **Voice Routing**, and then select **Trunk Configuration**.
    
2. On the **Trunk Configuration** tab, select the collection of SIP trunk configuration settings to be deleted, select **Edit**, and then select **Delete**. To delete multiple collections in the same operation, select the first collection to be deleted, then hold down the Ctrl key and select any other collections that you want to remove.
    
3. The **State** property for the collection is updated to **Uncommitted**. To commit the changes, and to delete the collection, select **Commit** and then select **Commit All**.
    
4. In the **Uncommitted Voice Configuration Settings** dialog box, select **OK**.
    
5. In the **Skype for Business Server Control Panel** dialog box, select **OK**.
    
6. If you change your mind and decide not to delete the collection, select **Commit** and then select **Cancel All Uncommitted Changes**. When the **Skype for Business Server Control Panel** dialog box appears, select **OK**.
    
## Removing Trunk Configuration Settings by Using Skype for Business Server Management Shell Cmdlets

You can delete trunk configuration settings by using Skype for Business Server Management Shell and the **Remove-CsTrunkConfiguration** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Skype for Business Server Management Shell.
  
### To remove a specified collection of settings

- The following command removes the trunk configuration settings applied to the Redmond site:
    
  ```powershell
  Remove-CsTrunkConfiguration -Identity site:Redmond
  ```

### To remove all the collections applied to the site scope

- This command removes all the trunk configuration settings applied to the service scope:
    
  ```powershell
  Get-CsTrunkConfiguration -Filter "service:*" | Remove-CsTrunkConfiguration
  ```

### To remove all the collections where media bypass is enabled

- The following command removes all the trunk configuration settings where media bypass is enabled:
    
  ```powershell
  Get-CsTrunkConfiguration | Where-Object {$_.EnableBypass -eq $True} | Remove-CsTrunkConfiguration
  ```

For more information, see the help article for the [Remove-CsTrunkConfiguration](/powershell/module/skype/remove-cstrunkconfiguration) cmdlet.

