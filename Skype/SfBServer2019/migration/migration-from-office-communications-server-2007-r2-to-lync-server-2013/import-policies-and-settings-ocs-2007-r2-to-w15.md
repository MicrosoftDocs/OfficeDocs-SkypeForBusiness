---
title: "Import policies and settings [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b25decee-2ee5-4836-b370-454411d39252
description: "After you merge your Office Communications Server 2007 R2 topology information with your Lync Server 2013 pilot pool, you need to run a Lync Server 2013 Management Shell cmdlet to migrate your Office Communications Server 2007 R2 policies and configuration settings to your Lync Server 2013 pilot pool."
---

# Import policies and settings [OCS 2007 R2 to W15]
[]
After you merge your Office Communications Server 2007 R2 topology information with your Lync Server 2013 pilot pool, you need to run a Lync Server 2013 Management Shell cmdlet to migrate your Office Communications Server 2007 R2 policies and configuration settings to your Lync Server 2013 pilot pool.
  
The **Import-CsLegacyConfiguration** cmdlet imports policies, voice routes, dial plans, Communicator Web Access URLs, and dial-in access numbers to Lync Server 2013. 
  
## To migrate policies and settings

1. On the Lync Server 2013 Front End server, start the Lync Server Management Shell.
    
2. At the command line, type the following:
    
  ```
  Import-CsLegacyConfiguration
  ```

    After the policies are imported, use the procedure that follows to see the imported policies in the Lync Server Control Panel .
    
## To view imported policies

1. Open Lync Server 2013 Control Panel. 
    
2. Click **Voice Routing** and view the imported policies. 
    
3. Click **Conferencing** and view the imported policies. 
    
4. Click **Federation and External Access** and view the imported policies. 
    
5. Click **Monitoring and Archiving** and view the imported policies. 
    

