---
title: "Delete an existing collection of Lync Phone Edition configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bfc427d-4dcd-4199-b25f-8d5cfec2164f
description: "If you no longer want to use a collection of settings for devices running Lync Phone Edition, delete it. If you delete a collection for a site, the global settings will apply to the phones in that site. You cannot delete the global collection."
---

# Delete an existing collection of Lync Phone Edition configuration settings in Lync Server 2013
[]
If you no longer want to use a collection of settings for devices running Lync Phone Edition, delete it. If you delete a collection for a site, the global settings will apply to the phones in that site. You cannot delete the global collection.
  
> [!NOTE]
> Instead of deleting a collection, you might just want to change some of the settings. For details about how to do so, see [Create or modify a collection of Lync Phone Edition configuration settings in Lync Server 2013](create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md). 
  
### To delete a collection of Lync Phone Edition configuration settings

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Device Configuration** navigation button. 
    
4. On the **Device Configuration** page, click the collection you want to delete, click the **Edit** menu, and then click **Delete**.
    
    > [!NOTE]
    > If you delete the global collection, the settings just revert to the default settings. The collection does not go away. 
  
5. In the confirmation box, click **OK**.
    
## Removing Lync Phone Edition Configuration Settings by Using Windows PowerShell Cmdlets

You can delete Lync Phone Edition configuration settings by using Windows PowerShell and the **Remove-CsUCConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specified collection of Lync Phone Edition configuration settings

- This command deletes the UC phone configuration settings applied to the Redmond site:
    
  ```
  Remove-CsUCPhoneConfiguration -Identity "site:Redmond"
  ```

### To remove all of the Lync Phone Edition configuration settings applied to the site scope

- This command removes all the UC phone configuration settings applied to the service scope:
    
  ```
  Get-CsUCPhoneConfiguration -Filter "site:*" | Remove-CsUCPhoneConfiguration
  ```

### To remove all of the Lync Phone Edition configuration settings where phone locking is disabled

- This command deletes any collection of UC phone configuration settings where phone locking has been disabled:
    
  ```
  Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration
  ```

For details, see [Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md).
  

