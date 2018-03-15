---
title: "Enable or disable hot desking in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 93a7fed6-f61a-4b41-9336-a8320afa87cf
description: "You can set up common area phones as hot-desk phones. With hot-desk phones, users can log on to their own user account, and, after they are logged on, use Lync Server features and their own user profile settings. Hot desking is managed by using client policies: to enable or disable hot desking, you need to modify the client policies that are used by your common area phones. For details about how to determine the conferencing policies that have been assigned to your common area phones, see View common area phone information in Lync Server 2013."
---

# Enable or disable hot desking in Lync Server 2013
[]
You can set up common area phones as hot-desk phones. With hot-desk phones, users can log on to their own user account, and, after they are logged on, use Lync Server features and their own user profile settings. Hot desking is managed by using client policies: to enable or disable hot desking, you need to modify the client policies that are used by your common area phones. For details about how to determine the conferencing policies that have been assigned to your common area phones, see [View common area phone information in Lync Server 2013](view-common-area-phone-information.md). 
  
You use the EnableHotdesking parameter of the **New-CSClientPolicy** cmdlet or the **Set-CSClientPolicy** cmdlet to enable or disable hot desking on a phone, as follows. Run these cmdlets from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
## 

### Enabling hot desking

- To enable hot desking for a common area phone, you must modify the client policy that has been assigned to that phone (or collection of phones). 
    
    After you have identified the policy that needs to be modified, the next step is to use the **Set-CsClientPolicy** cmdlet to set the EnableHotdesking parameter to True. For example: 
    
  ```
  Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $True
  ```

- Alternatively, you can use the **New-CsClientPolicy** cmdlet to create a new client policy that enables hot desking. For example: 
    
  ```
  New-CsClientPolicy -Identity "NewCommonAreaPhonePolicy" - EnableHotdesking $True
  ```

> [!IMPORTANT]
> After this policy has been created, you must assign it to the appropriate common area phones. For details, see [Assign policies in Lync Server 2013 to a common area phone](assign-policies-to-a-common-area-phone.md). 
  
### Disabling hot desking

- To disable hot desking for a common area phone, reset the EnableHotdesking parameter of the **Set-CsClientPolicy** cmdlet to the default value of False. For example: 
    
  ```
  Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $False
  ```

For details, see the Help topics for the [New-CsClientPolicy](new-csclientpolicy.md) cmdlet and the [Set-CsClientPolicy](set-csclientpolicy.md) cmdlet. 
  

