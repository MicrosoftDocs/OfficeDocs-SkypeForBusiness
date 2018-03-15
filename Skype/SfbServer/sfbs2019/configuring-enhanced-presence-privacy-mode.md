---
title: "Configuring enhanced presence privacy mode in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7a6b873-486d-4dfb-a967-c48f61f237f3
description: "With enhanced presence privacy mode, users can restrict their presence information so that it is visible only to the contacts listed in their Lync 2013 Contacts list. The New-CsPrivacyConfiguration and Set-CsPrivacyConfiguration cmdlets have an EnablePrivacyMode parameter controls this option. When EnablePrivacyMode is set to True, the option to restrict presence information to contacts becomes available in the Lync 2013 Status options. When EnablePrivacyMode is set to False, users can choose either to always allow everyone to see their presence information or to adhere to any future changes the administrator makes to the privacy mode."
---

# Configuring enhanced presence privacy mode in Lync Server 2013
[]
With enhanced presence privacy mode, users can restrict their presence information so that it is visible only to the contacts listed in their Lync 2013 Contacts list. The **New-CsPrivacyConfiguration** and **Set-CsPrivacyConfiguration** cmdlets have an EnablePrivacyMode parameter controls this option. When EnablePrivacyMode is set to True, the option to restrict presence information to contacts becomes available in the Lync 2013 Status options. When EnablePrivacyMode is set to False, users can choose either to always allow everyone to see their presence information or to adhere to any future changes the administrator makes to the privacy mode. 
  
> [!IMPORTANT]
>  Lync 2013 and Lync 2010 privacy settings are not honored by previous versions (Microsoft Office Communicator 2007 R2 or Microsoft Office Communicator 2007). If previous versions of Office Communicator are allowed to sign in, a Lync 2013 user's status, contact information, or picture could be viewed by someone who has not been authorized to view it. Additionally, a Lync 2013 user's privacy settings are reset if he or she later signs in with previous version of Communicator. >  For these reasons, in a migration scenario, before you enable enhanced presence privacy mode: >  Ensure that every user has Lync 2013 installed. >  Define a client version policy rule to prevent previous versions of Communicator from signing in. 
  
### To enable enhanced presence privacy mode

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following command:
    
  ```
  Get-CsPrivacyConfiguration | Set-CsPrivacyConfiguration -EnablePrivacyMode $True
  ```

    This command enables privacy mode for all the privacy configuration settings currently in use in the organization. For more information about how the Lync Server enhanced presence privacy mode policy configurations manages contact presence for the Lync 2013 client, see the Microsoft KB article [Enabling Lync Server enhanced presence privacy mode updates the presence status of some Lync contacts to "unavailable"](https://support.microsoft.com/kb/3020057).
    
## See also

#### 

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)
  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

