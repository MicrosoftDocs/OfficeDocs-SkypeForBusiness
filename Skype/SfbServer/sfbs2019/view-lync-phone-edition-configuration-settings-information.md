---
title: "View Lync Phone Edition configuration settings information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15f94478-651f-4063-9918-6a059f98df16
description: "You can view configuration information about devices running Lync Phone Edition. The information is organized into collections. When you install Lync Server, you get a collection of Lync Phone Edition settings that apply to all the devices running Lync Phone Edition in your deployment. You can also create new collections of settings for a specific site. Site settings take precedence over global settings. Each collection of settings consists of a name, the scope (global or site), SIP security setting, logging level, voice quality of service (QoS) level, phone-lock setting, and phone-lock details, that is, the minimum length of the unlock personal identification number (PIN) and time before the phone locks itself."
---

# View Lync Phone Edition configuration settings information in Lync Server 2013
[]
You can view configuration information about devices running Lync Phone Edition. The information is organized into collections. When you install Lync Server, you get a collection of Lync Phone Edition settings that apply to all the devices running Lync Phone Edition in your deployment. You can also create new collections of settings for a specific site. Site settings take precedence over global settings. Each collection of settings consists of a name, the scope (global or site), SIP security setting, logging level, voice quality of service (QoS) level, phone-lock setting, and phone-lock details, that is, the minimum length of the unlock personal identification number (PIN) and time before the phone locks itself.
  
### To view configuration information about devices running Lync Phone Edition

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Device Configuration** navigation button. 
    
4. On the **Device Configuration** page, click the collection of settings you want to view information about. The name, scope, SIP security setting, voice quality level, and phone lock setting are listed on the main page. To view the logging level and phone lock details, click the **Edit** menu, and then click **Show details**.
    
## Viewing Lync Phone Edition Configuration Information by Using Windows PowerShell Cmdlets

You can view Lync Phone Edition configuration settings by using Lync Server Management Shell and the **Get-CsUCPhoneConfiguration** cmdlet. You can run this cmdlet can from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view Lync Phone Edition configuration information

- To view information about all your Lync Phone Edition configuration settings, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsUCPhoneConfiguration
  ```

    The command returns information similar to the following:
    
  ```
  Identity             : Global
  CalendarPollInterval : 00:03:00
  EnforcePhoneLock     : True
  PhoneLockTimeout     : 00:10:00
  MinPhonePinLength    : 6
  SIPSecurityMode      : High
  VoiceDiffServTag     : 40
  Voice8021p           : 0
  LoggingLevel         : Off
  ```

For details, see [Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md).
  
## See also

#### 

[Create or modify a collection of Lync Phone Edition configuration settings in Lync Server 2013](create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md)
  
[Delete an existing collection of Lync Phone Edition configuration settings in Lync Server 2013](delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)
  
[Configure security settings for Lync Phone Edition in Lync Server 2013](configure-security-settings-for-lync-phone-edition.md)
  
[Enforce phone locking in Lync Server 2013](enforce-phone-locking.md)

