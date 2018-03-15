---
title: "Updating from the evaluation version of Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 62a88180-4289-4a2a-9cb9-1b9899344a63
description: "If you have installed the Evaluation version of Microsoft Lync Server 2013, you will eventually need to update that installation a licensed copy of the software; that's because the evaluation version expires 180 days after it was installed. However, you will not need to completely uninstall the evaluation version and then install the licensed version. Instead, after you have obtained a valid licensing key, you can update the evaluation version of Lync Server 2013 by carrying out the following procedure on each computer acting as a Lync Server Front End Server, Director, or Edge Server. Note that you do not have to update computers carrying out other server roles, such as a Monitoring Server or Archiving Server."
---

# Updating from the evaluation version of Lync Server 2013
[]
If you have installed the Evaluation version of Microsoft Lync Server 2013, you will eventually need to update that installation a licensed copy of the software; that's because the evaluation version expires 180 days after it was installed. However, you will not need to completely uninstall the evaluation version and then install the licensed version. Instead, after you have obtained a valid licensing key, you can update the evaluation version of Lync Server 2013 by carrying out the following procedure on each computer acting as a Lync Server Front End Server, Director, or Edge Server. Note that you do not have to update computers carrying out other server roles, such as a Monitoring Server or Archiving Server. 
  
## Updating from the Evaluation Version of Microsoft Lync Server 2013

To update a computer from the evaluation version of Lync Server 2013 to the licensed version of the software: 
  
### Updating from the Evaluation Version of Microsoft Lync Server 2013

1. Log on to the computer as a local administrator.
    
2. Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. In the Lync Server Management Shell, type the following command and then press ENTER:
    
  ```
  msiexec.exe /fvomus server.msi EVALTOFULL=1 /qb
  ```

    Note that you might need to specify the full path to the file server.msi. This file can be found in the Setup folder of the Lync Server Volume media installation files. 
    
4. After Setup finishes running, type the following from the command prompt and then press ENTER:
    
  ```
  Enable-CsComputer
  ```

5. Repeat this procedure on any other Front End Server, Director, or Edge Server running an evaluation copy of Lync Server. This procedure should also be performed on any Branch Office Servers that were deployed by using the Lync Server media installation files.
    
If you are not sure if the evaluation version of Lync Server is running on a given computer you can verify that by running the following command from within the Lync Server Management Shell:
  
```
Get-CsServerVersion
```

The [Get-CsServerVersion](get-csserverversion.md) cmdlet will analyze the local computer and report back one of the following: 
  
- That the Lync Server volume license key has been installed on the computer, meaning that no updating is necessary.
    
- That the Lync Server evaluation license key has been installed, meaning that the computer must be updated.
    
- That no volume license key is required on the computer. Updating from the evaluation version to the licensed version is only required on Front End Servers, Directors, and Edge Servers.
    

