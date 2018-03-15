---
title: "View trusted application information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/31/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b916323-96fb-4308-bc95-c178de41a3d3
description: "You can view information about your trusted applications by using Windows PowerShell and the Get-CsTrustedApplication cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog articleQuick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShellat https://go.microsoft.com/fwlink/p/?linkId=255876."
---

# View trusted application information in Lync Server 2013
[]
You can view information about your trusted applications by using Windows PowerShell and the **Get-CsTrustedApplication** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view trusted applications

- To view all of your trusted applications, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsTrustedApplication
  ```

    This command returns information similar to the following for each trusted application:
    
  ```
  Identity               : CN={5dedf4b0-a590-49b3-80cf-f16f914bbef9},CN=Application Contacts,CN=RTC
                           Service,CN=Services,CN=Configuration,DC=litware,DC=com
  RegistrarPool          : 487279971
  HomeServer             : CN=Lc Services,CN=Microsoft,CN=co1:2,CN=Pools,CN=RTC
                           Service,CN=Services,CN=Configuration,DC=litware,DC=com
  OwnerUrn               : urn:application:helpdesk
  SipAddress             : sip:RtcApplication-dbf5142f-2bb2-4c4f-9531-b7fea45c5000@litware.com
  DisplayName            :
  DisplayNumber          :
  LineURI                :
  PrimaryLanguage        : 0
  SecondaryLanguages     : {}
  EnterpriseVoiceEnabled : True
  ExUmEnabled            : False
  Enabled                : True
  
  ```

    For details, see [Get-CsTrustedApplication](get-cstrustedapplication.md).
    

