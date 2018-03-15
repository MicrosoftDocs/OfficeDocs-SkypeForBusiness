---
title: "Modify a trunk in Topology Builder in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 81055a82-c6f8-47b2-9779-223b1d842f36
description: "Follow these steps to modify the alternate media IP address and alternate bypass identifier of a trunk."
---

# Modify a trunk in Topology Builder in Lync Server 2013
[]
Follow these steps to modify the alternate media IP address and alternate bypass identifier of a trunk.
  
### To Modify the Alternate Media IP Address of a Trunk

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the Set-CsPstnGateway cmdlet and modify the AlternateBypassId field in the Lync Server Management Shell.
    
  ```
  Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -RepresentativeMediaIP <IP address>
  ```

### To Modify the Alternate BypassID of a Trunk

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the Set-CsPstnGateway cmdlet and modify the AlternateBypassId field in the Lync Server Management Shell.
    
  ```
  Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -AlternateBypassID <identifier>
  ```


