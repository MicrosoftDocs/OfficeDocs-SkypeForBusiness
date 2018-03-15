---
title: "Create or modify a collection of Lync Phone Edition configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6cf714af-8f57-4a71-89ad-0a776302b2ba
description: "When you install Lync Server, you get a global collection of Lync Phone Edition settings. These settings apply to all devices running Lync Phone Edition in your deployment. You can change these settings at any time. You can also set up a new collection of settings that apply to the devices in a specific site. Site settings take precedence over global settings."
---

# Create or modify a collection of Lync Phone Edition configuration settings in Lync Server 2013
[]
When you install Lync Server, you get a global collection of Lync Phone Edition settings. These settings apply to all devices running Lync Phone Edition in your deployment. You can change these settings at any time. You can also set up a new collection of settings that apply to the devices in a specific site. Site settings take precedence over global settings. 
  
Configuration settings consist of the collection name, scope (global or site), SIP security setting, logging level, voice quality of service (QoS) level, phone-lock setting, and phone-lock details, that is, how long the a) unlock personal identification number (PIN) must be and b) phone stays idle before locking itself.
  
### To create a collection of Lync Phone Edition configuration settings or edit settings for an existing collection

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Device Configuration** navigation button. 
    
4. On the **Device Configuration** page, do one of the following: 
    
  - To create a new collection of Lync Phone Edition configuration settings, click **New**, select a site, click **OK**, review the default settings, and, if you want to, make any changes.
    
  - To edit any of the settings in an existing collection, click the collection, click the **Edit** menu, click **Show details**, and then make your changes.
    
    > [!TIP]
    > To go back to using the default settings for the global collection, click the global collection, click the **Edit** menu, click **Delete**, and then click **OK**. This will not delete the global collection; it just resets the settings to the defaults. 
  
5. Click **Commit**.
    
## Creating New Lync Phone Edition Configuration Settings by Using Windows PowerShell Cmdlets

You can create Lync Phone Edition configuration settings can (at the site scope only) by using Windows PowerShell and the **New-CsUCPhoneConfiguration** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To create new Lync Phone Edition configuration settings that use the default values

- This command creates a new set of UC phone configuration settings for the Redmond site:
    
  ```
  New-CsUCPhoneConfiguration -Identity "site:Redmond"
  ```

    Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties.
    
### To change a single property value when creating new Lync Phone Edition configuration settings

- To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of UC phone configuration settings that, by default, require phone locking, use a command like this:
    
  ```
  New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True
  ```

### To change multiple property values when creating new Lync Phone Edition configuration settings

- Multiple property values can be modified by including multiple parameters. For example, this command enforces phone locking and also sets the minimum PIN length to 8 digits:
    
  ```
  New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True -MinPhonePinLength 8
  ```

For details, see [New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md).
  
## See also

#### 

[Delete an existing collection of Lync Phone Edition configuration settings in Lync Server 2013](delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)
  
[Configure security settings for Lync Phone Edition in Lync Server 2013](configure-security-settings-for-lync-phone-edition.md)
  
[Enforce phone locking in Lync Server 2013](enforce-phone-locking.md)

