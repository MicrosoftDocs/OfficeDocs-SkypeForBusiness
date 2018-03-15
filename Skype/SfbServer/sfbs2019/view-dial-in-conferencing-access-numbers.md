---
title: "View dial-in conferencing access numbers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 41a7dfb4-0c89-4650-b61b-0e1bf875c62b
description: "In Lync Server 2013 Control Panel, you provide dial-in access numbers to users so that they can join a meeting externally."
---

# View dial-in conferencing access numbers in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you provide dial-in access numbers to users so that they can join a meeting externally.
  
### To view dial-in access numbers

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Dial-in Access Number**.
    
4. On the **Dial-in Access Number** page, click the access number that you would like to view. 
    
5. In **Edit**, select the **Show Details…** check box. 
    
## Viewing Dial-in Conferencing Access Numbers by Using Windows PowerShell Cmdlets

Dial-in conferencing access numbers can be viewed by using Windows PowerShell and the Get-CsDialInConferencingAccessNumber cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view dial-in conferencing access numbers

- To view information about all your dial-in conferencing access numbers, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsDialInConferencingAccessNumber
  ```

    That will return information similar to this:
    
  ```
  Identity           : CN={20ca8dc8-5ff8-41f4-b5bb-22ba9972ae2e},
                       CN=Application Contacts,CN=RTCService=Services,
                       CN=Configuration,DC=litwareinc,DC=com
  PrimaryUri         : sip:testnumber@litwareinc.com
  DisplayName        : Test
  DisplayNumber      : 1-425-555-1019
  LineUri            : tel:+14255551019
  PrimaryLanguage    : en-US
  SecondaryLanguages : {}
  Pool               : atl-cs-001.litwareinc.com
  HostingProvider    :
  Regions            : {US}
  
  ```

For more information, see the help topic for the [Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md) cmdlet. 
  

