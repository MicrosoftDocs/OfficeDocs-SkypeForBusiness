---
title: "Delete a dial-in conferencing access number in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 199c5d9c-0489-4ad5-a7f1-ca59fe0e6ac7
description: "Follow these steps to delete a dial-in conferencing access number."
---

# Delete a dial-in conferencing access number in Lync Server 2013
[]
Follow these steps to delete a dial-in conferencing access number.
  
### To delete a dial-in conferencing access number

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing**, and then click **Dial-in Access Number**.
    
4. On the page, click the dial-in number you want to delete in the list, click **Edit**, and then click **Delete**.
    
5. Click **OK**.
    
## Removing Dial-in Conferencing Access Numbers by Using Windows PowerShell Cmdlets

Dial-in conferencing access numbers can be deleted by using Windows PowerShell and the **Remove-CsDialInConferencingAccessNumber** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To remove a specific dial-in conferencing access number

- This command deletes the dial-in conferencing access number with Identity sip:RedmondDialInAccess@litwareinc.com:
    
  ```
  Remove-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialInAccess@litwareinc.com"
  ```

### To remove all the dial-in conferencing access numbers assigned to a specific region

- This command deletes all the dial-in conferencing access numbers associated with the Northwest region:
    
  ```
  Get-CsDialInConferencingAccessNumber -Region "Northwest" | Remove-CsDialInConferencingAccessNumber
  ```

### To remove dial-in conferencing access numbers based on primary language

- This command deletes all the dial-in conferencing access numbers where Italian is the primary language:
    
  ```
  Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "it-IT"} | Remove-CsDialInConferencingAccessNumber
  ```

For more information, see the help topic for the [Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md) cmdlet. 
  

