---
title: "Modify the default dial-in conferencing PIN settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2d110e94-ad29-4755-b17f-d8c2da9b78a4
description: "The global PIN policy defines the rules for dial-in conferencing PINs at the forest level. Follow these steps to modify the global dial-in conferencing PIN policy. For details about creating or modifying a dial-in conferencing PIN policy at the site or user level, see Create or modify dial-in conferencing PIN settings in Lync Server 2013 for a site or group of users."
---

# Modify the default dial-in conferencing PIN settings in Lync Server 2013
[]
The global PIN policy defines the rules for dial-in conferencing PINs at the forest level. Follow these steps to modify the global dial-in conferencing PIN policy. For details about creating or modifying a dial-in conferencing PIN policy at the site or user level, see [Create or modify dial-in conferencing PIN settings in Lync Server 2013 for a site or group of users](create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md).
  
### To modify the global PIN policy

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click the **Global** policy, click **Edit**, and then click **Show details**.
    
5. In **Edit PIN Policy**, in **Minimum PIN length**, type or select the minimum PIN length that you want to allow. The default minimum length is five digits.
    
6. To be able to specify the maximum number of logon attempts before a user is locked out, select the **Specify maximum logon attempts** check box. If you do not select this option, the maximum number of allowed attempts is automatically determined based on the PIN length. By default, the maximum number of attempts is automatically determined. 
    
7. If you selected the **Specify maximum logon attempts** check box, in **Maximum logon attempts**, type or select the maximum number of logon attempts that you want to allow.
    
8. To have PINs expire, select the **Enable PIN expiration** check box. If you do not select this option, PINs will never expire. By default, PINs never expire. 
    
9. If you selected the **Enable PIN expiration** check box, in **PIN expires after (days)**, type or select the number of days after which PINs expire.
    
10. In **PIN history count**, type the number of PINs that a user must create before the user can reuse a PIN. By default, users can reuse their PINs.
    
11. To allow common patterns of digits in PINs, such as sequential numbers and repetitive sets of numbers, select the **Allow common patterns** check box. If you do not select this option, only complex patterns of digits are allowed. By default, only complex patterns of digits are allowed. 
    
    > [!IMPORTANT]
    > We recommend that you do not allow common patterns. 
  
12. Click **Commit**.
    

